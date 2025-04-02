# n8n Claude Integration MCP

This project provides a Minimum Compatible Project (MCP) for integrating n8n with Anthropic's Claude.

## Overview

n8n is an open-source workflow automation platform that allows you to connect different services and automate tasks. Claude is Anthropic's advanced AI assistant. This MCP demonstrates how to set up n8n and use it with Claude via LangChain integration.

## Prerequisites

- Node.js (>= 20.15)
- pnpm (>= 10.2.1)
- An Anthropic API key (get one at [https://console.anthropic.com/](https://console.anthropic.com/))

## Setup Instructions

### 1. Install n8n

You can install n8n in multiple ways:

#### Using npx (simplest option):

```bash
npx n8n
```

#### Using Docker:

```bash
docker volume create n8n_data
docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n
```

### 2. Access n8n

Open your browser and go to:
```
http://localhost:5678
```

### 3. Configure Claude Integration

1. In the n8n dashboard, click on "Settings" and then "Credentials"
2. Click "+ Add Credential"
3. Search for and select "Anthropic"
4. Enter your Anthropic API key and save

### 4. Create a Workflow

See the included workflows in this repository for examples of:

1. `simple-claude-prompt.json` - Basic prompt to Claude
2. `claude-chat-history.json` - Conversation with memory
3. `claude-with-tools.json` - Using Claude with external tools

## Sample Workflows

This repository includes sample workflows demonstrating:

1. Basic Claude integration
2. Using Claude with memory
3. Building an agent with tools
4. Processing documents with Claude

## Advanced Integration

For more advanced scenarios:

1. Use the "Chain" nodes to create complex LLM pipelines
2. Use the "Memory" nodes to persist conversations
3. Use the "Tool" nodes to give Claude capabilities like web search

## Troubleshooting

- If you encounter API rate limits, consider adjusting your workflow timing
- For large token usage, monitor your Anthropic account limits
- Check the n8n logs for detailed error messages

## Resources

- [n8n Documentation](https://docs.n8n.io/)
- [n8n LangChain Integration Docs](https://docs.n8n.io/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.lmchatanthropic/)
- [Anthropic API Documentation](https://docs.anthropic.com/claude/reference/getting-started-with-the-api)
