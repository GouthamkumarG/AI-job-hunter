<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1a1a2e,100:16213e&height=200&section=header&text=AI%20Job%20Hunter&fontSize=60&fontColor=ffffff&animation=fadeIn&fontAlignY=35&desc=Automated%20UK%20Job%20Matching%20Pipeline&descAlignY=55&descSize=18&descColor=a0aec0"/>

<br/>

[![N8N](https://img.shields.io/badge/N8N-Workflow%20Automation-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io)
[![Claude AI](https://img.shields.io/badge/Claude%20Sonnet-AI%20Scoring-D97706?style=for-the-badge&logo=anthropic&logoColor=white)](https://anthropic.com)
[![Apify](https://img.shields.io/badge/Apify-LinkedIn%20Scraper-00B4A6?style=for-the-badge&logo=apify&logoColor=white)](https://apify.com)
[![Google Sheets](https://img.shields.io/badge/Google%20Sheets-Job%20Tracker-34A853?style=for-the-badge&logo=google-sheets&logoColor=white)](https://sheets.google.com)
[![Gmail](https://img.shields.io/badge/Gmail-Daily%20Report-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](https://gmail.com)

<br/>

> Built in 2 hours. Runs every morning. Zero manual input.
>
> An end-to-end agentic AI pipeline that automatically scrapes, scores,
> and delivers ranked UK job matches with ATS analysis and resume tips daily.

<br/>

![Pipeline Demo](https://readme-typing-svg.demolab.com?font=Fira+Code&size=18&duration=2000&pause=500&color=16A34A&center=true&vCenter=true&multiline=true&repeat=true&width=600&height=100&lines=Scraping+fresh+UK+jobs+from+LinkedIn...;Scoring+every+job+against+resume+via+Claude+AI...;Delivering+ranked+report+to+inbox+daily...)

</div>

---

## What Is This?

Most job hunting is broken.

You spend hours scrolling LinkedIn, applying to roles you are underqualified for,
sending the same resume without knowing what keywords are missing, and never
knowing why you did not get a response.

This pipeline fixes all of that automatically.

Every morning it wakes up, scrapes fresh UK jobs, sends every single one through
Claude AI with my full resume embedded, and returns a brutally honest ranked
report with ATS scores, missing keywords, specific resume edits, and direct
apply links. All in under 3 minutes.

---

## How The Pipeline Works

```
+-----------------------------------------------------------------+
|                                                                 |
|   Schedule          Apify                JavaScript             |
|   Trigger    --->   LinkedIn    --->     Formatter              |
|   Fires 9AM         Scraper               Builds prompt         |
|                      UK Jobs                                    |
|                                                                 |
|                          |                                      |
|                          v                                      |
|                                                                 |
|   Google            Claude              JavaScript              |
|   Sheets    <---    Sonnet AI  <---     Parser                  |
|   Job tracker        Scores jobs         Filters 70%+           |
|                       vs resume                                 |
|                                                                 |
|                          |                                      |
|                          v                                      |
|                                                                 |
|                      Gmail                                      |
|                      HTML Report                                |
|                      Delivered                                  |
|                                                                 |
+-----------------------------------------------------------------+
```

---

## Step By Step Breakdown

### Step 1 - Schedule Trigger

N8N fires automatically every morning at 9AM UK time.
No manual input required. The pipeline runs whether you are awake or not.

### Step 2 - Apify LinkedIn Scraper

Apify runs 5 targeted LinkedIn searches simultaneously across different
role types — AI Engineer, LLM Engineer, Full Stack Developer, NLP Engineer,
and ML Engineer — all filtered to UK jobs posted in the last 24 hours.
Returns fresh jobs before applicant counts build up.

### Step 3 - JavaScript Formatter

A JavaScript node takes every scraped job and formats it into a single
structured prompt. Each job includes title, company, location, salary,
seniority level, full description up to 2000 characters, and apply URL.
All 100+ jobs bundled into one Claude API call for efficiency.

### Step 4 - Claude Sonnet AI Scoring

The core of the pipeline. Claude receives every job alongside the full
candidate resume and analyses each one across four dimensions:

- Skills Match (40%) — counts exactly how many required skills the candidate has
- Seniority Fit (25%) — checks if the role is genuinely junior or mid level
- Project Relevance (20%) — checks if projects directly prove ability to do the job
- Domain Alignment (15%) — AI, ML, Full Stack, or Automation fit

Claude also hard filters and immediately disqualifies any role requiring
3+ years experience, security clearance, PhD, or Senior/Lead/Principal titles.

### Step 5 - JavaScript Parser and Filter

Parses Claude's JSON response, removes duplicates using title and company
key matching, sanitises all text to prevent Google Sheets formula errors,
and filters to only jobs scoring 70% or above.

### Step 6 - Google Sheets Tracker

Every qualifying job is written as a clean row with all fields — date, rank,
priority, match score, ATS score, gaps, resume tips, cover letter
recommendation, and direct apply link. A new day separator row is added
automatically.

### Step 7 - Gmail HTML Report

A formatted HTML email is sent automatically with a summary card showing
Apply Now count, High Priority count, and Total Matches — followed by a
full ranked table with every job analysis and one-click apply buttons.

---

## Key Features

| Feature | What It Does |
|---|---|
| Match Percentage | Scores every job 0-100 against the exact resume |
| ATS Keyword Gaps | Lists every missing keyword from the job description |
| Resume Edits | Suggests specific bullet changes for each role |
| Interview Probability | Honest likelihood of getting an interview |
| Direct Apply Links | One click to apply — no searching required |
| Cover Letter Flag | Tells you which roles need a cover letter and why |
| Priority Ranking | Apply Now, High Priority, Good Backup |
| Deduplication | Filters out duplicate listings automatically |
| Data Sanitisation | Clean output with no broken characters or errors |
| Full Autonomy | Zero manual input from scraping to email delivery |

---

## Tech Stack

const pipeline = {
  orchestration : "N8N Cloud",
  scraping      : "Apify LinkedIn Jobs Scraper",
  ai            : "Claude Sonnet API (Anthropic)",
  formatting    : "JavaScript (Node.js)",
  storage       : "Google Sheets API",
  delivery      : "Gmail via N8N",
  hosting       : "N8N Cloud (scheduled)",
}

---

## Repository Structure

```
ai-job-hunter/
├── workflow/
│   └── AI_Job_Hunter.json      <- N8N workflow export (import directly)
├── assets/
│   └── pipeline.png            <- N8N pipeline screenshot
└── README.md
```

---

## How To Use This

1. Import AI_Job_Hunter.json into your N8N instance
2. Connect your Apify, Anthropic, Google Sheets, and Gmail credentials
3. Update the candidate profile in the JavaScript node with your resume
4. Set your Schedule Trigger time
5. Run it and wake up to ranked job matches every morning

---

## Built By

Goutham Gorthi — AI Engineer and Full Stack Developer

Open to AI Engineer, AI Automation, and Full Stack Developer roles
across the UK. Available immediately.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/gouthamchowdary)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/GouthamkumarG)

---

<div align="center">
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:16213e,100:1a1a2e&height=100&section=footer"/>
</div>
