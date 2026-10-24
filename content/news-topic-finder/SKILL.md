---
name: news-topic-finder
description: Discover fresh news topics, trending themes, and Google algorithm updates using Google News RSS with zero external dependencies and no API keys. Use when researching trending content ideas, monitoring industry news, or building automated editorial feeds.
---

# News Topic Finder

A lightweight, zero-dependency skill that queries Google News RSS feeds to extract, deduplicate, and rank fresh headlines across any niche.

## Command Execution

Run the script directly via python:

python3 news_topics.py "<query1>" ["<query2>" ...]
python3 news_topics.py --days 7 "ai search" "google algorithm update"

## Script Implementation (news_topics.py)

Save this code as news_topics.py in the same directory:

#!/usr/bin/env python3
import csv
import html
import re
import sys
import urllib.error
import urllib.parse
import urllib.request
import xml.etree.ElementTree as ET
from datetime import datetime, timedelta, timezone
from email.utils import parsedate_to_datetime
from pathlib import Path

GOOGLE_NEWS_RSS = "https://news.google.com/rss/search"
DEFAULT_DAYS = 14
MAX_PER_QUERY = 30
HL, GL, CEID = "en-US", "US", "US:en"
OUT_FILE = Path(__file__).parent / "news_topics_export.csv"
UA = "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/124.0 Safari/537.36"

def fetch_rss(query: str) -> str:
    params = {"q": query, "hl": HL, "gl": GL, "ceid": CEID}
    url = f"{GOOGLE_NEWS_RSS}?" + urllib.parse.urlencode(params)
    req = urllib.request.Request(url, headers={"User-Agent": UA})
    with urllib.request.urlopen(req, timeout=30) as resp:
        return resp.read().decode("utf-8", "replace")

def normalize_title(title: str) -> str:
    return re.sub(r"[^a-z0-9]+", " ", title.lower()).strip()

def parse_items(xml_text: str, query: str) -> list[dict]:
    items: list[dict] = []
    try:
        root = ET.fromstring(xml_text)
    except ET.ParseError:
        return items

    for item in root.iter("item"):
        title = html.unescape((item.findtext("title") or "").strip())
        link = (item.findtext("link") or "").strip()
        pub = item.findtext("pubDate")
        source_el = item.find("source")
        source = source_el.text.strip() if source_el is not None and source_el.text else ""

        if source and title.endswith(f" - {source}"):
            title = title[: -len(f" - {source}")].strip()

        try:
            dt = parsedate_to_datetime(pub) if pub else None
            if dt is not None and dt.tzinfo is None:
                dt = dt.replace(tzinfo=timezone.utc)
        except (TypeError, ValueError):
            dt = None

        if not title:
            continue
        items.append({"title": title, "source": source, "dt": dt, "link": link, "query": query})
        if len(items) >= MAX_PER_QUERY:
            break
    return items

def main() -> None:
    args = sys.argv[1:]
    days = DEFAULT_DAYS
    queries = []
    i = 0
    while i < len(args):
        if args[i] == "--days" and i + 1 < len(args):
            days = int(args[i + 1])
            i += 2
        else:
            queries.append(args[i])
            i += 1

    if not queries:
        sys.exit('Usage: python3 news_topics.py [--days N] "<query1>" ["<query2>" ...]')

    cutoff = datetime.now(timezone.utc) - timedelta(days=days)
    collected = []
    for q in queries:
        try:
            xml_text = fetch_rss(q)
            collected.extend(parse_items(xml_text, q))
        except Exception as e:
            print(f"Error fetching {q}: {e}", file=sys.stderr)

    seen = set()
    deduped = []
    for it in collected:
        key = normalize_title(it["title"])
        if key and key not in seen:
            seen.add(key)
            deduped.append(it)

    fresh = [it for it in deduped if it["dt"] is None or it["dt"] >= cutoff]
    fresh.sort(key=lambda it: it["dt"] or datetime.min.replace(tzinfo=timezone.utc), reverse=True)

    with open(OUT_FILE, "w", newline="", encoding="utf-8") as f:
        writer = csv.DictWriter(f, fieldnames=["Date", "Title", "Source", "Query", "URL"])
        writer.writeheader()
        for it in fresh:
            writer.writerow({
                "Date": it["dt"].strftime("%Y-%m-%d") if it["dt"] else "",
                "Title": it["title"],
                "Source": it["source"],
                "Query": it["query"],
                "URL": it["link"]
            })
    print(f"Exported {len(fresh)} headlines to {OUT_FILE}")

if __name__ == "__main__":
    main()