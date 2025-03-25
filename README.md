# test-action
testing
11
## Telegram Notifications

This repository uses [Telegram Notify](https://github.com/marketplace/actions/telegram-notify) GitHub Action to send notifications to Telegram for important releases.

### Setup

1. Create a Telegram bot using [@BotFather](https://t.me/botfather) and get the bot token
2. Get your chat ID (you can use [@userinfobot](https://t.me/userinfobot))
3. Add the bot to your group chat
4. Add the following secrets to your repository:
   - `TELEGRAM_TOKEN`: Your Telegram bot token
   - `TELEGRAM_TO`: Your chat ID (for group chats, use the format `-1001234567890`)
   - `TELEGRAM_TOPIC_ID`: If using a topic in a group, add the topic ID (e.g., `2`)

### Sending notifications

Notifications are only sent manually:

1. Go to "Actions" tab in the repository
2. Select "Manual Telegram Notification" workflow
3. Click "Run workflow" button
4. Enter the release tag (e.g., `v1.0.0`)
5. Optionally add a custom message
6. Click "Run workflow" to send the notification

This allows you to control which releases get announced to your Telegram group.
