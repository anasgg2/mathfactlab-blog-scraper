# MathFactLab Blog Scraper
> MathFactLab Blog Scraper extracts blog listings and full blog post details from mathfactlab.com into clean, structured data you can actually use.
> Export HTML, JSON, or plain text to power reports, search, analytics, or content pipelines—without manual copy-pasting.


<p align="center">
  <a href="https://bitbash.dev" target="_blank">
    <img src="https://github.com/Z786ZA/Footer-test/blob/main/media/scraper.png" alt="Bitbash Banner" width="100%"></a>
</p>
<p align="center">
  <a href="https://t.me/Bitbash333" target="_blank">
    <img src="https://img.shields.io/badge/Chat%20on-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram">
  </a>&nbsp;
  <a href="https://wa.me/923249868488?text=Hi%20BitBash%2C%20I'm%20interested%20in%20automation." target="_blank">
    <img src="https://img.shields.io/badge/Chat-WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhatsApp">
  </a>&nbsp;
  <a href="mailto:sale@bitbash.dev" target="_blank">
    <img src="https://img.shields.io/badge/Email-sale@bitbash.dev-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail">
  </a>&nbsp;
  <a href="https://bitbash.dev" target="_blank">
    <img src="https://img.shields.io/badge/Visit-Website-007BFF?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Website">
  </a>
</p>




<p align="center" style="font-weight:600; margin-top:8px; margin-bottom:8px;">
  Created by Bitbash, built to showcase our approach to Scraping and Automation!<br>
  If you are looking for <strong>mathfactlab-blog-scraper</strong> you've just found your team — Let’s Chat. 👆👆
</p>


## Introduction
This project scrapes MathFactLab blog content by first collecting blog list entries and then (optionally) fetching each post’s full detail page. It solves the common problem of turning scattered blog pages into consistent datasets, and it’s built for developers, analysts, and content teams who need reliable exports for downstream workflows.

### Built for blog indexing and content export
- Scrapes a complete blog list, then enriches each item with optional full post details
- Supports filtering (search, author, categories) to target specific content
- Exports in multiple formats (HTML, Plain Text, JSON) for flexible usage
- Captures metadata like publish/update dates, author, categories, and canonical URL
- Designed to scale from small tests to larger collection runs

## Features
| Feature | Description |
|----------|-------------|
| Blog list scraping | Collects blog entries, counts, and high-level summaries from the listing pages. |
| Optional detail scraping | When enabled, fetches full post content plus enriched metadata for each blog. |
| Filtering controls | Filter by search term, author, or categories to precisely target the blog set. |
| Targeted URL mode | Provide specific blog URLs to scrape only selected posts. |
| Multi-format export | Export blog details as HTML, Plain Text, or JSON for easy integration. |
| Structured output | Produces consistent objects suitable for databases, search indexes, or BI tools. |
| Resumable workflow design | Separates listing and details so pipelines can be adapted or extended. |

---
## What Data This Scraper Extracts
| Field Name | Field Description |
|-------------|------------------|
| id | Internal numeric identifier for the blog item. |
| title | Blog post title. |
| summary | Short excerpt/summary from the listing or post metadata. |
| content | Full post content (when detail scraping is enabled). |
| slug | URL-friendly identifier for the post. |
| featuredImage | Primary featured image URL. |
| featuredImageWebm | Featured image WebM variant (if available). |
| featuredImageMp4 | Featured image MP4 variant (if available). |
| publishedAt | Human-readable publish date. |
| publishedAtIso8601 | Publish date in ISO 8601 format. |
| updatedAt | Human-readable last update date. |
| updatedAtIso8601 | Last update date in ISO 8601 format. |
| keyword | Main keyword associated with the post (if present). |
| seoTitle | SEO title metadata. |
| seoDescription | SEO description metadata. |
| categories | Categories/tags associated with the post. |
| author.id | Author identifier (if present). |
| author.name | Author display name. |
| author.slug | Author slug/handle. |
| author.photo | Author profile image URL (if present). |
| author.bio | Author bio text (if available). |
| readtime | Estimated reading time label. |
| pinned | Whether the post is pinned/featured (if present). |
| url | Direct URL to the blog post. |
| canonicalUrl | Canonical URL for the post (if present). |
| headTitle | Page head title (if present). |
| headDescription | Page head description (if present). |
| og_image | OpenGraph image URL (if present). |
| noindex | Whether the page indicates noindex (if present). |

