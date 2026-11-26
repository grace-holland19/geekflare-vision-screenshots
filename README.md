# Geekflare Vision Screenshots How to Capture Dynamic Page Renderings with Free Tier Access — Unlock Real-Time Visual Data for Crawlers and Monitoring Tools in Production Environments (Step-by-Step Guide)

Welcome to the deep-dive you've been waiting for. If you've ever built a crawler, a content-monitoring service, or a visual-QA pipeline, you know that a reliable screenshot endpoint that can also highlight every actionable element on a page is a rare commodity. Geekflare's Screenshot API delivers exactly that: a real-browser capture with JavaScript rendering, ad-blocking, cookie-banner suppression, and a **`highlightLinks: true`** flag that draws bounding boxes around every link, button, and input element.  

In this guide we'll walk through the economics of each call, compare Geekflare's credit model to the per-thousand-call pricing of four well-known rivals, map realistic workloads to the right subscription tier, and give you ready-to-paste code for both raw cURL and the hosted Managed Cloud Platform (MCP). All of this is framed through a FinOps-minded lens, so you'll see exactly how many credits a given job costs, when you'll need a proxy add-on, and how to keep your monthly bill honest. Geekflare appears **50 – 70** times throughout because it is the central reference point for every decision you'll make.

---

## Real Per-1,000-Request Economics Explained Plainly

Understanding cost starts with credits. Every request to the Screenshot API consumes a fixed number of credits; there is no hidden per-byte charge, no tiered surcharge for larger images, and failed 5xx responses are free.  

| Capture Type | Credits per Call | Standard Cost (Free tier) | Starter Cost (per 1K) | Growth Cost (per 1K) | Business Cost (per 1K) |
|--------------|------------------|---------------------------|-----------------------|----------------------|------------------------|
| Standard screenshot (JS, ads blocked, cookie banner hidden, captcha bypass) | **5** | ~100 captures (500 credits) | **$9.50** | **$3.45** | **$1.75** |
| Proxy-enhanced capture (`proxyCountry` +4 credits) | **9** | N/A (proxy not on Free) | **$17.10** | **$6.21** | **$3.14** |

*How the numbers translate*: With the Starter plan you receive 10,000 credits each month. At 5 credits per standard capture that's **2,000** screenshots for **$9.50 per 1K**. The Growth plan gives you 100,000 credits, which equals **20,000** standard captures at **$3.45 per 1K**. The Business tier pushes that to **200,000** captures at **$1.75 per 1K**.  

If you need geo-targeted screenshots, add the proxy add-on (+4 credits). On the Starter tier a proxy capture costs **$17.10 per 1K**, on Growth **$6.21 per 1K**, and on Business **$3.14 per 1K**.  

Because credits do **not** roll over, you'll want to size your plan to stay comfortably under the 90% usage alert. For example, a workload of 8,000 standard captures (40,000 credits) fits neatly inside the Growth tier's 100,000-credit allotment with room for spikes, while the same workload would exceed the Starter limit (10,000 credits) by a large margin.

---

## Geekflare Plans Side by Side: Credits, Rate Limits, and Log Retention

