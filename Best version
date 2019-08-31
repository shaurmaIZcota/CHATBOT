import requests
import vk_api
import datetime
import json

from vk_api.longpoll import VkLongPoll, VkEventType
subjects= ['русский','английский','немецкий','физкультура','физика','информатика','история','алгебра','геометрия','литература','обществознание','технология','изо','биология']

MODE_DEFAULT = 0
MODE_REGISTR = 1
MODE_BOLTOVN = 2
MODE_DZ = 3
MODE_GAME = 4
user_mods= {}



def get_keyboard(keyboard_type):
    keyboard0 = {
        "one_time": False,
        "buttons": [
            [{
                    "action": {
                        "type": "text",
                        "payload": "{\"button\": \"1\"}",
                        "label": "негативная клавиатура"
                    },
                    "color": "negative"
                },
                {
                    "action": {
                        "type": "text",
                        "payload": "{\"button\": \"2\"}",
                        "label": "позитивная клавиатура"
                    },
                    "color": "positive"
                },
                {
                    "action": {
                        "type": "text",
                        "payload": "{\"button\": \"2\"}",
                        "label": "расписание на затра"
                    },
                    "color": "primary"
                }
            ]
        ]
    }
    keyboard_ne = {
        "one_time": False,
        "buttons": [
            [{
                    "action": {
                        "type": "text",
                        "payload": "{\"button\": \"1\"}",
                        "label": "Negative"
                    },
                    "color": "ах ты тварь, чатбот"
                },
                {
                    "action": {
                        "type": "text",
                        "payload": "{\"button\": \"2\"}",
                        "label": "извини"
                    },
                    "color": "positive"
                },
                {
                    "action": {
                        "type": "text",
                        "payload": "{\"button\": \"2\"}",
                        "label": "расписание на завтра"
                    },
                    "color": "primary"
                },
                {
                    "action": {
                        "type": "text",
                        "payload": "{\"button\": \"2\"}",
                        "label": "расписание на сегодняS"
                    },
                    "color": "secondary"
                }
            ]
        ]
    }
    keyboard_po = {
        "one_time": False,
        "buttons": [
            [{
                    "action": {
                        "type": "text",
                        "payload": "{\"button\": \"1\"}",
                        "label": "ах ты тварь, чатбот"
                    },
                    "color": "negative"
                },
                {
                    "action": {
                        "type": "",
                        "payload": "{\"button\": \"2\"}",
                        "label": "извини"
                    },
                    "color": "positive"
                },
                {
                    "action": {
                        "type": "text",
                        "payload": "{\"button\": \"2\"}",
                        "label": "расписание на завтра"
                    },
                    "color": "primary"
                },
                {
                    "action": {
                        "type": "text",
                        "payload": "{\"button\": \"2\"}",
                        "label": "расписание на сегодня"
                    },
                    "color": "secondary"
                }
            ]
        ]
    }


    if keyboard_type == 'негатив':
        keyboard = keyboard_ne
    if keyboard_type == 'позитив':
        keyboard = keyboard_po
    if keyboard_type == 'норма':
        keyboard = keyboard0



    keyboard = json.dumps(keyboard, ensure_ascii=False).encode('utf-8')
    keyboard = str(keyboard.decode('utf-8'))
    return keyboard


def schedule(day, klass='7а'):
    schedule = {'7а':[ ['технология',
         'алгебра',
         'история',
         'русский',
         'английский',
         'английский',
         'литература'],
                        ['геометрия',
                         'физ-ра',
                         'русский',
                         'немецкий',
                         'история',
                         'изо',
                         'лит-ра'],
                        ['физика',
                         'физика',
                         'обществознание',
                         'алгебра',
                         'английский',
                         'английский',
                         'физ-ра'],
                        ['алгебра',
                         'русский',
                         'литература',
                         'немецкий',
                         'технология',
                         'музыка'],
                        ['физ-ра',
                         'биология',
                         'геометрия',
                         'русский',
                         'география',
                         'география',
                         'английский']],
                 '7б': []
                 }
    d_to_w = ['понедельник','вторник','среда','четверг','пятница','суббота']
    w_to_d = {'понедельник' : 0,'вторник' : 1,'среда' : 2,'четверг' : 3,'пятница' : 4}

    sc = schedule[klass][day]
    result = ''

    for i,v  in enumerate(sc) :
        result += str(i+1) + '. ' + v + '\n'

    return result


