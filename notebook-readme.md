# Agent Cold Email Generator

This Jupyter notebook implements an automated system for generating personalized cold emails based on job postings. The system uses AI agents to parse job descriptions and craft tailored outreach messages.

## Features

- Web scraping functionality for job posting data
- Automated job description parsing
- Intelligent cold email generation
- Configurable AI agents using the pydantic-ai framework

## Prerequisites

```bash
pip install -r requirements.txt
```

Required packages:
- pydantic-ai
- beautifulsoup4
- requests
- html2text
- python-dotenv
- nest-asyncio
- rich

## Project Structure

The notebook consists of several key components:

1. **Web Scraping Module**
   - Functions for fetching and cleaning website content
   - HTML to Markdown conversion
   - Content storage with timestamps

2. **Job Description Parser**
   - Extracts key information from job postings:
     - Role/position title
     - Company name
     - Required experience
     - Required skills
     - Detailed job description

3. **Cold Email Generator**
   - Creates personalized outreach emails with:
     - Attention-grabbing subject lines
     - Relevant skill matching
     - Professional formatting
     - Clear call-to-action

## Usage

1. Set up your environment variables in a `.env` file
2. Run the notebook cells in sequence
3. Provide a job posting URL to analyze
4. Receive a structured job description and generated cold email

## Example Usage

```python
# Parse job description
job_post_url = "https://boards.greenhouse.io/company/jobs/123456"
job_description = job_description_parser_agent.run_sync(
    user_prompt="Please extract job description for the provided URL",
    deps=JobInformationFetchDeps(job_post_url=job_post_url)
)

# Generate cold email
email = cold_email_writer_agent.run_sync(
    "Please write a cold email",
    deps=ColdEmailWriterAgentInput(job_description=job_description.data)
)
```

## Model Configuration

The system uses the Groq LLaMA 3 70B model for optimal performance:
- Job Description Parser: `groq:llama3-70b-8192`
- Cold Email Writer: `groq:llama3-70b-8192`

## Error Handling

The notebook includes robust error handling for:
- Failed web scraping attempts
- Invalid URLs
- Parsing errors
- Model response failures

## Note

This tool is designed for professional recruitment purposes. Ensure compliance with all applicable email and recruitment regulations when using the generated content.
