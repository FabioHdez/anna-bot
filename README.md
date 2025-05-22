# anna-bot

_A cross-server announcement system for Discord._

anna-bot lets you draft an announcement once and broadcast it to every Discord server that **subscribes** to your feed.  
It bundles two parts:

1. **Discord bot** – listens for slash-commands or webhooks and posts the announcement.
2. **Web dashboard** – a small Flask site where you design, preview and schedule messages.

---

## ✨ Features

- **Multi-server publishing** – one click sends the same embed to all linked channels  
- **Slash-command shortcuts** – `/announce`, `/subscribe`, `/unsubscribe`
- **Templated embeds** – headline, body, image and link fields with live preview
- **Scheduled posts** – queue messages for a future UTC timestamp
- **MySQL / MariaDB storage** – SQL dumps included for quick bootstrap (`dumpfile*.sql`)
- **Webhook helper library** – `webhooks.py` wraps rate-limit-safe delivery

---

## 📦 Prerequisites

| Requirement | Version / Notes |
|-------------|-----------------|
| Python      | 3.9 + |
| Discord Bot | Create in the Discord Developer Portal and copy the **token** & **client-id** |
| MySQL / MariaDB | Import the provided `dumpfile04282025.sql` |

---

## 🚀 Quick start

```bash
# 1. Clone
git clone https://github.com/FabioHdez/anna-bot.git
cd anna-bot

# 2. Virtual environment
python3 -m venv .venv
source .venv/bin/activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Configure
cp .env.example .env            # or edit config.json if you prefer
#   DISCORD_TOKEN=...
#   DATABASE_URL=mysql+pymysql://user:pass@localhost/annabot

# 5. Import schema (optional sample data)
mysql -u root -p < dumpfile04282025.sql

# 6. Run the web dashboard
python server.py        # default http://127.0.0.1:5000

# 7. Start the bot
python bot.py
