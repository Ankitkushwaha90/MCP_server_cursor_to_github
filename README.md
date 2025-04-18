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




---
title: "MCP Server + GitHub Cursor Setup Guide"
description: "Step-by-step guide for setting up MCP server with Cursor GitHub integration for repo automation, creation, deletion, and commit control."
---

# 🚀 MCP Server + GitHub Cursor Integration

This tutorial walks you through setting up MCP with GitHub using Cursor and controlling repositories from the terminal or automation workflows.

## 📦 Prerequisites

- Node.js & npm installed
- [Cursor CLI](https://smithery.ai/server/@smithery-ai/github) downloaded for your OS
- A GitHub account
- An MCP-compatible agent setup with `@modelcontextprotocol/sdk`

---

## 🔐 Step 1: Create a GitHub Personal Access Token

1. Go to [GitHub Developer Settings](https://github.com/settings/tokens)
2. Click **"Fine-grained tokens" → Generate new token**
3. Set:
   - **Name**: `just_think`
   - **Expiration**: May 18, 2025 (or your preferred)
   - **Permissions**:
     - **Repositories**: Full Read/Write
     - **User**: Full Read/Write
4. Copy the token now. You **will not** see it again!

```text
github_pat_11A4PP7FQ07lGRHVynbe5e_... (keep it secret!)
```

---

## ⚙️ Step 2: Configure `mcp.json`

```json
{
  "defaultClient": "ollama",
  "ollama": {
    "baseUrl": "http://localhost:11434",
    "model": "llama2"
  },
  "github": {
    "token": "<your_copied_github_token>"
  },
  "agent": {
    "name": "DevOpsAgent",
    "persona": "An automation assistant for GitHub repo management"
  }
}
```

Save it as `mcp.json` in your project folder.

---

## 💻 Step 3: Run the MCP Studio Server

```js
// server.js
import { studio } from '@modelcontextprotocol/sdk/server/studio.js';

studio.run({
  config: './mcp.json',
  port: 3333
});
```

Then run:
```bash
node server.js
```

---

## 🧠 Step 4: Connect Cursor to GitHub

```bash
npx -y @smithery/cli@latest install @smithery-ai/github --client claude --config mcp.json
```

This will install the GitHub Cursor adapter and register the token from `mcp.json`.

---

## 🔧 Step 5: Automate Repo Control via Cursor

Use the terminal to create, delete, or manage GitHub repos:

### ✅ Create a Repository
```bash
npx @smithery/cli ask "Create a new private repo called test-automation"
```

### ❌ Delete a Repository
```bash
npx @smithery/cli ask "Delete the repo named old-project"
```

### 📥 Commit Code
```bash
npx @smithery/cli ask "Commit all changes to the repo my-app with message 'Init commit'"
```

---

## 📚 Use Cases

- 🚀 **CI/CD Pipelines** – Deploy workflows via GitHub Actions
- 🧠 **LLM Automation** – Agents can trigger repo events
- 🛡 **Secure DevOps** – Use fine-grained tokens to maintain security
- 🧰 **Full Dev Automation** – No manual clicking, fully terminal-driven

---

## 📎 Resources
- [Cursor GitHub Adapter](https://smithery.ai/server/@smithery-ai/github)
- [MCP SDK](https://npmjs.com/package/@modelcontextprotocol/sdk)
- [Ollama Server](https://ollama.com)

---

If you'd like a complete ready-to-clone repo with these files, just ask and I’ll generate one!

