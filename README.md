# test-action

## Telegram Notifications

This repository uses [Telegram Notify](https://github.com/marketplace/actions/telegram-notify) GitHub Action to send notifications to Telegram when changes are pushed to the repository.

### Setup

1. Create a Telegram bot using [@BotFather](https://t.me/botfather) and get the bot token
2. Get your chat ID (you can use [@userinfobot](https://t.me/userinfobot))
3. Add the following secrets to your repository:
   - `TELEGRAM_TOKEN`: Your Telegram bot token
   - `TELEGRAM_TO`: Your chat ID

The action will send formatted notifications with commit details whenever code is pushed to any branch.
