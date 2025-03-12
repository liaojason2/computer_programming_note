# Telegram Bot

- [使用Python寫一個Telegram Notify](https://lofinancier.medium.com/%E4%BD%BF%E7%94%A8python%E5%AF%AB%E4%B8%80%E5%80%8Btelegram-notify-8826fc99d842)

## Get Chat ID

```python
import telebot
from dotenv import load_dotenv
import os

# Load environment variables
load_dotenv()

# Initialize bot
bot = telebot.TeleBot(os.getenv('TELEGRAM_BOT_TOKEN'))

# Handler for all messages
@bot.message_handler(func=lambda message: True)
def echo_message(message):
    chat_id = message.chat.id
    print(f"Chat ID: {chat_id}")  # Print to console
    bot.reply_to(message, f"Hello World! Your chat ID is: {chat_id}")

if __name__ == "__main__":
    print("Bot started...")
    bot.infinity_polling()
```

## async/await issue

In Python `telegram` package, `bot.sendMessage` is a async/await function

- [RuntimeWarning: Enable tracemalloc to get the object allocation traceback - Not using async](https://stackoverflow.com/questions/75076069/runtimewarning-enable-tracemalloc-to-get-the-object-allocation-traceback-not)

```python
async def send_message(msg: str) -> None:
    try:
        bot = telegram.Bot(token=TELEGRAM_BOT_TOKEN)
        await bot.send_message(chat_id=TELEGRAM_CHAT_ID, text=msg)
        logging.info("Message Sent!")
    except TelegramError as e:
        logging.error(f"Failed to send message: {e}")
```
