# n8n + Claude Integration Setup Guide

This guide will walk you through setting up n8n and integrating it with Anthropic's Claude.

## Prerequisites

1. An Anthropic API key (get one at [https://console.anthropic.com/](https://console.anthropic.com/))
2. Node.js installed (v20.15+)
3. pnpm installed (v10.2.1+)

## Step 1: Install n8n

You have multiple options for installing n8n:

### Quick Start with npx

```bash
npx n8n
```

This will start n8n immediately and you can access it at http://localhost:5678

### Using Docker

```bash
docker volume create n8n_data
docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n
```

### Installing Globally

```bash
npm install n8n -g
n8n start
```

## Step 2: Configure Anthropic API Credentials

1. Open n8n in your browser: http://localhost:5678
2. Navigate to Settings (⚙️) > Credentials
3. Click "+ Add Credential"
4. Search for and select "Anthropic"
5. Enter your Anthropic API key
6. Click "Save"

## Step 3: Import a Workflow

To try out Claude integration:

1. Go to Workflows
2. Click "Import from File"
3. Select one of the workflow JSON files from this repository
4. Update the credential ID in the Claude node to match your saved credential

## Step 4: Configure and Run Your Workflow

Each sample workflow demonstrates different capabilities:

### Simple Claude Prompt

This workflow demonstrates basic interaction with Claude:
- Modify the prompt in the "Set Prompt" Code node
- Execute the workflow to see Claude's response

### Claude with Chat History

This workflow shows how to implement memory for multi-turn conversations:
- The Memory Buffer Window node stores conversation history
- You can modify the system message to change Claude's personality
- Each execution adds to the conversation history

### Claude with Tools

This workflow shows Claude working with external tools:
- Calculator tool for math operations
- Wikipedia tool for factual lookups
- HTTP Request tool for external APIs
- The Agent node orchestrates tool use based on the query

## Advanced Configurations

### Claude Models

You can select different Claude models based on your needs:
- Claude 3.7 Sonnet: Best overall performance and reasoning
- Claude 3.5 Sonnet: Strong performance for most tasks
- Claude 3 Opus: Highest intelligence and reasoning
- Claude 3 Sonnet: Good balance of capabilities
- Claude 3 Haiku: Fastest and most cost-effective

### Thinking Mode

Claude 3 models support "thinking" mode through n8n:
1. In the Anthropic Chat Model node, go to "Options"
2. Enable "Enable Thinking"
3. Adjust "Thinking Budget (Tokens)" (min: 1024)

Thinking mode allows Claude to perform step-by-step reasoning internally before responding, which can lead to more accurate and thoughtful answers, especially for complex questions.

### Parameter Tuning

- Temperature: Controls randomness (0.0-1.0), lower values produce more deterministic outputs
- Top P: Controls diversity via nucleus sampling (0.0-1.0)
- Max Tokens: Limits the length of Claude's responses

## Creating Custom Integrations

### Building Agents with Claude

To create a custom agent with Claude:
1. Use the Agent node with "tools" agent type
2. Connect Claude as the language model
3. Add relevant tools (HTTP requests, calculations, etc.)
4. Set an appropriate system message
5. Configure input/output parameters

### Persistent Memory

For conversations that persist across sessions:
1. Replace Memory Buffer Window with Memory Postgres Chat or Memory Redis Chat
2. Configure database credentials
3. Set a session ID to track separate conversations

### Document Processing with Claude

To process documents with Claude:
1. Add Document Loader nodes to import files
2. Use Text Splitter nodes to chunk documents appropriately
3. Use Vector Store nodes to create embeddings
4. Use Chain Retrieval QA to connect Claude with the data

## Troubleshooting

### API Key Issues
- Ensure your API key is correctly entered in credentials
- Check that you have sufficient credits in your Anthropic account

### Model Errors
- Verify model name is correctly spelled and available to your account
- Check token limits if responses are being cut off

### Connection Issues
- Ensure n8n can access the internet
- Check for any proxy or firewall settings blocking API calls

## Resources

- [n8n Documentation](https://docs.n8n.io/)
- [Anthropic API Documentation](https://docs.anthropic.com/claude/reference)
- [n8n LangChain Integration](https://docs.n8n.io/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.lmchatanthropic/)

For more detailed examples and workflow templates, check the other files in this repository.