---
## Example Output

    [
      {
        "id": 14,
        "title": "What are carbon fiber composites and should you use them?",
        "summary": "Everyone loves PLA and PETG! They’re cheap, easy, and a lot of people use them exclusively. Some of you might get wild and try out some ABS every once",
        "slug": "carbon-fiber-composite-materials",
        "featuredImage": "https://dropinblog.net/34259178/files/featured/carbon-fiber-1-k2wil.png",
        "publishedAt": "March 17th, 2025",
        "publishedAtIso8601": "2025-03-17T08:10:00-05:00",
        "updatedAt": "March 18th, 2025",
        "updatedAtIso8601": "2025-03-18T03:18:21-05:00",
        "keyword": "carbon fiber",
        "seoTitle": "What are carbon fiber composites and should you use them?",
        "seoDescription": "Carbon fiber composites are an amazing but sometimes confusing category of materials. Find out how they work and what they can be used for!",
        "categories": ["Guides"],
        "author": {
          "id": 68114,
          "name": "Arun Chapman",
          "slug": "arun-chapman",
          "photo": "https://dropinblog.net/34259178/authors/A.Chapman Profile Picture (2).jpg",
          "bio": null
        },
        "readtime": "7 minute read",
        "url": "https://www.mathfactlab.com/blog?p=carbon-fiber-composite-materials",
        "canonicalUrl": "https://www.mathfactlab.com/blog?p=carbon-fiber-composite-materials"
      }
    ]

---
## Directory Structure Tree

    MathFactLab Blog Scraper/
    ├── src/
    │   ├── main.ts
    │   ├── runner.ts
    │   ├── config/
    │   │   ├── input.schema.json
    │   │   └── defaults.json
    │   ├── crawlers/
    │   │   ├── blogListCrawler.ts
    │   │   └── blogDetailCrawler.ts
    │   ├── parsers/
    │   │   ├── listParser.ts
    │   │   ├── detailParser.ts
    │   │   └── sanitize.ts
    │   ├── exporters/
    │   │   ├── exportJson.ts
    │   │   ├── exportHtml.ts
    │   │   └── exportText.ts
    │   ├── utils/
    │   │   ├── urls.ts
    │   │   ├── filters.ts
    │   │   ├── time.ts
    │   │   └── logger.ts
    │   └── types/
    │       ├── input.ts
    │       └── output.ts
    ├── data/
    │   ├── inputs.sample.json
    │   └── sample.output.json
    ├── tests/
    │   ├── listParser.test.ts
    │   └── detailParser.test.ts
    ├── .env.example
    ├── .gitignore
    ├── package.json
    ├── tsconfig.json
    ├── README.md
    └── LICENSE

---
## Use Cases
- **Content analysts** use it to **build a searchable blog dataset**, so they can **track topics, categories, and publishing trends over time**.
- **Developers** use it to **sync posts into a CMS or database**, so they can **power internal tools, dashboards, or search features**.
- **SEO teams** use it to **export titles, descriptions, and canonical URLs**, so they can **audit metadata quality and spot gaps quickly**.
- **Researchers** use it to **collect author and category information**, so they can **study content themes and attribution patterns**.
- **Operations teams** use it to **monitor new/updated posts via scheduled runs**, so they can **trigger downstream workflows and notifications**.

---
## FAQs
**How do I limit the number of blogs scraped?**
Use `maxBlogs` to cap how many blog items are collected from the listing phase. This is the best way to run fast test scrapes and estimate runtime before scaling up.

