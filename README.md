# OpenHands Skills Collection

A collection of custom skills for OpenHands AI agent.

## Installation

In any OpenHands conversation:
```
/add-skill https://github.com/sonamcgoo-dev/openhands-skills-i-made/tree/main/skills/[skill-name]
```

## Available Skills

---

### 🤖 Agent Supervisor
**Trigger:** `go time`

Spawns and coordinates multiple sub-agents to complete complex tasks.

```
/add-skill https://github.com/sonamcgoo-dev/openhands-skills-i-made/tree/main/skills/agent-supervisor
```

**Usage:**
```
go time and build me a REST API with tests and docs
```

---

### 🔍 Deep Dive
**Trigger:** `deepdive`

Comprehensive web scraping and research tool that generates markdown reports.

```
/add-skill https://github.com/sonamcgoo-dev/openhands-skills-i-made/tree/main/skills/deepdive
```

**Usage:**
```
deepdive AI trends in healthcare 2024
deepdive https://example.com/article
```

**Features:**
- Web page scraping
- Full website crawling
- Dark web support (via Tor)
- Research reports
- Data extraction

---

### ⚡ Automator
**Trigger:** `automate`

Creative automation agent for web, APIs, and platform integrations.

```
/add-skill https://github.com/sonamcgoo-dev/openhands-skills-i-made/tree/main/skills/automator
```

**Usage:**
```
automate "schedule this tweet for 9am"
automate "alert me when Bitcoin drops"
automate "monitor this page for changes"
```

**Supported Platforms:**
- Social: Twitter, LinkedIn, Reddit, Discord, Slack, Telegram
- Cloud: Gmail, Google Calendar, Drive, Notion
- Browser: Any website via Playwright/Selenium
- Monitoring: Uptime, price tracking, RSS feeds

---

## Quick Start

1. Add a skill to your OpenHands chat
2. Type the trigger keyword when you need it
3. Get results!

## License

MIT License
