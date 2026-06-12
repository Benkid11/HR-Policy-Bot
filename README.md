# HR Assistant

This repository contains two main components for an HR support experience:

1. `index.html` — a standalone web-based HR assistant interface.
2. `UPL HR BOT.json` — an n8n workflow that powers the HR assistant with AI, vector search, memory, and document ingestion.

---

## Project Overview

The HR Assistant is built to answer employee questions about HR policies, including leave, benefits, payroll, attendance, and conduct.

### `index.html`

- A lightweight chat interface with HTML, CSS, and JavaScript.
- Sends user queries to a webhook endpoint.
- Displays bot replies with styling, typing indicators, and structured response rendering.
- Includes quick prompt buttons for common HR questions.

### `UPL HR BOT.json`

- An n8n workflow definition for the backend logic.
- Uses a chat trigger and an AI agent to process incoming HR questions.
- Connects a vector store tool for document retrieval and a memory buffer for conversational context.
- Loads HR policy documents from Google Drive, splits text into chunks, and creates embeddings with Mistral Cloud.
- Uses a Mistral Cloud chat model for response generation.

---

## Files

- `index.html` — the client-side chatbot UI.
- `UPL HR BOT.json` — the n8n workflow for the chat backend.

---

## How to Use

### Web UI

1. Open `index.html` in a browser.
2. Enter an HR question in the text field.
3. Press `Enter` or click the send button.
4. The UI posts the query to the configured webhook and shows the response.

### n8n Workflow

1. Import `UPL HR BOT.json` into your n8n instance.
2. Confirm the workflow has these credentials available:
   - `Mistral Cloud` API credentials
   - `Google Drive OAuth2` credentials
3. Confirm the webhook endpoint in `index.html` matches the webhook URL exposed by n8n.
4. Activate the workflow in n8n.
5. Use the web UI or chat trigger endpoint to ask questions.

---

## Deployment

1. Host `index.html` as a static page (local file, web server, or static hosting service).
2. Host n8n and enable the workflow.
3. Update the webhook URL in `index.html` if the n8n endpoint changes.
4. Ensure the HR policy document is available in Google Drive and properly downloaded into the vector store.

---

## Configuration

### `index.html`

Update the webhook URL in the script section when needed:

```js
const WEBHOOK_URL = "...";
```

### `UPL HR BOT.json`

- Review the AI agent system prompt and tool configuration.
- Adjust retrieval settings, response formatting rules, or memory behavior as needed.
- Make sure the document loader and embedding pipeline are connected correctly.

---

## Important Notes

- The UI is a static, self-contained HTML page with inline styles and JavaScript.
- The workflow expects HR policy content to be loaded and indexed so the assistant can answer accurately.
- Keep the webhook and API credentials secure.
- Do not publish the webhook URL in a public repository or client-side source without protection.
- Consider using a backend proxy, authentication token, or IP restrictions for webhook access.
- This project is intended for internal HR support and should be deployed in a controlled environment.

---

## License

No license is included. Add a suitable license if you plan to share or distribute this project.
