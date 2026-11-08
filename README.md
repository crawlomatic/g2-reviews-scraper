# G2 Reviews Scraper & API | Extract Software Reviews & Ratings

[![Apify Store](https://img.shields.io/badge/Apify%20Store-View%20Actor-brightgreen?logo=apify)](https://apify.com/misterkhan/g2-reviews-scraper)
[![GitHub stars](https://img.shields.io/github/stars/crawlomatic/g2-reviews-scraper?style=social)](https://github.com/crawlomatic/g2-reviews-scraper)
[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Python SDK](https://img.shields.io/badge/SDK-Python-3776AB?logo=python&logoColor=white)](https://github.com/apify/apify-client-python)
[![Node.js SDK](https://img.shields.io/badge/SDK-Node.js-339933?logo=node.js&logoColor=white)](https://github.com/apify/apify-client-js)

> Fast, reliable G2 reviews scraper to extract verified user ratings, pros & cons, company sizes, and reviewer profiles without getting blocked.

---

## ⚡ Quick Start

You can run this scraper directly via the **[Apify Store Web Console](https://apify.com/misterkhan/g2-reviews-scraper)** with zero setup, or integrate it into your Python / Node.js backend using the code below.

### 🐍 Python Quickstart

```bash
pip install apify-client
```

```python
from apify_client import ApifyClient

# Initialize the ApifyClient with your API token
# Get your token from https://console.apify.com/account/integrations
client = ApifyClient("YOUR_APIFY_TOKEN")

# Configure input parameters
run_input = {
  "startUrls": [
    {
      "url": "https://www.g2.com/products/slack/reviews"
    }
  ],
  "maxItems": 25
}

print("🚀 Launching G2 Reviews Scraper & API | Extract Software Reviews & Ratings on Crawlomatic Engine...")
run = client.actor("misterkhan/g2-reviews-scraper").call(run_input=run_input)

# Fetch results from the Actor's default dataset
dataset_items = client.dataset(run["defaultDatasetId"]).list_items().items
print(f"✅ Successfully fetched {len(dataset_items)} records!")

for item in dataset_items[:3]:
    print(item)
```

---

### 🟢 Node.js / JavaScript Quickstart

```bash
npm install apify-client
```

```javascript
import { ApifyClient } from 'apify-client';

// Initialize the ApifyClient with your API token
const client = new ApifyClient({
    token: 'YOUR_APIFY_TOKEN',
});

// Configure input parameters
const input = {
  "startUrls": [
    {
      "url": "https://www.g2.com/products/slack/reviews"
    }
  ],
  "maxItems": 25
};

console.log('🚀 Launching G2 Reviews Scraper & API | Extract Software Reviews & Ratings...');
const run = await client.actor('misterkhan/g2-reviews-scraper').call(input);

// Fetch results
const { items } = await client.dataset(run.defaultDatasetId).listItems();
console.log(`✅ Extracted ${items.length} records!`);
console.dir(items.slice(0, 3));
```

---

## What does G2 Software Reviews Scraper do?

G2 Software Reviews Scraper is a B2B Voice-of-Customer (VoC) and competitive intelligence tool that extracts verified software reviews directly from **G2.com**—capturing 1–5 star ratings, structured answers to **"What do you like best?"** (`likes_best`), **"What do you dislike?"** (`dislikes`), and **"What problems is it solving?"** (`problems_solved`), alongside reviewer job titles and company size segments.

Whether you are building sales battlecards against competing SaaS products, mining churn triggers from 1-to-3 star competitor reviews, or training AI agents on authentic B2B buyer language, this scraper delivers clean, structured records in seconds.

> 🛡️ **Zero Proxy Configuration Required:** Anti-blocking and regional routing are **handled automatically out of the box** — just paste your target URLs and click **Start**.

## What data can you extract with G2 Software Reviews Scraper?

**⭐ Star Rating & Review Headline** — numeric `rating` (1.0–5.0), review `title`, unique review `id`, and publication date <br>
**👍 What Users Like Best (`likes_best`)** — full verified customer answer describing favorite features and strengths <br>
**👎 What Users Dislike (`dislikes`)** — separated product complaints, missing features, and UX friction points <br>
**🎯 Business Problems Solved (`problems_solved`)** — real-world ROI, workflows, and business outcomes described by the buyer <br>
**👤 B2B Reviewer Persona** — `author` (`reviewer_name`), `reviewer_title` (e.g., VP of Engineering), and `company_size` (Small-Business, Mid-Market, Enterprise) <br>
**🔗 Direct Review Permalink** — canonical `url` pointing to the verified G2 review <br>

## Why scrape B2B software reviews from G2.com?

**💪 Build data-backed sales battlecards** — isolate exact feature gaps (`dislikes`) reported by Mid-Market and Enterprise buyers of your competitors <br>
**🕵️ Uncover high-intent churn and switching signals** — identify why users outgrow rival SaaS tools and tailor your outbound messaging to those exact pain points <br>
**✨ Write higher-converting SaaS landing page copy** — extract the exact words buyers use in `problems_solved` and `likes_best` to mirror your ideal customer profile's vocabulary <br>
**👍 Zero proxy or account configuration** — built-in anti-blocking and proxy routing work automatically out of the box <br>
**📩 Automate product and competitive intelligence** — sync new G2 reviews directly into Slack, Notion, HubSpot, Airtable, or AI summarization pipelines <br>

## How do I use G2 Software Reviews Scraper?

G2 Software Reviews Scraper is designed for fast, zero-configuration operation in Apify Console:

1. Click **Try for free** on the Actor page to open Apify Console.
2. Paste one or more G2 product review URLs into **Start URLs** (for example, `https://www.g2.com/products/slack/reviews`).
3. Set **Max Results** (`maxItems`) to choose how many software reviews to collect.
4. Click **Start** to launch the extraction run.
5. Download your B2B software review dataset from the **Dataset** tab in Excel, CSV, JSON, or HTML table format.

## Input

G2 Software Reviews Scraper accepts a simple 2-parameter JSON configuration. Click on the [Input tab](https://apify.com/misterkhan/g2-reviews-scraper/input-schema) for the interactive form.

```json
{
  "startUrls": [
    {
      "url": "https://www.g2.com/products/slack/reviews"
    }
  ],
  "maxItems": 25
}
```

**🔍 `product`** — software product name or G2 product slug (e.g. `slack` or `notion`). When provided, `startUrls` is optional <br>
**🔍 `product`** — software product name or G2 product slug (e.g. `slack` or `notion`). When provided, `startUrls` is optional <br>
**⭐ `startUrls`** — array of G2 product review page URLs (`https://www.g2.com/products/{product-slug}/reviews`) <br>
**🔢 `maxItems`** — maximum number of software reviews to collect per run (default: 25; Free plan runs collect up to 25 reviews per run, while paid Apify plans support unlimited review extraction) <br>

## Output sample

Results are streamed in real time to your default Apify Dataset. Each record contains the structured Q&A review responses (`likes_best`, `dislikes`, `problems_solved`), star rating, and B2B buyer persona:

```json
[
  {
    "id": "g2_rev_9928174",
    "title": "Essential communication hub for our remote engineering team",
    "rating": 5.0,
    "date": "2026-09-28",
    "likes_best": "Huddles and workflow integrations save us hours of status meetings every week.",
    "dislikes": "Search history can get cluttered when channels grow past a few hundred members.",
    "problems_solved": "Centralized real-time collaboration across 4 time zones and automated deployment alerts.",
    "author": "David K.",
    "reviewer_title": "VP of Engineering",
    "company_size": "Mid-Market (51-1000 emp.)",
    "url": "https://www.g2.com/products/slack/reviews/slack-review-9928174"
  }
]
```

## How much does it cost to scrape G2 software reviews?

G2 Software Reviews Scraper uses **Pay-Per-Event (PPE)** pricing (apify-default-dataset-item) with a `$0.00` startup fee—you only pay for verified software reviews delivered to your dataset:

**🆓 Free plan** — `$0.005` per review ($5.00 / 1,000 reviews, up to 25 reviews/run) <br>
**🥉 Starter (Bronze) plan** — `$0.0016` per review ($1.60 / 1,000 reviews) <br>
**🥈 Scale (Silver) plan** — `$0.0012` per review ($1.20 / 1,000 reviews) <br>
**🥇 Business+ (Gold) plan** — `$0.0009` per review ($0.90 / 1,000 reviews) <br>

With the monthly free credit on the Apify Free plan, you can extract **up to 1,000 G2 software reviews per month for free**.

> 💡 **Predictable, All-Inclusive Pay-Per-Event Pricing:** There is a **`$0.00` run start fee** and **no separate proxy configuration required**. You only pay the flat per-result rate above for data successfully delivered to your dataset — works out of the box on both **Free** and **Paid** Apify plans.

## How many results can you scrape with G2 Software Reviews Scraper?

G2 Software Reviews Scraper can extract **hundreds to thousands of verified B2B software reviews per product** on paid Apify plans (up to 25 reviews per run on the Free plan). Keep these tips in mind when planning your runs:

- **Use /products/{slug}/reviews URLs** — pass direct G2 product review URLs (e.g., `https://www.g2.com/products/slack/reviews`) in `startUrls` to extract the product's verified review stream.
- **Anonymous B2B reviewers** — when a G2 reviewer chooses to hide their name ("Verified User in Computer Software"), `author` (`reviewer_name`) reflects their public display label while still preserving `reviewer_title`, `company_size`, and all three Q&A fields.
- **Multi-competitor category audits** — pass 5 to 10 competing software product URLs in `startUrls` to build a complete category sentiment matrix in a single execution.

## Want to scrape Trustpilot reviews, SaaS tech stacks, or company contacts?

Combine G2 Software Reviews Scraper with our companion B2B intelligence and review Actors:

⭐ **[Trustpilot Reviews Scraper](https://apify.com/misterkhan/trustpilot-reviews-scraper)** — extract verified Trustpilot customer reviews, star ratings, experience dates, and company replies <br>
🛠️ **[Website Tech Stack, Contacts & AI Markdown Scanner](https://apify.com/misterkhan/website-tech-stack-scanner)** — detect 7,000+ SaaS technologies, analytics tools, and verified contacts across any company domain list <br>
📧 **[Website Contact & Email Scraper](https://apify.com/misterkhan/contact-enricher-scraper)** — extract business emails, phone numbers, and LinkedIn company links from any website <br>
💼 **[Indeed Jobs Scraper](https://apify.com/misterkhan/indeed-scraper)** — track SaaS company hiring velocity, open engineering roles, and salary ranges <br>

## Integrations and G2 Software Reviews Scraper

G2 Software Reviews Scraper connects seamlessly with your product management, CRM, and AI analysis stack via [Apify integrations](https://apify.com/integrations):

- **No-Code & AI Workflows** — pipe new G2 reviews into Make, Zapier, n8n, or Clay to summarize competitor pain points with OpenAI or Claude.
- **Spreadsheets & BI** — sync structured `likes_best`, `dislikes`, and `problems_solved` columns straight into Google Sheets, Airtable, Notion, BigQuery, or Snowflake.
- **Webhooks** — trigger Slack battlecard updates or CRM alerts the moment a run finishes.

## Using G2 Software Reviews Scraper with the Apify API

You can launch review runs and fetch dataset items programmatically using the official `apify-client` SDKs for **Node.js** and **Python**, or connect this Actor directly to AI product-research agents via the **Apify MCP Server** (`https://mcp.apify.com`).

Check the [API tab](https://apify.com/misterkhan/g2-reviews-scraper/api) for ready-to-copy Node.js, Python, and cURL code snippets.

## Frequently asked questions about G2 Software Reviews Scraper

**🎯 Does the scraper separate "Likes Best", "Dislikes", and "Problems Solved"? <br>**
Yes. Every G2 review is parsed into three distinct fields (`likes_best`, `dislikes`, and `problems_solved`) so you can filter or embed customer pain points without manual text splitting.

**👤 Does the output include the reviewer's job title and company size? <br>**
Yes. Whenever displayed on the public G2 review card, `reviewer_title` (such as VP of Engineering or Director of Marketing) and `company_size` (Small-Business, Mid-Market, Enterprise) are extracted automatically.

**🛡️ Do I need to configure proxies or a G2 account? <br>**
**No — everything works out of the box with zero setup.** Regional routing, session management, and anti-blocking are handled automatically so you do not need to configure custom proxy settings.

## Is it legal to scrape public software reviews from G2?

Our scrapers are ethical and only extract publicly available software review scores, Q&A commentary, and public reviewer role labels displayed on G2.com. They do not access private user accounts or non-public data. For more details on the legality of web scraping, read Apify's guide on [is web scraping legal](https://blog.apify.com/is-web-scraping-legal/).

## Your feedback

We keep this Actor under active maintenance. If a run finishes successfully but returns fewer results than you expected, hangs, or errors — please **open an Issue before posting a public review** so we can diagnose and fix it for you.

**🛠️ How to report** — Use the Actor’s [Issues tab](https://apify.com/misterkhan/g2-reviews-scraper/issues/open) in Apify Console. Include the run ID, your input JSON, and what you expected vs. what you got. <br>
**⏱️ Response time** — We aim to reply within 24 hours on business days. <br>
**⭐ Reviews** — Happy with the results? A short positive review helps other users find a reliable scraper. Ran into a problem? Open an Issue first — we’ll work with you to resolve it before you leave a rating. <br>


---

## 🛡️ Architecture & Engine Reliability

This scraper runs on the **[Crawlomatic Engine](https://crawlomatic.com)**:
- **Zero Proxy Configuration:** Intelligent residential and datacenter proxy rotation with automated regional ccTLD binding.
- **WAF Bypass Engine:** Autonomous challenge solving for Cloudflare Turnstile, DataDome, PerimeterX, Kasada, and Akamai.
- **Pay-Per-Event (PPE) Pricing:** Transparent pay-as-you-go pricing with \$0 starting fee.

## 📄 License

Apache License 2.0. See [LICENSE](LICENSE) for details.

Developed & Maintained by **[Crawlomatic](https://crawlomatic.com)**.
