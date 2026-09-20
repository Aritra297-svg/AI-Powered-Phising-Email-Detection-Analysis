# Bytex Fraud Detect AI

Bytex Fraud Detect AI is a browser-based prototype for analyzing suspicious email and identifying common phishing indicators.

## Features

- Browser-local login and account creation for the demo workspace
- Explainable local heuristic analysis that works offline
- Optional Google Gemini analysis for richer rationale and risk assessment
- Risk score from 0 to 100 with verdict and recommended action
- Detection of urgency, credential requests, suspicious links, lookalike domains, generic greetings, and sender anomalies
- Load built-in phishing and benign samples
- Analyze pasted email content or local `.eml` and `.txt` files
- Responsive interface with no build process or framework required

## Run Locally

No installation is required.

1. Open `index.html` in a modern web browser.
2. Select **Create account** and create a test-only local account.
3. Paste an email, load a sample, or open a local `.eml` or `.txt` file.
4. Select **Analyze email**.

The application can also be served from any static web server if preferred.

## Optional Gemini Configuration

To enable AI-assisted analysis:

1. Create a Gemini API key through Google AI Studio.
2. Open **API settings** in the application.
3. Paste the key and select **Save key**.
4. Analyze an email normally.

The key is stored in browser Local Storage under `phishguard_gemini_key`. If Gemini is unavailable, the application automatically shows the local analysis instead.

## Technology

- HTML5
- CSS3
- Vanilla JavaScript
- Browser Local Storage
- Fetch API
- Google Gemini `gemini-2.0-flash` API, optional

## Project Files

- `index.html` - Complete application, including markup, styles, and JavaScript
- `PROJECT_DOCUMENTATION.txt` - Detailed behavior, heuristics, API information, and security notes

## Security and Privacy

This is a security-awareness prototype, not an enterprise email security product. Results are advisory and should be verified through a trusted channel.

The prototype calls Gemini directly from the browser when an API key is configured. This exposes the key to the browser user and is not suitable for production. A production deployment should use:

```text
Browser UI -> HTTPS backend -> Gemini API
```

The backend should keep `GEMINI_API_KEY` in a server-side secret manager or environment variable, authenticate requests, apply rate and request-size limits, and avoid logging sensitive email content.

The demo account is also stored in browser Local Storage and must not be used with real credentials.

## Limitations

- Local detection uses simple, explainable rules rather than a trained statistical classifier.
- Gemini responses may be inaccurate or unavailable.
- Email content is sent to Google only when Gemini is configured and analysis is requested.
- The prototype does not connect to a mailbox or provide enterprise incident-response controls.
