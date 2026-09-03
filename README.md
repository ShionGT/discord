# Discord Bot Application

A web-based landing and installation interface for a Discord bot application.

The project provides users with the information they should review before using the application, including the **Terms of Service** and **Privacy Policy**, followed by a dedicated Discord installation page.

---

## Project Structure

```text
.
├── index.html
├── installation.html
└── README.md
```

### `index.html`

The main information and agreement page.

It contains:

* Terms of Service
* Privacy Policy
* Privacy/data collection information
* User responsibilities
* Discord-related terms
* Bot permissions information
* Agreement checkbox
* Continue button

The user must agree to the Terms of Service and Privacy Policy before continuing to the application.

---

### `installation.html`

The Discord installation page.

It provides:

* Discord application installation information
* Requested permission summary
* Installation instructions
* Security information
* **Add to Discord** button

The installation button redirects the user to Discord's official OAuth2 authorization page.

---

## User Flow

The intended user flow is:

```text
┌───────────────────────┐
│       index.html      │
│                       │
│  Terms of Service     │
│  Privacy Policy       │
│  Application Details  │
└───────────┬───────────┘
            │
            │ Accept Terms
            ▼
┌───────────────────────┐
│  installation.html    │
│                       │
│  Discord Application  │
│  Installation Deck    │
└───────────┬───────────┘
            │
            │ Add to Discord
            ▼
┌───────────────────────┐
│       Discord         │
│                       │
│  Select Server        │
│  Review Permissions   │
│  Authorize            │
└───────────┬───────────┘
            │
            ▼
┌───────────────────────┐
│     Discord Server    │
│                       │
│      Bot Installed    │
└───────────────────────┘
```

---

## Discord Installation

The application uses Discord's OAuth2 authorization system for bot installation.

The current application uses:

```text
Client ID:
1544682128099254432
```

The OAuth2 scopes are:

```text
bot
applications.commands
```

The requested permission integer is:

```text
274878286912
```

The installation URL is:

```text
https://discord.com/oauth2/authorize?client_id=1544682128099254432&scope=bot+applications.commands&permissions=274878286912
```

Users are redirected to Discord's authorization page rather than entering their Discord credentials into this website.

---

## Running Locally

This project is a static website and does not require a backend to display the current pages.

### Option 1 — Open Directly

You can open:

```text
index.html
```

directly in a web browser.

However, using a local web server is recommended.

### Option 2 — Python HTTP Server

If Python is installed:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

### Option 3 — VS Code Live Server

If using Visual Studio Code, you can install a Live Server extension and open `index.html` through the local development server.

---

## Configuration

### Application URL

The Continue button in `index.html` currently redirects to:

```javascript
window.location.href = "/app";
```

Change this if your actual application uses a different URL.

For example:

```javascript
window.location.href = "/dashboard";
```

or:

```javascript
window.location.href = "https://example.com/app";
```

---

## Terms of Service and Privacy Policy

The Terms of Service and Privacy Policy included in this project are intended as a **generic starting template for a Discord bot application**.

Before using the project as a public service, review and modify them to accurately describe:

* What information the bot collects
* What information the website collects
* How Discord information is processed
* What information is stored
* How long information is retained
* Whether logs are stored
* Whether message content is processed
* Third-party services
* Hosting providers
* Analytics
* Authentication
* Data deletion procedures
* Applicable laws and jurisdiction
* Contact information

The policies should accurately reflect the actual implementation.

---

## Security

The website should never request users to provide:

* Discord passwords
* Discord authentication tokens
* Recovery codes
* API keys
* Private keys
* Cryptocurrency recovery phrases
* Payment card information

Discord authorization should be performed through Discord's official OAuth2 authorization system.

The installation page also includes a security notice reminding users to verify that they are authorizing the application through Discord.

---

## Discord Permissions

The current OAuth2 installation URL requests:

```text
permissions=274878286912
```

This should be reviewed before production deployment.

The application should request **only the permissions required for the bot's actual functionality**.

For example, if the bot only needs to send messages, it should not request administrative permissions.

A future improvement should be to replace the generic permission summary with a complete list of the human-readable Discord permissions requested by the bot.

---

## Deployment

Because the current project consists of static HTML and CSS/JavaScript, it can be hosted using many static hosting providers.

Typical deployment structure:

```text
public/
├── index.html
├── installation.html
└── README.md
```

The website can then be deployed behind HTTPS.

HTTPS is strongly recommended for the production website, especially if authentication, OAuth callbacks, cookies, or user-specific application data are added later.

---

## Future Development

Potential future features include:

### Discord OAuth2 Login

Allow users to log into the website using Discord.

```text
User
  │
  ▼
Discord OAuth2
  │
  ▼
Website Dashboard
```

### Server Dashboard

Allow authorized server administrators to configure the bot through a web interface.

Possible features:

* Server selection
* Bot configuration
* Command configuration
* Moderation settings
* Logging settings
* Notification settings
* Role configuration
* Channel configuration

### Bot Status

Display information such as:

```text
Bot Status: Online
Servers: 42
Latency: 38ms
Uptime: 99.9%
```

### Database

Store server-specific configuration such as:

```json
{
    "guild_id": "123456789",
    "prefix": "!",
    "logging_enabled": true,
    "log_channel": "987654321"
}
```

### Terms Version Tracking

For production use, agreement records could track:

```text
Discord User ID
Terms Version
Privacy Policy Version
Accepted At
```

This makes it possible to determine which version of the policies a user agreed to.

---

## Important Legal Notice

The included Terms of Service and Privacy Policy are generic templates and **do not constitute legal advice**.

They should be reviewed and adapted before the application is released publicly, particularly if the service stores personal information or operates across multiple jurisdictions.
