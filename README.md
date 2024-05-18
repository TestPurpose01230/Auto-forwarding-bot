# Auto-forwarding-bot
pip install telethon
from telethon import TelegramClient, events

# Define your API ID and hash, which you can get from my.telegram.org
api_id = 'YOUR_API_ID'
api_hash = 'YOUR_API_HASH'

# Define your phone number
phone = 'YOUR_PHONE_NUMBER'

# Define the source and target channel IDs
source_channel = 'SOURCE_CHANNEL_USERNAME_OR_ID'
target_channel = 'TARGET_CHANNEL_ID'  # Use negative sign for channel IDs

# Create the client and connect
client = TelegramClient('session_name', api_id, api_hash)

@client.on(events.NewMessage(chats=source_channel))
async def handler(event):
    # Forward the message to the target channel
    await client.forward_messages(target_channel, event.message)

# Start the client
client.start(phone)
client.run_until_disconnected()
python forward_telethon.py
