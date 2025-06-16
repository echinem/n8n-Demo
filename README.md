# 🔄 n8n Automation Workflows – Himangi Mishra

This repository contains a collection of real-world automation workflows built using [n8n](https://n8n.io/), showcasing API integration, data enrichment, automation orchestration, and clean modular design. These workflows have been tested in live environments, with all sensitive information removed from the exported `.json` files.

---

## 📂 Workflow Descriptions

### 🧠 1. WIOT Expo Exhibitor Intelligence – Full Pipeline
- **Goal**: Extract and enrich exhibitor data from the WIOT Expo website.
- **Steps**:
  - **Scrape the WIOT website** using HTTP Request nodes.
  - **Parse JSON response** and iterate over exhibitor data.
  - **Extract fields** like company name, description, and profile URL.
  - **Enrich data** via OpenAI API (using a system prompt to extract structured info like country, company size, RFID involvement).
  - **Output to Google Sheets** using upsert logic to avoid duplicates.
- **Highlights**:
  - Prompt engineering using `deterministic prompts`.
  - Modularized into clean sub-workflows for scraping, enrichment, and storage.
  - Uses Google Sheets as a lightweight CRM backend.

---

### ⚙️ 2. Scraper Flow – WIOT Website Crawler
- **Goal**: Isolate the scraping logic for reuse.
- **Steps**:
  - Send dynamic HTTP requests to the WIOT exhibitor list.
  - Loop through paginated data using a function node.
  - Return structured exhibitor fields for enrichment.
- **Highlights**:
  - Clean modular structure for reusability.
  - JSON manipulation with Function and Set nodes.

---

### 🧠 3. Enrichment Flow – OpenAI Field Extractor
- **Goal**: Enhance raw exhibitor data using LLMs.
- **Steps**:
  - Send a POST request to OpenAI with a preformatted prompt.
  - Parse the response to extract country, size, type, RFID role.
- **Highlights**:
  - Designed to be deterministic and low hallucination.
  - Easily extensible to other LLMs or prompt formats.

---

### 📊 4. Output Flow – Google Sheets Integration
- **Goal**: Insert enriched data into a Google Sheet as structured rows.
- **Steps**:
  - Check for existing entries using `Lookup Rows`.
  - Use `Append` or `Update` logic to prevent duplicates.
- **Highlights**:
  - API authentication with Google OAuth.
  - Acts as a simple but powerful backend database.

---

## 🛠️ How to Use

1. Clone or download this repository.
2. Import any workflow `.json` file into your n8n instance.
3. Configure your credentials (OpenAI, Google Sheets, etc.) via n8n's credential manager.
4. Run each workflow or connect them via a parent workflow to orchestrate the full pipeline.

---

## 🔐 Security Note

All API keys, access tokens, and sensitive information have been removed from these `.json` files. Please add your own credentials and endpoints where needed.

---

## 🙋‍♀️ About Me

I’m Himangi Mishra, a Computer Science Engineering student with hands-on experience in no-code automation, AI integrations, and real-time data processing.  
🔗 [GitHub](https://github.com/echinem)  
📧 [developer.himangi@gmail.com](mailto:developer.himangi@gmail.com)