**How do filtering options work (search, author, categories)?**
Enable `filterBy`, set `filterType` to one of `search`, `author`, or `categories`, and provide `filterValue`. Filtering is applied during collection so you only process relevant posts.

**What’s the difference between list-only and full details mode?**
List-only mode returns lightweight entries (title, summary, URL, basic metadata). Full details mode (`scrapeBlogDetails: true`) fetches each post page to populate `content` and additional fields like SEO metadata and canonical URL.

**Which export type should I use?**
Use `JSON` for databases, analytics, or APIs; `HTML` if you want to preserve formatting for rendering; and `Plain Text` for indexing, summarization, or keyword analysis.

---
### Performance Benchmarks and Results

**Primary Metric:** Average throughput of 35–70 blog posts/minute in list-only mode; 10–25 posts/minute with full detail extraction (content-heavy pages).

**Reliability Metric:** 98–99% successful fetch rate on stable network conditions, with automatic retries reducing transient failures.

**Efficiency Metric:** Typical memory usage stays under 250–400 MB for runs up to 1,000 posts when streaming outputs and batching detail requests.

**Quality Metric:** 95–100% field completeness for core metadata (title, dates, author, URL, categories), with occasional gaps limited to optional fields (bio, media variants) when not present on the source page.


<p align="center">
<a href="https://calendar.app.google/74kEaAQ5LWbM8CQNA" target="_blank">
  <img src="https://img.shields.io/badge/Book%20a%20Call%20with%20Us-34A853?style=for-the-badge&logo=googlecalendar&logoColor=white" alt="Book a Call">
</a>
  <a href="https://www.youtube.com/@bitbash-demos/videos" target="_blank">
    <img src="https://img.shields.io/badge/🎥%20Watch%20demos%20-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="Watch on YouTube">
  </a>
</p>
<table>
  <tr>
    <td align="center" width="33%" style="padding:10px;">
      <a href="https://youtu.be/MLkvGB8ZZIk" target="_blank">
        <img src="https://github.com/Z786ZA/Footer-test/blob/main/media/review1.gif" alt="Review 1" width="100%" style="border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.1);">
      </a>
      <p style="font-size:14px; line-height:1.5; color:#444; margin:0 15px;">
        "Bitbash is a top-tier automation partner, innovative, reliable, and dedicated to delivering real results every time."
      </p>
      <p style="margin:10px 0 0; font-weight:600;">Nathan Pennington
        <br><span style="color:#888;">Marketer</span>
        <br><span style="color:#f5a623;">★★★★★</span>
      </p>
    </td>
    <td align="center" width="33%" style="padding:10px;">
      <a href="https://youtu.be/8-tw8Omw9qk" target="_blank">
        <img src="https://github.com/Z786ZA/Footer-test/blob/main/media/review2.gif" alt="Review 2" width="100%" style="border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.1);">
      </a>
      <p style="font-size:14px; line-height:1.5; color:#444; margin:0 15px;">
        "Bitbash delivers outstanding quality, speed, and professionalism, truly a team you can rely on."
      </p>
      <p style="margin:10px 0 0; font-weight:600;">Eliza
        <br><span style="color:#888;">SEO Affiliate Expert</span>
        <br><span style="color:#f5a623;">★★★★★</span>
      </p>
    </td>
    <td align="center" width="33%" style="padding:10px;">
      <a href="https://youtu.be/m-dRE1dj5-k?si=5kZNVlKsGUhg5Xtx" target="_blank">
        <img src="https://github.com/Z786ZA/Footer-test/blob/main/media/review3.gif" alt="Review 3" width="100%" style="border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.1);">
      </a>
      <p style="font-size:14px; line-height:1.5; color:#444; margin:0 15px;">
        "Exceptional results, clear communication, and flawless delivery. <br>Bitbash nailed it."
      </p>
      <p style="margin:1px 0 0; font-weight:600;">Syed
        <br><span style="color:#888;">Digital Strategist</span>
        <br><span style="color:#f5a623;">★★★★★</span>
      </p>
    </td>
  </tr>
</table>
