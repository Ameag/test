# test
import config
import telebot
from telebot import types
import random


bot = telebot.TeleBot('5199225069:AAFKbDLtciaJRm65xD-f0_iSpdsZ_k8cdBY')
#кнопки начального меню
markup = types.ReplyKeyboardMarkup(resize_keyboard=True)
itembtn1 = types.KeyboardButton("Опросник")
itembtn2 = types.KeyboardButton("Обучение")
itembtn3 = types.KeyboardButton("Блиц")
itembtn4 = types.KeyboardButton("Я еще не придумал")

markup.add(itembtn1,itembtn2,itembtn3,itembtn4)


#начало, меню и помощь
@bot.message_handler(commands=['start'])
def send_welcome(message):
   bot.reply_to(message, "Здраствуйте, я бот, который немного поможет вам выучить историю,"
                  )
   bot.send_message(message.chat.id,"Что бы со мной контактировать лучше использейте приведенную ниже клавиатуру",
               reply_markup=markup)

@bot.message_handler(commands=['menu'])
def send_welcome(message):
   bot.send_message(message.chat.id,"Выбирай",
               reply_markup=markup)

@bot.message_handler(commands=['help'])
def send_welcome(message):
   bot.send_message(message.chat.id,"Список команд\n"
                                    "/start:запускает бота\n"
                                    "/menu:возвращает в начальное меню\n"
                                    "/help:список команд\n ")




#ответ на кнопкb
@bot.message_handler(content_types=['text'])
def echo_all(message):
   if message.text == 'Опросник':
       #инлайн кнопки опросника
      reply_opr = types.ReplyKeyboardMarkup(resize_keyboard=True)
      reply_buton_opr1 = types.KeyboardButton("Хорошо, погнали")
      reply_buton_opr2 = types.KeyboardButton("Вернуться назад")

      reply_opr.add(reply_buton_opr1,reply_buton_opr2)

      bot.send_message(message.chat.id, "Все легко и просто, я задаю вопрос, ты отвечаешь."
                                        "Попасться может все что угодно, от карт до дат",
                       reply_markup=reply_opr)
    # рандомный выбор вопроса
   quastion_list = ['1 вопрос', '2 вопрос', '3 вопрос']
   a = random.choice(quastion_list)



    #1вопрос
   if a =="1 вопрос":
        reply1 = types.ReplyKeyboardMarkup(resize_keyboard=True)# кнопки 1 вопроса
        reply_buton1 = types.KeyboardButton("1 вариант")
        reply_buton1_2 = types.KeyboardButton("2 вариант")
        reply1.add(reply_buton1, reply_buton1_2)
        bot.send_message(message.chat.id, "1 вопрос", reply_markup=reply1)
   if message.text =="1 вариант":
        bot.send_message(message.chat.id,"правильно")#1 ответ

   elif message.text == "2 вариант":
        bot.send_message(message.chat.id,"неверно")# 2 ответ

    # 2 вопрос
   if a =="2 вопрос":
        reply2 = types.ReplyKeyboardMarkup(resize_keyboard=True)# кнопки 2 вопроса
        reply_buton2 = types.KeyboardButton("1 вариант(2)")
        reply_buton2_2 = types.KeyboardButton("2 вариант(2)")
        reply2.add(reply_buton2, reply_buton2_2)
        bot.send_message(message.chat.id, "2 вопрос",
                        reply_markup=reply2)
   if message.text =="1 вариант(2)":
        bot.send_message(message.chat.id,"правильно(2)")

   elif message.text == "2 вариант(2)":
        bot.send_message(message.chat.id,"неверно(2)")


       #3 вопрос
   if a =="3 вопрос":
        reply3 = types.ReplyKeyboardMarkup(resize_keyboard=True)#кнопки 3 вопроса
        reply_buton3 = types.KeyboardButton("1 вариант(3)")
        reply_buton3_2 = types.KeyboardButton("2 вариант(3)")
        reply3.add(reply_buton3, reply_buton3_2)
        bot.send_message(message.chat.id, "3 вопрос",
                        reply_markup=reply3)
   if message.text =="1 вариант(3)":
        bot.send_message(message.chat.id,"правильно(3)")

   elif message.text == "2 вариант(3)":
        bot.send_message(message.chat.id,"неверно(3)")





   # ответ на кнопку обучения
   if message.text == 'Обучение':
       #инлайн кнопки обучения
      reply_oby = types.ReplyKeyboardMarkup(resize_keyboard=True)
      reply_buton_oby1 = types.KeyboardButton("Понял")
      reply_buton_oby2 = types.KeyboardButton("Вернуться назад")

      reply_oby.add(reply_buton_oby1,reply_buton_oby2)

      bot.send_message(message.chat.id, "Тут будут разные исторические факты, посторайся запомнить",
                       reply_markup=reply_oby)
    # рандомный выбор
   quastion_list = ['1 факт', '2 факт', '3 факт']
   b = random.choice(quastion_list)

   # 1факт
   if b == "1 факт":
       reply_oby1 = types.ReplyKeyboardMarkup(resize_keyboard=True)  # кнопки 1 факта
       reply_oby_buton1 = types.KeyboardButton("Далее")
       reply_oby1.add(reply_oby_buton1)
       bot.send_message(message.chat.id, "1 факт",
                        reply_markup=reply_oby1)
   if message.text == "Далее":
       bot.send_message(message.chat.id, "Листаю дальше")  # 1 ответ


   # 2 факт
   if b == "2 факт":
       reply_oby2 = types.ReplyKeyboardMarkup(resize_keyboard=True)  # кнопки 2 факта
       reply_oby_buton2 = types.KeyboardButton("Далее")

       reply_oby2.add(reply_oby_buton2,)
       bot.send_message(message.chat.id, "2 факт",
                        reply_markup=reply_oby2)


       # 3 факт
   if b == "3 факт":
       reply_oby3 = types.ReplyKeyboardMarkup(resize_keyboard=True)  # кнопки 3 факт
       reply_oby_buton3 = types.KeyboardButton("Далее")

       reply_oby3.add(reply_oby_buton3, )
       bot.send_message(message.chat.id, "3 факт",
                        reply_markup=reply_oby3)


bot.polling()
