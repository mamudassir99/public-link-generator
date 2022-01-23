# public-link-generator

from datetime import date
from typing import Text
import telebot
import time

bot_token = '2101142644:AAG_-h_bO-pzEhqhOVT1efeNHLJwn6F2TK0'

bot = telebot.TeleBot(token=bot_token)

def find_at(msg):
    for text in msg:
        if'@' in text:
            return text

@bot.message_handler(commands=['start'])
def send_welcome(message):
    bot.reply_to(message,'welcome! to this bot')

@bot.message_handler(commands=['help'])
def send_welcome(message):
    bot.reply_to(message,'To use this bot,send it a username')

@bot.message_handler(func=lambda msg: msg.text is not None and '@' in msg.text)
# lamda function finds message  with the'@' sign in them
# in case msg.text doesn't exist, the handler doesn't process it
def at_converter(message):
    text = message.text.split()
    at_text = find_at(text)

def server():
    @server.route('/' + bot_token, methods=['post'])
    def getMessage():
     bot.process_new_updates
    return "!",200

def webhook():
    bot.remove_webhook
    bot.set_webhook(url='publiclinkgenerator.herokuapp.com/' + bot_token)
    return "!",200
