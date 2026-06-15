# GigaJoyce — AI-Powered Discord Bot

Modular, multi-language Discord bot built with discord.py featuring an XP system, RPG, role management, and AI integrations. Uses MongoDB for persistence and supports hot-reloadable modules.

## Features

- **Modular Architecture** — Hot-reloadable command/event modules (Defaults, Owner, XPSystem)
- **XP & Leveling** — Per-guild XP tracking with configurable rewards
- **RPG System** — Game commands and metadata-driven mechanics
- **Multi-Language** — i18n with translation caching (EN/PT)
- **Permissions Framework** — Granular role/user/channel permission namespaces
- **Slash Commands** — Full discord.py hybrid command tree with sync options
- **Settings System** — Extensible per-guild settings with custom types (embed, channel, role, etc.)
- **Emoji Management** — Custom emoji synchronization across guilds
- **AI Integration** — Transformers/torch for NLP features

## Tech Stack

| Component | Library / Tool |
|-----------|----------------|
| Framework | [discord.py](https://github.com/Rapptz/discord.py) 2.5+ |
| Database | MongoDB via [Motor](https://github.com/mongodb/motor) (async) + PyMongo |
| AI/ML | PyTorch, Hugging Face Transformers |
| Scheduler | APScheduler |
| I18n | Custom translation module with JSON locales |
| Hosting | Square Cloud (squarecloud.app) |
| Other | aiohttp, PyYAML, python-Levenshtein, fuzzywuzzy, GitPython |

## Project Structure

```
main.py                          — Bot entry point & initialization
modules/                         — Hot-reloadable feature modules
  Defaults/                      — Core commands & events
  Owner/                         — Owner-only administration
  XPSystem/                      — XP tracking and leaderboards
handlers/                        — Command, event, module & database handlers
classes/                         — Managers (Guild, Member, Permissions, Settings)
  managers/                      — Business logic managers
  structs/                       — Data structures (Command, Guild, Member, etc.)
settings/                        — Extensible setting types (boolean, channel, embed, etc.)
db/                              — MongoDB async ORM
utils/                           — Translator, EmojiManager, views, decorators
shared/                          — Shared translations (en.json, pt.json), types
data/                            — MongoDB data dir, images, emoji defaults
locales/                         — Translation strings
```

## Setup

1. Clone the repo and install dependencies:

```bash
pip install -r requirements.txt
```

2. Copy `.env.example` to `.env` and configure:

```
BOT_TOKEN=your_discord_bot_token
MONGODB_URI=your_mongodb_connection_string
```

3. Run the bot:

```bash
python main.py [--debug]
```

4. Choose slash command sync option at startup (global / guild / test guild).

## Notes

Active development project with AI-powered features on a separate branch. MongoDB required — the bot uses an async ORM with WiredTiger storage engine.
