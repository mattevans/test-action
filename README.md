# test-action
testing
11
## Telegram Notifications

This repository uses [Telegram Notify](https://github.com/marketplace/actions/telegram-notify) GitHub Action to send notifications to Telegram for important releases.

### Setup

1. Create a Telegram bot using [@BotFather](https://t.me/botfather) and get the bot token
2. Get your chat ID (you can use [@userinfobot](https://t.me/userinfobot))
3. Add the bot to your group chat:
   - Open the group
   - Click the group name at the top
   - Click "Add members"
   - Search for your bot by username
   - **Important**: After adding the bot, send at least one message in the group, or use the `/start` command
   - Consider making the bot an admin in the group (required in some cases)
4. Add the following secrets to your repository:
   - `TELEGRAM_TOKEN`: Your Telegram bot token
   - `TELEGRAM_TO`: Your chat ID (for group chats, use the format `-1001234567890`)
   - `TELEGRAM_TOPIC_ID`: If using a topic in a group, add the topic ID (e.g., `2`)

### Working with Telegram Topics

If your group has topics enabled:

1. **Topic IDs** are simple numbers:
   - `1` is usually the General topic (default)
   - `2`, `3`, etc. for additional topics you create
   
2. **Finding the correct Topic ID**:
   - Create a new topic in your group
   - Look at the URL when you're in that topic - the last number is often the topic ID
   - Or use the "Test Telegram Topics" workflow to try different IDs
   
3. **Topic testing**:
   - Use the "Test Telegram Topics" workflow to send test messages to different topics
   - This helps confirm which topic ID corresponds to which channel

### Getting the correct Chat ID

If you're using a group chat, make sure to:

1. Add your bot to the group
2. Send a message in the group (important: mention the bot or use /start)
3. Visit `https://api.telegram.org/bot<YOUR_BOT_TOKEN>/getUpdates`
4. Look for a "chat" section with "id" - for groups, this will start with a minus sign (-)
5. If using a topic, note the "message_thread_id" value

### Sending notifications

Notifications are only sent manually:

1. Go to "Actions" tab in the repository
2. Select "Manual Telegram Notification" workflow
3. Click "Run workflow" button
4. Enter the release tag (e.g., `v1.0.0`)
5. Optionally add a custom message
6. **Select a topic ID** (leave empty to use the default from secrets)
7. Click "Run workflow" to send the notification

This allows you to control which releases get announced to your Telegram group.

### Troubleshooting "Not Found" Errors

If you keep seeing "Not Found" errors, try these steps in order:

1. **Verify Bot Setup**:
   - Check that your bot token is correct
   - Make sure the bot is active (send a direct message to it)
   - Try regenerating the token with BotFather if needed

2. **Group Chat Permissions**:
   - Make the bot an admin in the group (this is often required)
   - Ensure the group settings allow bot messages
   - For privacy-focused groups, you may need to use different settings

3. **Chat ID Format Issues**:
   - For group chats, the ID must start with a minus sign (-)
   - For supergroups, the format is usually `-100xxxxxxxxxx`
   - For regular groups, the format is usually `-xxxxxxxxxx`
   - Use the debug-telegram-id.yml workflow to check the exact format

4. **Topic ID Issues**:
   - Topic IDs should be simple numbers (`1`, `2`, etc.)
   - The General topic is usually `1`
   - Custom topics start from `2` onwards
   - Try the "Test Telegram Topics" workflow to find the correct IDs

5. **Test with Personal Chat**:
   - Try sending a message to your personal Telegram ID first
   - If that works, the issue is specific to the group configuration

6. **Create a Fresh Bot**:
   - Sometimes creating a new bot resolves permission issues
   - Set it up from scratch with BotFather

7. **Telegram API Rate Limits**:
   - Telegram has rate limits that might cause temporary failures
   - Wait a few minutes between attempts