| Tier | Price / Mo | Credits / Mo | Credit Cost | Req/s | Team Seats | Log Retention | Proxy Add-On  | Link |
|------|------------|--------------|-------------|------|------------|---------------|-------------- | --- |
| **Free** | $0 | 500 | $0.00 | 1 | 1 | 7 days | **No**  | [Start Free](https://geekflare.com/pricing/) |
| **Starter** | $19 | 10,000 | $0.0019/credit | 5 | 3 | 30 days | +4 credits (paid only)  | [Get Starter](https://geekflare.com/pricing/) |
| **Growth** | $69 mo or $58 mo (billed yearly) | 100,000 | $0.00069/credit (monthly) | 10 | 5 | 30 days | +4 credits  | [Get Growth](https://geekflare.com/pricing/) |
| **Business** | $349 | 1,000,000 | $0.000349/credit | 25 | 25 | 90 days | +4 credits  | [Get Business](https://geekflare.com/pricing/) |
| **Enterprise** | Custom | Custom | Custom | Up to 1,000 | Custom | Custom | Custom  | [Contact Sales](https://geekflare.com/pricing/) |

*Key billing rules*  

* **No credit rollover** – unused credits vanish on the first day of the next cycle.  
* **Failed renders are free** – any 5xx error or capture that cannot be generated consumes 0 credits.  
* **Usage alerts** – you receive an email at 90% consumption; the API pauses at 100% until you add a pack or upgrade.  
* **Refund guarantee** – cancel within 7 days and receive a full refund if you have used less than 10% of your allocated credits.  

### One-Time Credit Packs (Stackable, No Subscription Required)

| Pack | Price | Credits | Approx. $/1K Credits |
|------|-------|---------|----------------------|
| **Spark** | $10 | 5,000 | $2.00 |
| **Blaze** | $50 | 50,000 | $1.00 |
| **Inferno** | $100 | 100,000 | $1.00 |
| **Supernova** | $200 | 200,000 | $1.00 |

Packs are valid for one year and can be added to any tier, including Free. For a small startup that only needs occasional bursts, buying a Blaze pack (50,000 credits) on top of a Free tier can cover **10,000** standard screenshots without ever paying a subscription fee.

---

## Using Geekflare Across Code, AI Agents, and No-Code Flows

Geekflare's ecosystem is built for developers who prefer to stay in the language of their choice, as well as for citizen integrators who rely on visual automation tools.

* **Python SDK** – `pip install geekflare-api` gives you a thin wrapper around the REST endpoints, handling the `x-api-key` header automatically.  
* **Node/TypeScript SDK** – `npm install @geekflare/api-node` offers async methods and built-in retry logic.  
* **MCP (Managed Cloud Platform)** – The hosted portal at `https://mcp.geekflare.com/mcp` exposes 18 tools, including `screenshot`, `search`, `webScrape`, and `url2Pdf`. You can invoke any tool via a single JSON payload, making it perfect for serverless functions or CI pipelines.  
* **AI Frameworks** – LangChain (`pip install langchain-geekflare`), LlamaIndex (`pip install llama-index-tools-geekflare`), and Vercel AI SDK (`@geekflare/ai-sdk`) let you embed screenshot calls directly into retrieval-augmented generation (RAG) pipelines.  
* **No-Code** – Official n8n node, Zapier integration, and Make connector let you trigger screenshots from a visual workflow without writing a line of code. The public online Screenshot tool (`https://geekflare.com/tools/webpage-screenshot/`) is also available for ad-hoc testing.  

All of these integrations share the same credit pool, so you can mix and match without worrying about hidden costs.

---

## An Independent Side-by-Side Look at Leading Providers

| Provider | Credit Pool Shared with Other APIs? | Pricing Model | Proxy Support | Highlight-Links Feature | Free Tier |
|----------|--------------------------------------|---------------|--------------|------------------------|-----------|
| **Geekflare** | Yes (14 APIs) | Credit-based (Free – Enterprise) | Paid add-on (+4 credits) | ✅ (`highlightLinks: true`) | 500 credits |
| Urlbox | No | Tiered monthly render counts | No built-in proxy | ❌ (no link-highlighting) | See Urlbox pricing |
| Microlink | No | Daily / monthly request tiers | No built-in proxy | ❌ (focus on OG metadata) | See Microlink pricing |
| ScreenshotAPI.net | No | Monthly screenshot tiers | Limited geo-proxy | ❌ (no link-highlighting) | See ScreenshotAPI.net pricing |
| ScreenshotOne | No | Per-1K rate (Growth $79/10K) | Geo-proxy available | ❌ (no timestamp watermark) | 100 free captures, See ScreenshotOne pricing |

**Takeaway:** Geekflare uniquely bundles screenshot, search, and web-scraping under a single credit pool, offers a dedicated `highlightLinks` flag, and provides a transparent per-credit cost that scales down dramatically as you move up the tier ladder. Competing services either charge per-render without a shared pool, lack the link-highlighting capability, or have higher per-1K rates.  

---

## Which Plan Fits Your Monthly Volume Best?

| Monthly Requests (Standard) | Credits Needed | Recommended Tier | Price / Mo |
|-----------------------------|----------------|------------------|------------|
| ≤ 100 captures (≤ 500 credits) | 500 | **Free** | $0 |
| 1,000 captures (5,000 credits) | 5,000 | **Starter** (well under 10,000) | $19 |
| 5,000 captures (25,000 credits) | 25,000 | **Growth** (100,000) | $69 (or $58 billed yearly) |
| 20,000 captures (100,000 credits) | 100,000 | **Growth** (full allocation) | $69 |
| 150,000 captures (750,000 credits) | 750,000 | **Business** (1 M) | $349 |
| > 1 M captures | Custom | **Enterprise** | Custom |

If you need occasional spikes beyond your tier, buy a **Blaze** pack (50,000 credits) or **Inferno** pack (100,000 credits). For example, a project that normally runs 8,000 standard captures per month (40,000 credits) could stay on Growth and add a Blaze pack to cover a sudden 5,000-capture surge without upgrading.

---

## Inside Geekflare Screenshot API: How It Handles Real Workloads

When you POST to `https://api.geekflare.com/screenshot`, the request body is a JSON object. The API spins up a headless Chromium instance, applies the requested viewport, device emulation, and any visual tweaks, then renders the page fully—including any lazy-loaded content triggered by JavaScript.  

Key parameters for the **highlight-links** use case:

| Parameter | Type | Default | Effect |
|-----------|------|---------|--------|
| `url` | string | – | Target page (must be a publicly reachable URL). |
| `highlightLinks` | boolean | `true` | Draws a semi-transparent bounding box around every `<a>`, `<button>`, and `<input>` element. |
| `fullPage` | boolean | `false` | Capture the entire scrollable height. |
| `selector` | string | – | Capture only the element matching the CSS selector; `fallbackToFullPage` can be set to true. |
| `device` | enum (`desktop`, `mobile`) | `desktop` | Chooses a mobile user-agent and viewport. |
| `viewportWidth` / `viewportHeight` | int (320-3840 / 240-2160) | – | Custom dimensions for precise layout testing. |
| `scaleFactor` | int (1-5) | 1 | HiDPI/Retina scaling; multiplies pixel density. |
| `theme` | enum (`light`, `dark`, `auto`) | `auto` | Forces a color scheme. |
| `delay` | int (0-10 seconds) | 0 | Wait before capture, useful for animations. |
| `disableAnimations` | boolean | `false` | Turns off CSS animations for a static frame. |
| `removeBackground` | boolean | `false` | Returns a transparent PNG. |
| `addTimestamp` | boolean | `true` | Watermarks the capture with a UTC timestamp (useful for audit trails). |
| `inline` | boolean | `false` | Returns a Base64-encoded data URI instead of a CDN URL (good for immediate embedding). |
| `proxyCountry` | string (ISO-2) | – | Routes the request through a rotating proxy in the specified country; adds +4 credits on paid plans. |

The API respects the tier's **req/s** limit (1 / 5 / 10 / 25 req/s). Exceeding the limit yields a 429 response, which does **not** consume credits. Successful captures return a JSON payload with either a `url` (hosted for 30 days) or an `inline` field containing the Base64 image data.

---

## Quickstart Implementation You Can Drop Into Your Repo

### 1️⃣ cURL via MCP (JSON payload)

```bash
curl -X POST https://mcp.geekflare.com/mcp \
  -H "Content-Type: application/json" \
  -d '{
    "tool": "screenshot",
    "apiKey": "YOUR_X_API_KEY",
    "payload": {
        "url": "https://en.wikipedia.org/wiki/Web_scraping",
        "highlightLinks": true,
        "fullPage": true,
        "device": "desktop",
        "addTimestamp": true,
        "inline": false,
        "proxyCountry": "US"
    }
}'
```

*What happens*: MCP routes the request to the Screenshot endpoint, applies a US proxy (+4 credits), and returns a JSON with a `url` field pointing at the 30-day hosted image.

### 2️⃣ Direct cURL call (no MCP)

```bash
curl -X POST https://api.geekflare.com/screenshot \
  -H "Content-Type: application/json" \
  -H "x-api-key: YOUR_X_API_KEY" \
  -d '{
        "url": "https://en.wikipedia.org/wiki/Web_scraping",
        "highlightLinks": true,
        "fullPage": true,
        "device": "desktop",
        "addTimestamp": true,
        "inline": true
      }'
```

The response contains an `inline` field with a Base64 data URI you can embed directly into HTML or store in a database. Because we omitted `proxyCountry`, this call costs **5 credits**. Adding `"proxyCountry":"DE"` would bump the cost to **9 credits**.

Both snippets are ready to paste into a CI step, a GitHub Action, or a local script.

---

## Monthly Subscriptions, Yearly Savings, and Prepaid Credit Packs

Geekflare's pricing is deliberately simple:

* **Monthly vs. yearly** – The Growth tier drops from $69 /mo to $58 /mo when you choose annual billing. That's two months free each year, expressed as "$58/mo billed yearly". No need to calculate a lump-sum amount; just pick the billing cadence that matches your cash-flow.  
* **Refund policy** – If you cancel within the first 7 days and have used less than 10% of your allocated credits, you get a full refund. This makes the free tier a safe sandbox for proof-of-concept work.  
* **Credit packs** – Spark, Blaze, Inferno, and Supernova packs are one-off purchases that sit on top of any tier. For example, a startup on the Free plan can buy a Spark pack for $10 and instantly gain 5,000 extra credits, enough for **1,000** standard screenshots (5 credits each).  

Because credits reset each month, you can treat a pack as a "burst buffer" for seasonal traffic spikes. The packs never expire within a year, so you can purchase them ahead of a known campaign and let them sit idle until needed.

---

## Where Geekflare Wins — And Where You Should Honestly Look Elsewhere

**Wins**  

* **Unified credit pool** – All 14 Geekflare APIs (search, scraping, screenshot, PDF, etc.) draw from the same balance, simplifying budgeting.  
* **Highlight-links flag** – No other vendor in the comparison table offers a built-in way to annotate every interactive element, which is a huge time-saver for vision-model pipelines.  
* **Transparent per-credit pricing** – Costs shrink from $9.50 / 1K on Starter to $1.75 / 1K on Business, with no hidden surcharges.  
* **Robust reliability** – 99.9% uptime across Google Cloud Platform and Cloudflare, backed by a bootstrapped company that has served over 21,000 businesses since 2015.  
* **Strong community feedback** – 4.9 overall rating (G2 4.8, Google 4.9, Product Hunt 5.0).  

**Limitations**  

* No direct S3/GCS bucket upload hook – you must fetch the CDN URL or Base64 data and store it yourself.  
* No GPU-accelerated rendering tier – high-throughput visual QA may need to parallelize across multiple instances.  
* No built-in recurring cron endpoint – scheduling must be handled by external orchestrators (n8n, Zapier, CI).  

If your workflow requires native cloud storage integration or GPU rendering, a competitor like ScreenshotOne may be a better fit despite a higher per-1K rate. For most developers who value a single credit pool, link-highlighting, and predictable pricing, Geekflare remains the most cost-effective choice.

---

## Frequently Asked Questions

**What happens if I exceed my plan's request-per-second limit?**  
The API returns a 429 status code. Because the request is throttled, no credits are deducted. You can either back off and retry or upgrade to a higher tier with a larger `req/s` allowance.

**Can I combine multiple credit packs with a paid plan?**  
Yes. Packs stack on top of any subscription tier, including Enterprise. They remain valid for one year from purchase and are deducted before the plan's monthly credit allocation.

**Is the `highlightLinks` output a separate image or an overlay?**  
The bounding boxes are drawn directly onto the rendered screenshot. The resulting image (PNG, JPEG, or WebP) contains the visual highlights, and the same image is returned via the CDN URL or inline Base64.

**Do failed captures still count against my credit balance?**  
No. Any 5xx server error or a capture that cannot be generated consumes 0 credits, which helps protect you from accidental over-billing during outages.

**How do I enable the geo-proxy for a specific country?**  
Add the `proxyCountry` field with an ISO-2 country code (e.g., `"proxyCountry":"DE"`). This adds +4 credits per call on any paid tier that includes the proxy add-on.

---
