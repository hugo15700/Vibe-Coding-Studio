# Vibe Coding Studio

A lightweight, single-page code editor prototype for experimenting with Vibe Coding. The interface is entirely in English and includes a project explorer, an editable code area, a live preview, and an AI assistant that stays unavailable until an API connection has been verified.

## Getting started

Open `index.html` in a modern browser. No package installation or build step is required.

The editor starts with a sample HTML, CSS, JavaScript, and README project. Select a file in the Explorer, make changes in the editor, and select **Run** to refresh the preview. The **+** button creates additional in-memory files.

> Project edits and new files are kept only for the current page session. Reloading or closing the page resets the sample project.

## Connecting an AI provider

1. Open the assistant's **Setup** tab.
2. Enter an API base URL, model name, and API key for an OpenAI-compatible Chat Completions endpoint.
3. Select **Connect and verify**. The studio sends a short test request; the Chat tab unlocks only after a valid response.
4. Use **Disconnect** in Setup to remove the active connection and clear the key from the page.

The default endpoint is `https://api.openai.com/v1`, and the default model is `gpt-4o-mini`. Providers must support the OpenAI-compatible `/chat/completions` endpoint, browser requests, and CORS. If opening the file directly does not work with a provider, serve the folder from localhost, for example:

```powershell
py -m http.server 8000
```

Then open `http://localhost:8000` in your browser.

## Privacy and safety

- The API key is held in page memory only. It is not saved to a file, browser storage, or a server, and is cleared when you disconnect or reload the page.
- Prompts and the connection-verification request are sent directly from your browser to the API endpoint you configure.
- A browser-only app cannot keep an API key secret from its user or provide server-side protections. Use only providers and endpoints you trust; do not use a personal key in a public or shared deployment.
- Review AI-generated code before running it. The preview is sandboxed, but code you choose to run can still make network requests permitted by the browser sandbox.
- Back up project work you want to keep; this prototype does not persist files.

## Current limitations

Vibe Coding Studio is a front-end prototype, not a full IDE or hosted AI service. Files exist only in memory, and the AI connection is made directly from the browser. The editor does not yet provide syntax highlighting, project saving, or filesystem access.
