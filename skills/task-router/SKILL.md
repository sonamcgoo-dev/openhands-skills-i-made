# Task Router

## Purpose
When triggered, analyzes the current task and conversation context, then routes/delivers work to the appropriate external platform, service, or agent. Think of it as a smart dispatcher that figures out where work should go.

## Trigger
- **Activation phrase**: `lets route that`
- Case-insensitive
- Context-aware — uses conversation history to understand what needs routing

## How It Works

### Phase 1: Analyze Context
- Review conversation history and recent messages
- Identify what task needs to be completed
- Determine what platform/service can handle it
- Check for any relevant files, data, or credentials in context

### Phase 2: Determine Destination
Based on task analysis, route to appropriate destination:

| Task Type | Route To |
|-----------|----------|
| Create a website/page | Wix, WordPress, Webflow, Squarespace |
| Manage e-commerce | Shopify, WooCommerce, BigCommerce |
| Send a message/notification | Email, Slack, Discord, Telegram |
| Create content | Medium, Substack, Ghost |
| Manage customer data | CRM (HubSpot, Salesforce) |
| Handle payments | Stripe, PayPal |
| Create documents | Notion, Google Docs |
| Track issues | Linear, Jira, Asana |
| Social media | Twitter, LinkedIn, Instagram |
| File storage | Dropbox, Google Drive, S3 |
| Database operations | Airtable, Firebase, Supabase |

### Phase 3: Route & Execute
- Connect to the target platform via API
- Prepare and format data appropriately
- Execute the task (create, update, send, etc.)
- Handle authentication and errors

### Phase 4: Report
- Confirm task was routed successfully
- Provide links/references to created content
- Summarize what was done

## Supervisor Prompt

You are the Task Router. When "lets route that" is detected:

1. **ANALYZE** the context:
   ```
   - What task needs to be completed?
   - What data/information is available in conversation?
   - What is the intended outcome?
   ```

2. **DETERMINE** the destination:
   ```
   - Which platform/service can fulfill this task?
   - What credentials/API access is needed?
   - Is the task even possible via API?
   ```

3. **PREPARE** the payload:
   ```
   - Format data for the target platform
   - Gather necessary authentication
   - Map conversation context to platform schema
   ```

4. **ROUTE** the task:
   ```
   - Execute via platform API
   - Create page, send message, update record, etc.
   - Handle any errors gracefully
   ```

5. **REPORT** results:
   ```
   - What was created/updated?
   - Provide links if applicable
   - Explain what was done
   - Note any limitations or next steps
   ```

## Example Requests

**Content Routing:**
```
User: "I need to turn this research into a blog post and publish it"
Assistant: "lets route that" → Analyzes research → Routes to WordPress Medium API → Creates and publishes post
```

**E-commerce Routing:**
```
User: "Add these 50 products to my Shopify store with images and descriptions"
Assistant: "lets route that" → Parses product data → Routes to Shopify API → Bulk creates products
```

**Notification Routing:**
```
User: "Ping my team in Slack that the deployment is done"
Assistant: "lets route that" → Formats message → Routes to Slack API → Posts to channel
```

**CRM Routing:**
```
User: "Create leads in HubSpot for everyone who signed up today"
Assistant: "lets route that" → Extracts signups → Routes to HubSpot API → Creates lead records
```

**Multi-Platform Routing:**
```
User: "Same announcement to Twitter, LinkedIn, and our newsletter"
Assistant: "lets route that" → Formats for each platform → Routes to all three APIs → Confirms all posted
```

## Supported Platforms

### Website Builders
- **Wix** — Create pages, update content, manage site
- **WordPress** — Posts, pages, media, plugins
- **Webflow** — CMS items, collections
- **Squarespace** — Pages, products

### E-commerce
- **Shopify** — Products, orders, customers
- **WooCommerce** — Products, orders
- **BigCommerce** — Catalog management

### Communication
- **Email (SMTP/API)** — Send emails
- **Slack** — Messages, channels, webhooks
- **Discord** — Messages, webhooks
- **Telegram** — Bot messages

### Social Media
- **Twitter/X** — Posts, media
- **LinkedIn** — Posts, articles
- **Reddit** — Posts, comments

### Content Platforms
- **Medium** — Posts, articles
- **Substack** — Newsletters
- **Ghost** — Posts, pages

### Productivity & CRM
- **Notion** — Pages, databases
- **Google Docs/Sheets** — Documents, data
- **HubSpot** — Contacts, deals, tickets
- **Salesforce** — Leads, opportunities
- **Linear** — Issues, projects
- **Jira** — Tickets, sprints
- **Asana** — Tasks, projects

### Payments
- **Stripe** — Customers, invoices, subscriptions
- **PayPal** — Invoices, payments

### Data & Storage
- **Airtable** — Bases, tables, records
- **Google Drive** — Files, folders
- **Dropbox** — Files
- **Firebase** — Database, storage

## Context Extraction

The router automatically extracts from conversation:

- **URLs** — Links to pages, images, files
- **Code snippets** — For embedding or integration
- **Data structures** — JSON, lists, tables
- **User info** — Names, emails, identifiers
- **Content** — Text blocks, descriptions, bios
- **Credentials** — API keys, tokens (stored securely)

## Error Handling

If routing fails:

1. **Platform unavailable** → Try alternative platform or notify user
2. **Auth failed** → Request credentials from user
3. **API limit hit** → Retry later or suggest manual action
4. **Invalid data** → Attempt to fix format or ask for clarification
5. **Partial failure** → Complete what's possible, report what's not

## Limitations

- **Platform APIs** — All have rate limits and restrictions
- **Authentication** — May need user-provided API keys/tokens
- **Complex tasks** — May need multiple API calls or manual steps
- **Platform ToS** — Some platforms prohibit automated posting
- **No UI tasks** — Can only do what APIs allow (no clicking buttons on websites)

## Important Notes

- Always respect platform Terms of Service
- Store credentials securely (never log them)
- Implement rate limiting to avoid bans
- Provide fallback options when possible
- Be transparent about what's possible vs. what's blocked
