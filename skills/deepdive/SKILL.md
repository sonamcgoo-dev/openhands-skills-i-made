# Deep Dive Web Scraper

## Purpose
When the trigger phrase **"deepdive"** is detected, this skill performs comprehensive web scraping and research on any topic or URL, generating a conclusive markdown report.

## Trigger
- **Activation phrase**: `deepdive`
- Case-insensitive matching
- Can be followed by:
  - A URL: `deepdive https://example.com`
  - A topic: `deepdive AI trends 2024`
  - A question: `deepdive how do neural networks work`

## Capabilities

### Web Scraping
- **Single pages**: Extract all text, links, images, metadata
- **Full websites**: Crawl and map site structure (configurable depth)
- **Search results**: Gather information from multiple sources on a topic
- **Data extraction**: Emails, prices, contact info, product details, articles

### Dark Web (Optional)
- Requires Tor proxy setup (`tor://` or SOCKS proxy on port 9050)
- Falls back to surface web if Tor unavailable
- Common `.onion` URLs can be accessed if Tor is running

### Research Sources
- Google search results
- Wikipedia and wikis
- News articles
- Documentation sites
- Social media content
- Academic papers (via search)
- Any public website

## Output

Generates a comprehensive markdown report saved to the workspace:
- `deepdive-report-{timestamp}.md`

### Report Structure
```
# Deep Dive Report: [Topic]

## Executive Summary
[Quick overview of findings]

## Key Findings
[Main discoveries organized by category]

## Detailed Analysis
[In-depth information from each source]

## Data Extracted
[Any structured data: emails, prices, links, etc.]

## Sources
[List of all URLs scraped with timestamps]

## Conclusion
[Conclusive summary with actionable insights]
```

## Usage Examples

**Scrape a URL:**
> "deepdive https://news.example.com/article"

**Research a topic:**
> "deepdive the latest developments in quantum computing"

**Deep research on a subject:**
> "deepdive everything about renewable energy trends 2024"

**Dark web research (if Tor available):**
> "deepdive tor://example.onion/some-page"

## Technical Notes

### Web Scraping Methods
1. **Tavily API**: For search and content extraction (if available)
2. **Browser tools**: For interactive sites and JavaScript content
3. **Direct HTTP**: For simple page fetching
4. **Crawl**: For site-wide scraping with configurable breadth/depth

### Dark Web Requirements
- Tor daemon running on localhost:9050
- Or `torify` command available
- Note: Some dark web sites may be offline or require authentication

### Limitations
- Rate limiting may apply to aggressive scraping
- Some sites block scraping (robots.txt respected)
- JavaScript-heavy sites may need browser rendering
- Tor connections are slower than surface web

## Supervisor Prompt

You are the Deep Dive Researcher. When "deepdive" is detected:

1. **PARSE** the request:
   - Extract target URL or topic
   - Determine scraping scope (single page vs. full research)
   - Identify any special requirements

2. **EXECUTE** scraping:
   - Use Tavily for comprehensive web research
   - Crawl target pages for detailed content
   - Extract structured data where applicable
   - Handle dark web URLs if `tor://` prefix detected

3. **ANALYZE** findings:
   - Organize information by theme
   - Identify key insights and patterns
   - Extract actionable data points
   - Cross-reference multiple sources

4. **GENERATE** report:
   - Write comprehensive markdown report
   - Include executive summary
   - List all sources
   - Add conclusion with findings

5. **DELIVER**:
   - Save report as `deepdive-report-{timestamp}.md`
   - Confirm file location to user
   - Summarize key findings in chat

## Important Rules
- Always save the report as a markdown file
- Include source URLs in the report
- Be thorough but concise in summaries
- Handle errors gracefully (continue with available data)
- If Tor unavailable for dark web, note this and use surface web alternatives
