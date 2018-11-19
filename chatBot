import config
import telebot
import time

bot = telebot.TeleBot(token=config.botToken)


def find_at(msg):
    for text in msg:
        if "@" in text:
            return text


@bot.message_handler(commands=["start"])
def sendWelcome(message):
    bot.reply_to(message, "Welcome!")


@bot.message_handler(func=lambda msg: msg.text is not None and "@" in msg.text)
def at_answer(message):
    textChat = message.text.split()
    at_text = find_at(textChat)

    bot.reply_to(message, "https://instagram.com/{}".format(at_text[1:]))


while True:
    try:
        bot.polling()
    except Exception:
        time.sleep(15)
