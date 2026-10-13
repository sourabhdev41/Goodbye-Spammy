# Goodbye Spammy

**Goodbye Spammy** is a WordPress plugin that sweeps spammy comments and spammy form submissions into the Trash, with optional AI spam detection powered by OpenRouter, Google Gemini, ChatGPT (OpenAI) or Claude (Anthropic).

Built by [NRW India](https://wp.nrwone.in).

[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20me%20a%20coffee-ffdd00?logo=buymeacoffee&logoColor=black)](https://buymeacoffee.com/sourabhnrw)
![Version](https://img.shields.io/badge/version-1.0.1-blue)
![WordPress](https://img.shields.io/badge/WordPress-5.0%2B-21759b)
![PHP](https://img.shields.io/badge/PHP-7.2%2B-777bb3)
![License](https://img.shields.io/badge/license-GPL--2.0--or--later-green)

## Features

- **Comment cleanup:** moves every comment marked as spam to Trash, including those flagged by Akismet.
- **Instant trash:** new comments go straight to Trash the moment they are marked as spam.
- **Rule-based scan:** trashes pending comments with spam keywords, too many links, a URL used as the author name, or empty text. Keywords and link limit are editable.
- **AI detection (optional):** an AI model reviews pending comments and form messages and flags spam.
  - Providers: **OpenRouter**, **Google Gemini**, **ChatGPT (OpenAI)**, **Claude (Anthropic)**
  - Choose any model per provider and use your own API key
  - Optional live check on every new comment (fails open if the API is down)
  - Per-run cap on AI checks to keep your bill predictable
  - "Test AI connection" button
- **Form spam cleanup:** trashes spam-flagged entries from Contact Form 7 (via Flamingo), Gravity Forms and Fluent Forms. Extend it with the `nrw_gs_trash_form_spam` filter.
- **Automatic:** daily WP-Cron run plus a one-click "Move spam to Trash now" button.
- **Safe:** nothing is permanently deleted. Everything goes to Trash and can be restored.
- **GitHub updates:** WordPress shows a normal update notice when you publish a new release.

## Installation

1. Download `goodbye-spammy.zip` from the [latest release](../../releases/latest).
2. In WordPress go to **Plugins → Add New → Upload Plugin**, choose the zip and activate.
3. Open **Goodbye Spammy** in the admin sidebar.

## Setting up AI detection

1. Open **Goodbye Spammy → AI spam detection**.
2. Tick **Enable AI** and pick a provider.
3. Paste the API key and choose a model (or leave the default). Cheap, fast models such as `gemini-2.0-flash`, `gpt-4o-mini` or a Claude Haiku model work well.
4. Click **Save all settings**, then **Test AI connection**.

| Provider | Get a key | Example model |
|---|---|---|
| OpenRouter | https://openrouter.ai/keys | `google/gemini-2.0-flash-001` |
| Google Gemini | https://aistudio.google.com/apikey | `gemini-2.0-flash` |
| ChatGPT (OpenAI) | https://platform.openai.com/api-keys | `gpt-4o-mini` |
| Claude (Anthropic) | https://console.anthropic.com | `claude-haiku-5-5` |

Model names change over time. You can type any model ID the provider currently offers.

**Privacy:** with AI enabled, the text of checked comments and form messages (including name, email and URL) is sent to the provider you select. Add this to your privacy policy. If the AI call fails (bad key, quota, network), nothing is trashed.

## Updating from GitHub

The plugin checks the latest **GitHub Release** of the repository set under **Goodbye Spammy → Updates from GitHub** (default `nrwindia/goodbye-spammy`, change it to your own `owner/repo`).

To publish an update:

1. Bump `Version:` in `goodbye-spammy.php` and the `VERSION` constant (for example to `1.0.2`).
2. Commit and push.
3. Create a GitHub release with the tag `v1.0.2`.
4. Optional but recommended: attach a `goodbye-spammy.zip` asset (a zip containing the `goodbye-spammy/` folder). If there is no asset, the plugin falls back to the release source zipball and fixes the folder name automatically.

Sites then see the update in **Dashboard → Updates** and on the Plugins page. Use **Check for updates** in the plugin to refresh immediately. Update checks are cached for 6 hours. Private repositories are not supported.

## Supported form plugins

| Plugin | What gets trashed |
|---|---|
| Contact Form 7 + Flamingo | Messages flagged as spam (and AI-detected spam) |
| Gravity Forms | Entries with the spam status |
| Fluent Forms | Submissions with the spam status |

## Repository structure

```
goodbye-spammy/
├── goodbye-spammy.php   # main plugin file
├── uninstall.php        # removes options on delete
└── README.md
```

## Changelog

### 1.0.1
- Added AI spam detection with OpenRouter, Gemini, ChatGPT and Claude (own API key and model per provider)
- Added optional live AI check for new comments and AI review of Flamingo (CF7) messages
- Added "Test AI connection" tool
- Added GitHub-based plugin updates
- New comments stored as spam by Akismet are now trashed instantly when "Instant trash" is on

### 1.0.0
- Initial release: spam comment cleanup, rule-based scan, form spam cleanup, daily automation

## Support

If this plugin helps you, you can [buy me a coffee](https://buymeacoffee.com/sourabhnrw). Issues and pull requests are welcome.

## License

GPL-2.0-or-later
