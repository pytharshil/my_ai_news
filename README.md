# AI News Aggregator

An AI-powered news aggregation system that collects recent AI-related content, summarizes it, ranks it according to user preferences, and delivers a personalized newsletter through email.

## Features

* Collects AI news from:

  * YouTube channels
  * OpenAI articles
  * Anthropic articles
* Retrieves YouTube transcripts
* Generates AI-powered summaries
* Personalizes news ranking based on user interests and expertise
* Creates a personalized email digest
* Sends the newsletter through Gmail SMTP
* Stores articles and summaries in PostgreSQL

## Workflow

```text
News Sources
    ↓
Data Collection
    ↓
PostgreSQL Database
    ↓
YouTube Transcript Processing
    ↓
AI Summary Generation
    ↓
Personalized Article Ranking
    ↓
Email Digest Generation
    ↓
Gmail SMTP Delivery
```

## Technologies Used

* **Python** – Main programming language
* **OpenAI API** – Summarization, ranking, and email generation
* **GPT-4o-mini** – Digest and email generation
* **GPT-4.1** – Personalized article ranking
* **PostgreSQL** – Database storage
* **SQLAlchemy** – ORM for database operations
* **BeautifulSoup** – Web scraping
* **Feedparser** – RSS feed parsing
* **YouTube Transcript API** – Fetching video transcripts
* **Pydantic** – Structured and validated LLM outputs
* **SMTP** – Email delivery

## AI Components

### DigestAgent

Generates short, technically accurate summaries from articles and video transcripts.

### CuratorAgent

Ranks summaries based on:

* User interests
* Expertise level
* Technical depth
* Practical value
* Novelty
* Actionability

### EmailAgent

Creates a personalized newsletter containing the top-ranked articles, summaries, and links.

## Database Tables

* `youtube_videos`
* `openai_articles`
* `anthropic_articles`
* `digests`

## Project Structure

```text
main.py
app/
├── agent/
│   ├── curator_agent.py
│   ├── digest_agent.py
│   └── email_agent.py
├── database/
│   ├── connection.py
│   ├── create_tables.py
│   ├── models.py
│   └── repository.py
├── profiles/
│   └── user_profile.py
├── scrapers/
│   ├── anthropic.py
│   ├── openai.py
│   └── youtube.py
└── services/
    ├── process_curator.py
    ├── process_digest.py
    ├── process_email.py
    └── process_youtube.py
```

## Running the Project

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the pipeline:

```bash
python main.py
```

Optional arguments:

```bash
python main.py 24 10
```

* `24` → collect news from the last 24 hours
* `10` → generate a digest containing the top 10 articles

## Environment Variables

Create a `.env` file containing:

```env
OPENAI_API_KEY=your_openai_api_key
MY_EMAIL=your_email
APP_PASSWORD=your_gmail_app_password
DATABASE_URL=your_database_url
```

## Future Improvements

* Add a web dashboard
* Support more news sources
* Add duplicate-content detection
* Improve ranking using embeddings
* Add scheduled automatic execution
* Add user login and multiple profiles
* Deploy the application using Docker or cloud services

## Project Objective

The objective of this project is to reduce the time required to follow AI developments by automatically collecting, summarizing, personalizing, and delivering relevant AI news in one daily newsletter.
