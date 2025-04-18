---
title: Connect Cursor to MCP for GitHub Control
---

# 🔄 MCP + Cursor GitHub Setup

> Set up full GitHub control via Cursor once your MCP server is running.

## 🛠️ Step-by-Step Cursor Setup for MCP

### 🧭 1. Open Cursor Editor
- Launch **Cursor**, the AI-first code editor.
- Click **Settings** (bottom-left corner ⚙️).

### 🌐 2. Navigate to MCP Section
- In **Settings**, scroll down to the **MCP (Model Context Protocol)** section.
- Click **"Add Server"**.

### 🔧 3. Fill in MCP Server Details
- **Name:** `Local MCP Server`
- **URL:** `http://localhost:3333` (or your configured port from `server.js`)
- **Client:** Select `ollama` or your preferred LLM engine.
- **Auth:** Leave blank for local use (behind firewall). Add headers if using token-based auth.

✅ Cursor is now connected to your MCP server!

## ⚙️ Make Sure Your MCP Server Is Running
Run your server locally from your terminal:

```bash
node server.js
```

Expected output:

```bash
✅ MCP server running at http://localhost:3333
```

## 🤖 Use Cursor Prompts to Control GitHub
With MCP connected, use the Cursor command palette:

<kbd>⌘ + K</kbd> / <kbd>Ctrl + K</kbd> → Type:

```text
Create a private GitHub repo named ai-lab
Add README.md to ai-lab repo with initial text
Search repositories about 'android hacking tools'
```

> MCP GitHub plugin (`@smithery-ai/github`) handles GitHub API calls via your server.

## ✅ Available GitHub Tools via MCP

| Tool                  | Description                      |
|-----------------------|----------------------------------|
| `create_or_update_file` | Create or update files          |
| `create_repository`     | Create a new GitHub repository  |
| `delete_repository`     | Delete a repository (if supported) |
| `get_file_contents`     | Read contents of files          |
| `search_repositories`   | Discover GitHub repositories    |

These tools can be triggered through Cursor's prompt bar or:

```bash
npx @smithery/cli
```

## 🧠 Best Practice Tips

- Keep your `mcp.json` secure (especially GitHub tokens).
- Use environment variables for secrets in production.
- Test server connection with:

```bash
curl http://localhost:3333
```

> Logs will show tool calls and API responses for easier debugging.



# MCP_server_cursor_to_github
https://smithery.ai/server/@smithery-ai/github

cursor download for your operating system 

and then github setting ->developer -> token -> generate-> auth -> users-> repository

Make sure to copy your token now as you will not be able to see it again.

just_think

create new think my token

Created today.
Expires on Sun, May 18 2025
Access on @Ankitkushwaha90 Ankitkushwaha90
Repository access
This token has access to all repositories owned by you.
User permissions
 Read access to Copilot Chat, Copilot Editor Context, models, plan, private repository invitations, and user events
 Read and Write access to blocking, codespaces user secrets, email addresses, followers, gists, git signing ssh public keys, gpg keys, interaction limits, keys, profile, starring, user knowledge bases, and watching
Repository permissions
 Read access to codespaces metadata and metadata
 Read and Write access to Dependabot alerts, actions, actions variables, administration, attestations api, code, codespaces, codespaces lifecycle admin, codespaces secrets, commit statuses, dependabot secrets, deployments, discussions, environments, issues, merge queues, pages, pull requests, repository advisories, repository custom properties, repository hooks, secret scanning alerts, secrets, security events, and workflows

write mdx page for good understanding for setup github and mcp and cursors . for create repo
and other control from cursor to github account create delete communite and other write tutorial page
