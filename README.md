# 🌐 Google Search Workflow (n8n)

This n8n workflow automates Google search queries using [Apify](https://apify.com/), extracts emails from result pages, and stores them in a Google Sheet.

---

## 🧩 Features

- Triggers on **new rows** added to a Google Sheet
- Sends keywords to Apify's Google Search actor
- Retrieves and processes search results
- Scrapes target pages for **email addresses**
- Writes deduplicated results into a separate Google Sheet tab

---

## ⚙️ Setup Instructions

### 1. 🗂 Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git