def get_intent(text):
    # определение учебников
    for subject in subjects:
        if text.find(subject) !=-1:
            return 'учебник'
    # определение погоды
    weather_keywords = ['погода', 'температура', 'осадки']
    for weather_keyword in weather_keywords:
        if text.find(weather_keyword) !=-1:
            return 'погода'
    # регистрация
    regs = ['регистрация', 'регестрация']
    for reg in regs:
        if text.find(reg) !=-1:
            return 'регистрация'
    # расписание
    rasps = ['расписание','rasp']
    for rasp in rasps:
        if text.find(rasp) !=-1:
            return 'расписание'


def get_page(subject, page):
    first_page = {'алгебра' : 457241716,
                  'история' : 457241286}
    if subject in first_page:
        return 'photo-169581676_' + str(first_page[subject] + page - 1)
    else:
        return ''

def get_schedule_day(text):
    weekday = ['понедельник','вторник','среда','четверг','пятница']

    for word in text.lower().split(' '):
        if word.find("сегодня") !=-1:
            return datetime.date.today().isoweekday()
        if word.find("завтра") !=-1:
            return datetime.date.today().isoweekday() % 7
        if word in weekday:
            w_to_d = {'понедельник' : 0,'вторник' : 1,'среда' : 2,'четверг' : 3,'пятница' : 4}
            return w_to_d[word]


def analyze_page(msg):
    words = msg.lower().strip().split(" ")
    subject = ""
    page = 0
    for word in words:
       if word.isnumeric():

           page = int(word)
       else:
           if word in subjects:
               subject = word
    return subject, page


if __name__ == '__main__':
    vk_session = vk_api.VkApi(token='d858971a5a24cc3978cd93813eb1b1ecc874234928ee82b3695a4d28676a12d5d7d01fff12439d09d26b5')
    longpoll = VkLongPoll(vk_session)
    vk = vk_session.get_api()
    for event in longpoll.listen():
        if event.type == VkEventType.MESSAGE_NEW and event.to_me and event.text:
       #Слушаем longpoll, если пришло сообщение то:
            intent = get_intent(event.text.lower())
            print('Намерение пользователя : ', intent)
            if intent == 'учебник':
                subject, page = analyze_page(event.text.lower())
                vk.messages.send(user_id = event.user_id,
                                 message = subject + ' ' + str(page),
                                 attachment = get_page(subject, page),
                                 keyboard = get_keyboard('норма')
                                 )

            if intent == 'регистрация':
                vk.messages.send(user_id = event.user_id,
                                 message = 'Введите свой класс')
                print(event.user_id)

            if intent == 'погода':
                vk.messages.send(user_id = event.user_id,
                                 message = 'тест клавиатуры',
                                 keyboard = get_keyboard('негатив'))

            if intent == 'расписание':
                print(schedule(get_schedule_day(event.text)))

                vk.messages.send(user_id = event.user_id,
                                 message = schedule(get_schedule_day(event.text)))
                print(event.user_id)


            # if event.text == 'Первый вариант фразы' or event.text == 'Второй вариант фразы': #Если написали заданную фразу
            #     if event.from_user: #Если написали в ЛС
            #         vk.messages.send( #Отправляем сообщение vk.messages.send(user_id = id,message = text,attachment = attachment)
            #             user_id=event.user_id,
            #             message='Ваш текст'
            # )
            #     elif event.from_chat: #Если написали в Беседе
            #         vk.messages.send( #Отправляем собщение
            #             chat_id=event.chat_id,
            #             message='Ваш текст'
            # )
