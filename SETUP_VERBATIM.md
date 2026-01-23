# Verbatim Archival Setup Guide

To enable truly verbatim, non-truncated archival of your emails from the terminal, we will use a dedicated Python script. This is the **long-term workflow** that avoids current MCP limitations and browser interaction.

## 🛠️ One-Time Setup

1.  **Enable Gmail API:**
    -   Go to the **[Google Cloud Console](https://console.cloud.google.com/)**.
    -   Create a new project (e.g., `Gmail-Verbatim-Archive`).
    -   Go to **APIs & Services > Library** and search for "Gmail API". Click **Enable**.

2.  **Configure OAuth Consent Screen:**
    -   Go to **APIs & Services > OAuth consent screen**.
    -   User Type: **External** (or Internal if available for your university).
    -   App name: `Gmail Archiver`.
    -   Add your email to **Test users** (This is critical!).

3.  **Create Credentials:**
    -   Go to **APIs & Services > Credentials**.
    -   Click **Create Credentials > OAuth client ID**.
    -   Application type: **Desktop app**.
    -   Download the JSON file and rename it to **`credentials.json`**.
    -   Place it in this workspace folder: `C:\Users\dhl\.gemini\antigravity\scratch\gmail-mcp-workspace\`.

4.  **Install Dependencies:**
    ```bash
    pip install --upgrade google-api-python-client google-auth-httplib2 google-auth-oauthlib
    ```

## 🚀 Usage

Run the archival script:
```bash
python archive_verbatim.py
```

### What happens next?
-   A browser window will open **on your machine** for a one-time Google login to authorize the script.
-   The script will download the **raw RFC822 (.eml)** data for all self-sent emails.
-   Files will be saved in the `emails_verbatim/` directory.

---
*This workflow ensures 100% fidelity. No truncation. No AI summarization.*
