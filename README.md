# Google Search Email Finder Workflow

## Overview
This n8n workflow automates the process of finding email addresses from websites that appear in Google search results for specific keywords. When new keywords are added to a Google Sheet, the workflow performs a Google search, visits each result's website, extracts any email addresses found, and saves them back to your spreadsheet.

## How It Works

### Workflow Steps
1. **Trigger**: Monitors a Google Sheet for new keywords added
2. **Search**: Uses Apify to perform Google searches for each keyword
3. **Extract**: Visits each search result and extracts email addresses
4. **Store**: Saves found emails along with website details to a results sheet

### Node Descriptions

#### 1. Google Sheets Trigger
- Monitors the "Get words" sheet for new rows
- Triggers the workflow when a new keyword is added

#### 2. Run Actor
- Sends the keyword to Apify's Google Search actor
- Configures search parameters (results per page, max pages, etc.)

#### 3. Get Actor Run
- Waits for the Apify search to complete
- Retrieves the search results

#### 4. Get Dataset
- Fetches the complete dataset from Apify containing search results

#### 5. Split Out
- Separates each search result for individual processing

#### 6. Get the Website Data
- Visits each search result URL
- Downloads the website's HTML content

#### 7. Extract the Emails Found
- Uses regex to find email addresses in the website content
- Stores found emails in an array

#### 8. Split Out Emails
- Separates each found email for individual processing

#### 9. If Contains Email
- Filters out results where no emails were found

#### 10. Remove Duplicates
- Eliminates duplicate email addresses

#### 11. Google Sheets
- Writes results to the "Results" sheet
- Saves the email, page title, description, URL, and search keyword

## Setup Requirements

### Prerequisites
- n8n account/installation
- Google account with access to Google Sheets
- Apify account with API access token

### Credentials Needed
- Google Sheets OAuth2 credentials
- Apify API token (for HTTP Header Authentication)

### Google Sheets Structure
1. **Input Sheet** (Get words):
   - Column "Keyword": Keywords to search
   - Column "count": Number of results to retrieve (optional)

2. **Results Sheet**:
   - Column "Key": The search keyword
   - Column "title": Website title
   - Column "url": Website URL
   - Column "email": Extracted email address
   - Column "description": Website description

## Installation
1. Import the workflow JSON into your n8n instance
2. Set up the required credentials
3. Configure Google Sheet access
4. Activate the workflow

## Usage
Simply add new keywords to the "Get words" sheet, and the workflow will automatically:
1. Detect the new keyword
2. Perform the search
3. Extract emails
4. Save results to the "Results" sheet

## Limitations
- Relies on the Apify service for Google searches
- Email extraction uses regex which may miss some complex email patterns
- Website scraping may be blocked by some sites that use anti-scraping protection


