import vk_api # работа с vk
import time # для функции sleep - ожидание
import random # случайные числа
import datetime # дни недели
import requests
import json
from pprint import pprint

polzovateli= ['пользователи','польза']
delimeter='?'#РАЗДЕЛИТЕЛЬ В SETDZ
hello = ['привет','здравствуйте','дратути','здраствуйте','прувет','драсте','привет, бот','приветствую','привеат','здравствуй','дратуйте']
info = ['info']
ktoty = ['кто ты','ты кто','как тебя зовут']
Dz = ['дз','домашк','домашняя работа','скажи дз','какое дз','задали','задавали','по немецкому','по английскому', 'по биологии', 'по истории', 'по русскому', 'по матем']
russ = ['русский','рус']
mat = ['математика','матеша','матёша','математику','матешу','матёшу','матем','математику']
biolog = ['биология','биологичка']
angl = ['англ','англиский']
geo=['геогр','география','гео']
nem=['нем','немецкий','нем яз']
ist=['ист','истор','история']
obzhestvo=['обществознание','общество']
raspisan = ['расписание','какие завтра предметы','какие завтра уроки']
admins = [426651961, #рома
          426392340,#руся
          347304385,  #карина
          486965306, #ксюша
          511246054,  #макс
          369134139 , #ира
          378276990 #артем
          ]
anekdot = ['анекдот','расскажи анекдот','расскажи мне анекдот','скажи мне анекдот']
answ_anekdot = ['Прости, но мои шутки плоские, КАК ЗЕМЛЯ',
                '- В первый раз? - спросил палач.',
                'Начальник вызывает к себе в офис уборщика, чтобы уволить и говорит: Убирайся отсюда!',
                'Здравствуй добрая фея. - Здравствуй мальчик.- Добрая фея, а по чему у тебя в руках топор?- А настроение у меня плохое.',
                'Сообщество плоской земли заявило, что имеет последователей по всему земному шару.',
                'сменку не взял,маслину поймал',
                'Дима не очень любил ездить на велосипеде без рук, но после случая на пилораме другого варианта у него не было.',
                'Звонок в 4 утра : — Алло! А у вас стадо оленей не пробегало? Спокойный ответ: — А ты что отстал?']
znacheniedz = []
dela = ['как дела','как делишки']
chto = ['что ты можешь','что ты умеешь']
pogoda = ['погода','какая погода сегодня','что за погода сегодня','сколько градусов']
eshe = ['что еще ты умеешь','что ещё ты умеешь','что еще ты можешь','что ещё ты можешь','что еще ты умеешь?']
page = ['стр','страниц']
dz_markers=['что','по','что по','че по','чё по','дз','задали','задовали','задавали','задания','задание']
kalkulator = ['вычисли','посчитай','пощитай','сколько']
segodn = ['сегодня','в этот день']
LinkPhoto = 'photo-169581676_'
LinkMatem1 = '456239752'
LinkRuss='456240027'
LinkBiolog='456240186'
LinkAng='456240716'
LinkNem='456240901'
LinkGeo='456240529'
LinkObsh='456241000'
zavtra = ['завтра','завтрашний']
LinkIst='456240329'
LinkIst2='456241112'
dni=['понедельник','пн','вторник','вт','среда','ср','четверг','чт','пятница','пт','суббота','сб','воскресенье','вс']
messeg_list=[]

BUTTON={
  "type": "object",
  "properties": {
    "action": {
      "type": "object",
      "properties": {
        "type": {
          "type": "string",
          "enum": ["text"],
          "description": "Содержит 'text'"
        },
        "payload": {
          "type": "string",
          "description": "JSON строка с payload, до 255 символов"
        },
        "label": {
          "type": "string",
          "description": "Кнопка"
        }
      }
    },
    "color": {
      "type": "string",
      "enum": ["Primary", "Default", "Negative", "Positive"],
      "description": "Цвет кнопки"
    }
  }
}




keyboard={
    "one_time": False,
    "buttons": [
      [{
        "action": {
          "type": "text",
          "payload": "{\"button\": \"1\"}",
          "label": "учебник"
        },
        "color": "primary"
      },
     {
        "action": {
          "type": "text",
          "payload": "{\"button\": \"2\"}",
          "label": "Погода"
        },
        "color": "default"
      }],
      [{
        "action": {
          "type": "text",
          "payload": "{\"button\": \"3\"}",
          "label": "Расписание"
        },
        "color": "default"
      },
     {
        "action": {
          "type": "text",
          "payload": "{\"button\": \"4\"}",
          "label": "Дз"
        },
        "color": "primary"
      }],
    ]
  }

keyboardDZ={
    "one_time": True,
    "buttons": [

      [{
        "action": {
          "type": "text",
          "payload": "{\"button\": \"1\"}",
          "label": "дз на завтра"
        },
        "color": "default"
      }],
      [{
        "action": {
          "type": "text",
          "payload": "{\"button\": \"2\"}",
          "label": "дз на послезавтра"
        },
        "color": "default"
      }],
      [{
        "action": {
          "type": "text",
          "payload": "{\"button\": \"3\"}",
          "label": "Дз на определенный день"
        },
        "color": "default"
      }],
      [{
        "action": {
          "type": "text",
          "payload": "{\"button\": \"3\"}",
          "label": "Дз на определенный день"
        },
        "color": "primary"
      }]

    ]
  }




keyboardDZpredmet={
    "one_time": True,
    "buttons": [
      [{
        "action": {
          "type": "text",
          "payload": "{\"button\": \"1\"}",
          "label": "русск?"
        },
        "color": "default"
      }],
     [{
        "action": {
          "type": "text",
          "payload": "{\"button\": \"2\"}",
          "label": "мат?"
        },
        "color": "default"
      }],
      [{
        "action": {
          "type": "text",
          "payload": "{\"button\": \"3\"}",
          "label": "общ?"
        },
        "color": "default"
      }],
     [{
        "action": {
          "type": "text",
          "payload": "{\"button\": \"4\"}",
          "label": "ист?"
        },
        "color": "default"
      }],
      [{
        "action": {
          "type": "text",
          "payload": "{\"button\": \"5\"}",
          "label": "био?"
        },
        "color": "default"
      }],
      [{
        "action": {
          "type": "text",
          "payload": "{\"button\": \"6\"}",
          "label": "гео?"
        },
        "color": "default"
      }],
      [{
        "action": {
          "type": "text",
          "payload": "{\"button\": \"7\"}",
          "label": "нем?"
        },
        "color": "default"
      }],
     [{
        "action": {
          "type": "text",
          "payload": "{\"button\": \"8\"}",
          "label": "англ?"
        },
        "color": "default"
      }]

    ]
  }




keyboardDZday={
    "one_time": True,
    "buttons": [
      [{
        "action": {
        "type": "text",
        "payload": "{\"button\": \"1\"}",
        "label": "пн?"
        },
        "color": "default"
      },
    {
        "action": {
        "type": "text",
        "payload": "{\"button\": \"2\"}",
        "label": "вт?"
        },
        "color": "primary"
      }],


    [{
        "action": {
        "type": "text",
        "payload": "{\"button\": \"3\"}",
        "label": "ср?"
        },
        "color": "default"
      },
    {
        "action": {
        "type": "text",
        "payload": "{\"button\": \"4\"}",
        "label": "чт?"
        },
        "color": "primary"
      }],
    {
        "action": {
        "type": "text",
        "payload": "{\"button\": \"5\"}",
        "label": "пт?"
        },
        "color": "default"
      }



    ]
  }



dscp={
    'рус':'русский',
    'мат':'математика',
    'анг':'англиский',
    'изо':'изо',
    'тех':'тенология',
    'физ':'физра',
    'общ':'общесвознание',
    'лит':'литература',
    'ист':'история',
    'нем':'немецкий',
    'гео':'география',
    'крм':'крымовединие',
    'муз':'музыка',
    'био':'биология',
    'леж':'лежать'
}

def context_msg(user_id, count=5):
    get_messages = vk.method('messages.getHistory', {'offset':0, "count":200, 'user_id':user_id})
    #last_messages = list(get_messages['items'][i] for i in range(count))
    last_messages=[]
    c = 0
    for item in get_messages['items']:
        if item['user_id'] == item['from_id']:
            last_messages.append(item['body'])
            c+=1
            if c == count:
                return last_messages
    return last_messages
    ### ['body']'user_id':user_id, 'filter': 'all'

def eto_dz_zapros(usr_msg):
    markers=usr_msg.split()
    cnt=0
    for i in markers:

        if i in dz_markers:
            cnt+=1
    return  cnt

def loadschedule():
    f=open('h.rasp','r')
    w=f.read()
    print("Загужаем расписание\n")
    pprint(eval(w))
    r=json.loads(w)
    f.close()
    return r

def users_list():
    emoji_male = [
        '&#128057;', # хомяк
        '&#127770;',
        '&#128110;', # дас мент
        '&#128115;',  #indus
        '&#128114;',   #china
        '&#127877;', #ded moroz
        '&#128373;',   #detektiv
        '&#128130;',   #gvardeec
        '&#128102;'    #malchik

    ]
    emoji_female=['&#128103;', #девочка
                  '&#128117;', # бабушка
                  '&#129318;',
                  '&#127774;',
                  '&#128129;', #женщина информация
                  '&#128581;',   #женщина нет
                  '&#128587;',    #женщина за
                  '&#128120;',   #принцесса
                  '&#128112;',   #невеста
                  '&#129335;',    #женщина пожимает плечами
                  '&#128131;',  #женщина танцует
                  '&#128105;',    #женщина
                  '&#128590;', #женщина обиделась
                  '&#128589;' #женщина хмуриться
                  ]
    emoji_anybody =['&#128064;',
                    '&#127752;']
    imena='На сегоднешний день чатботом пользуются: \n'
    users=[]
    dialogs =vk.method('messages.getConversations', {'offset':0, "count":200, 'filter': 'all'})
    dialogs_count=int(dialogs['count'])
    print(dialogs)

    id_list=[]
    for i in range(0,dialogs_count):
        print(i)
        user_id = dialogs['items'][i]['last_message']["from_id"]
        id_list.append(user_id)


    messages = vk.method('messages.getConversations', {'offset':0, "count":20, 'filter': 'all'})
    #pprint(messages)
    profiles=[]
    for i in range(0,messages['count']):
        profiles.append(messages['items'][i]['conversation']['peer']['id'])


    for profile in profiles:
        userinfo = vk.method('users.get', {'user_id':profile,'fields':'sex','name_case':''})
        username = userinfo[0]['first_name']# [в списке первый элемент][по ключу - имя]
        sex = userinfo[0]['sex']
        userlastname= userinfo[0]['last_name']
        imena += username
        if sex==1:
            imena+=random.choice(emoji_female)
        if sex==2:
            imena+=random.choice(emoji_male)
        users.append(username)
        imena+=", \n"
    return imena

def saveschedule():
    f=open('h.rasp','w')
    r=json.dumps(Rasp)
    f.write(r)
    f.close()

def analyse_str(text):
    #выдает стр по математике
    for i in page: #ищем слово страница
        for j in mat: #ищем слово математика
            if (body.lower().find(i) != -1)and (body.lower().find(j) != -1): #если в одном сообщении есть и одно и другое
                f=False
                for element in body.split(" "):
                    try:
                        Link1 = str (int(LinkMatem1) + int(element) - 1)
                        text=LinkPhoto +Link1
                        f=True
                    except ValueError:
                        print('игнорируем строку, так-как нельзя перевести в интеджер '+element)
                if not (f): #если не нашел страницу
                    vk.method('messages.send', {'peer_id': id, 'message':  "Я не понял какую страницу ты имеешь ввиду. Попробуй написать через пробел например:'математика стр 7'"})

    #выдает стр по русскому

        for j in russ: #ищем слово  русск
            if (body.lower().find(i) != -1)and (body.lower().find(j) != -1): #если в одном сообщении есть и одно и другое
                pagesfound = 0   ############# начинаем считать сколько найдено страниц в сообщении
                for element in body.split(" "): # разделяем сообщение на слова
                    if element.isdigit(): #########################  если слово (элемент строки) состоит из цифр
                                ############################# прежде всего стоит проверить что число не отрицательное, не равно нулю, и не выходит за диапазон учебника
                                ########################### написать код проверки
                        pagesfound += 1
                        Link1 = str (int(LinkRuss) + int(element) - 1)
                        text=LinkPhoto +Link1
                        print('Отправлена страница', int(element),'по русскому языку для пользователя',username, userlastname, sep=" ")
                        ################ после цикла посчитали все числовые значения в сообщении
                        if pagesfound == 0: ############ если в сообщении не было указано ни одной страницы, нужно сообщить об ошибке пользователю
                            text="Я не понял какую страницу ты имеешь ввиду. Попробуй написать через пробел например:'русский стр 7'"
                        elif pagesfound ==1:
                            pass  ################### если указана одна страница, то можно отправить обычный attachment
                        elif pagesfound >= 2:
                            pass ############## если пользователь запросил несколько страниц, то лучше все эти фотографии отправить одним сообщением
                            ################################# для этого нужно сделать цикл - pagesfound раз - в отдельую строку мы добавляем список всех аттачментов,
                            ################################# все тоже самое, как и для одной фотки, НО через запятую без пробелов
                            ################################# а когда до конца прошлись по циклу и строка сформирована, мы отправляем message.send attachment


                            break

    #выдает стр по биологии
             #ищем слово страница
        for j in biolog: #ищем слово математика
            if (body.lower().find(i) != -1)and (body.lower().find(j) != -1): #если в одном сообщении есть и одно и другое
                for element in body.split(" "):
                    try:
                        Link1 = str (int(LinkBiolog) + int(element) - 1)
                        text=LinkPhoto +Link1
                    except ValueError:
                        print('игнорируем строку, так-как нельзя перевести в интеджер '+element)
                    break

    #выдает стр по английскому
                 #ищем слово страница
        for j in angl: #ищем слово математика
                    if (body.lower().find(i) != -1)and (body.lower().find(j) != -1): #если в одном сообщении есть и одно и другое
                        for element in body.split(" "):
                            try:
                                Link1 = str (int(LinkAng) + int(element) - 1)
                                text=LinkPhoto +Link1
                            except ValueError:
                                print('игнорируем строку, так-как нельзя перевести в интеджер '+element)
                            break

    #выдает стр по немецкому

        for j in nem: #ищем слово математика
             if (body.lower().find(i) != -1)and (body.lower().find(j) != -1): #если в одном сообщении есть и одно и другое
                for element in body.split(" "):
                    try:
                        Link1 = str (int(LinkNem) + int(element) - 1)
                        text=LinkPhoto +Link1
                    except ValueError:
                        print('игнорируем строку, так-как нельзя перевести в интеджер '+element)
                    break

    #выдает стр по географии

        for j in geo: #ищем слово математика
            if (body.lower().find(i) != -1)and (body.lower().find(j) != -1): #если в одном сообщении есть и одно и другое
                for element in body.split(" "):
                    try:
                        Link1 = str (int(LinkGeo) + int(element) - 1)
                        text=LinkPhoto +Link1
                    except ValueError:
                        print('игнорируем строку, так-как нельзя перевести в интеджер '+element)
                    break
    #выдает стр по истории

        for j in ist: #ищем слово математика
            if (body.lower().find(i) != -1)and (body.lower().find(j) != -1): #если в одном сообщении есть и одно и другое
                for element in body.split(" "):
                    try:
                        Link1 = str (int(LinkIst) + int(element) - 1)
                        text=LinkPhoto+Link1
                    except ValueError:
                        print('игнорируем строку, так-как нельзя перевести в интеджер '+element)


                    try:
                        if int(element) >200:
                            Link1 = str (int(LinkIst2) + int(element) - 1)
                            text= LinkPhoto +Link1
                    except ValueError:
                        print('игнорируем строку, так-как нельзя перевести в интеджер '+element)

                    break

    #выдает стр по обществу

        for j in obzhestvo: #ищем слово общество
            if (body.lower().find(i) != -1)and (body.lower().find(j) != -1): #если в одном сообщении есть и одно и другое
                for element in body.split(" "):
                    try:
                        Link1 = str (int(LinkObsh) + int(element) - 1)
                        text= LinkPhoto +Link1
                    except ValueError:
                        print('игнорируем строку, так-как нельзя перевести в интеджер '+element)
                    break
    return text

def analyze_dz(text):
    russ_dz = ['русский','рус','русскому']
    mat_dz = ['математика','матеша','матёша','математику','матешу','матёшу','матем','математику', 'математике']
    biolog_dz = ['биология','биологичка']
    lit_dz = ['литре','литературе','литература','литра']
    angl_dz = ['англ','англиский','англискому','ангийскому']
    geo_dz=['геогр','география','гео',"географии"]
    nem_dz=['нем','немецкий','нем яз']
    ist_dz=['ист','истор','история']
    obzhestvo_dz=['обществознание','общество']
    dz_day=-1;
    dt = datetime.datetime.today()
    tt = dt.weekday()
    posle_zavtra=days[(tt+1)%7]
    dz_predmet=''
    dz_subgroup=''

    text_otvet=''

    den_sokr = dict([('пн',0), ('вт',1), ('ср',2), ('чт',3), ('пт',4), ('сб',5), ('вс',6)])
    den_poln = dict([('понедельник',0), ('вторник',1), ('среда',2), ('четверг',3), ('пятница',4), ('суббота',5), ('воскресенье',6)])

    text_list = text.split(" ")#создаеееееееееем массив отдельых слов

    for slovo in text_list: # проходимся по каждому слову из сообщения
        print("Найденно слово", slovo)

        if slovo == "понедельник" or slovo=="пн":
            dz_day=0
        if slovo == "вторник" or slovo=="вт":
            dz_day=1
        if slovo == "среда" or slovo=="ср":
            dz_day=2
        if slovo == "четверг" or slovo=="чт":
            dz_day=3
        if slovo == "пятница" or slovo=="пт":
            dz_day=4
        if slovo == "суббота" or slovo=="сб":
            dz_day=5
        if slovo == "воскресенье" or slovo=="вс":
            dz_day=6
        if slovo== "завтра":
            dz_day= (tt+1)%7
        if slovo== "послезавтра":
            dz_day= (tt+2)%7
        if slovo=="сегодня": #
            dz_day= tt


        if slovo in russ_dz:
            dz_predmet='рус'
        if slovo in mat_dz:
            dz_predmet='мат'
        if slovo in geo_dz:
            dz_predmet='гео'
        if slovo in biolog_dz:
            dz_predmet='био'
        if slovo in ist_dz:
            dz_predmet='ист'
        if slovo in nem_dz:
            dz_predmet='нем'
        if slovo in obzhestvo_dz:
            dz_predmet='общ'
        if slovo in angl_dz:
            dz_predmet='анг'
        if slovo in lit_dz:
            dz_predmet='лит'

    print('определен день ',dz_day)
    print('определен предмет ',dz_predmet)
    #print(Rasp[str(dz_day)]['2'][dz_predmet])
    inf=''
    #сценарий 1 - известен предмет, неизвестен день
    if dz_day==-1 and dz_predmet!='':
        pass
    #сценарий 2 - известен день, неизвестен предмет
    if dz_day!=-1 and dz_predmet=='':
        for predmet_nomer in Rasp[str(dz_day)]:
            for key in Rasp[str(dz_day)][predmet_nomer]:
                s=Rasp[str(dz_day)][predmet_nomer][key]
                if len (s)>1:
                    text_otvet+=dscp[key]+'-'+s+'\n'

    #сценарий 3 - известен предмет, известен день
    if dz_day!=-1 and dz_predmet!='':
        for predmet_nomer in Rasp[str(dz_day)]:
            for key in Rasp[str(dz_day)][predmet_nomer]:
                print(key)
                if key==dz_predmet:
                    s=Rasp[str(dz_day)][predmet_nomer][key]
                    print(s)
                    text_otvet+='задание - '+s+'\n'


    #сценарий 4 - неизвестно ничего
    if dz_day==-1 and dz_predmet=='':
        print(':0')
    if text_otvet=='':
        return 'ничего не найденно &#128584; &#128585; &#128586; \n скорее всего задание не записано '

    return text_otvet

def information():
    dt = datetime.datetime.today() #получит сегодняшнюю дату
    tt = dt.weekday() #день Недели в виде числа

    inf = 'Сегодня '+days[tt]#+'\nЗавтра будет '+ days[(tt+1)%7] #
    inf = inf + '\n Расписание на завтра:' + '('+  days[(tt+1)%7] +')' + '\n' #задать inf "расписание на завра (это не значение ,а обычная надпись)"  + какой завтра день
#    print(Rasp[str((tt+1)%7)]['0'])
    print(Rasp)
    k=str((tt+1)%7)   # ключ - строка от завтрашнего дня
    for nnn in Rasp[k]:    # расписание дня номер k
        print(nnn)
        for key in Rasp[k][nnn]:
            print ('tt = ', tt, '\n key =', key,'\n info= ', inf)
            inf+='\n'+dscp[key]+' - '+Rasp[k][nnn][key]
    return inf

def pogodka():
    res = requests.get("http://api.openweathermap.org/data/2.5/weather?id=693805&appid=7ca53812a6dcac1b30f316f807354abd&lang=RU")
    print("Получаем погоду из OpenWeatherMap:\n",res)
    data = res.json()
    print('Погода: ',data)
    t = round (data['main']['temp'] - 273.15) #берем данные из main temp, переводим в цельсий, округляем
    print(data['weather'][0]['description'])
    description = data['weather'][0]['description'] #1-weather, 2 - [], 3 - description
    wind = data['wind']['speed']
    otvet = ' Сейчас ' + str(t) + ' градусов, ' + description
    if 15<wind<30:
        otvet += ', ветренно, одень шапку! &#127788;'
    elif wind>30:
        otvet+= ', на улице очень сильный ветер! &#127788; &#127788; &#127788;'
    weatherid = data['weather'][0]['id']
    if weatherid==800:
        icontext = ' &#9728; &#65039;' #погода - ясно
    elif weatherid==801 or weatherid==802:
        icontext = '&#127780;' #погода - облачно
    elif weatherid==803:
        icontext = '&#127781;'
    elif weatherid==804:
        icontext = '&#9729; &#65039;'
    elif 200<=weatherid<=232:
        icontext = '&#9928;' #погода - гроза
    elif 300<=weatherid<=321:
        icontext='&#127783;' #погода - моросит дождь
    elif 500<=weatherid<=531:
        icontext='&#127783;  &#9748; &#65039;' #погода - идет дождь
    elif weatherid==600 or weatherid==601:
        icontext='&#127784;' #погода - снег
    elif weatherid==602:
        icontext='&#127784;  &#10052; &#65039;  &#9731;' #погода - много снега
    elif 611<=weatherid<=622:
        icontext='&#10052; &#65039; &#127783;' #погода - снег с дождем
    otvet += icontext #добавить текст иконки к сообщению
    return otvet


###################################### начало основного скрипта

days = ['понедельник','вторник','среда','четверг','пятница','суббота','воскресенье']
sokrdays = {'пн':0,'вт':1,'ср':2,'чт':3,'пт':4,'сб':5,'вс':6}
Rasp={}
Rasp=loadschedule()

ddt = datetime.datetime.today() #получит сегодняшнюю дату
dtw = ddt.weekday() #день Недели в виде числа
#wd = weektostr(dtw) #день недели в виде строки
vk = vk_api.VkApi(token = 'd858971a5a24cc3978cd93813eb1b1ecc874234928ee82b3695a4d28676a12d5d7d01fff12439d09d26b5')
ScriptStartTime = datetime.datetime.now()
ScriptDebugTime = datetime.datetime.now()
ScriptRequestsCount = 0
print('Скрипт запущен ', ScriptStartTime.strftime("%H:%M:%S"))

ROMA = 426651961
print(context_msg(ROMA))



while True:                # в строке ниже нужно сделать try except    --  название ошибки vk_api.exceptions.ApiHttpError: Response code 504

    ScriptRequestsCount+=1
    try:
        messages = vk.method('messages.getConversations', {'offset':0, "count":20, 'filter': 'unread'})       #offset- с какого сообщения начать, count- сколько сообщений , fiter- фильтрует сообщения
    except Exception as e:
        ScriptDebugTime = datetime.datetime.now()
        print('Обнаружена ошибка  ', ScriptDebugTime.strftime("%H:%M:%S"))
        print(e)
        time.sleep(5)

    if messages["count"] >= 1:
        id = messages['items'][0]['last_message']["from_id"] #бот реагитует на последнее сообщение
        body = messages["items"][0]['last_message']['text']  #получить текст последнего сообщения
        userinfo = vk.method('users.get', {'user_id':id,'fields':'','name_case':''}) #узнает информацию о пользователе
        username = userinfo[0]['first_name'] # [в списке первый элемент][по ключу - имя]
        userlastname= userinfo[0]['last_name']
        ScriptDebugTime = datetime.datetime.now()
        print(ScriptDebugTime.strftime("%H:%M:%S"),"Получено сообщение от пользователя", username, userlastname,":\n",body,sep=" ")
        print(eto_dz_zapros(body))
#приветствие
        for i in hello:
            if body.lower().find(i) != -1:
                vk.method('messages.send', {'peer_id': id, 'message': "Привет, "+username })
                break           #lower() - воспринемает буквы любого размера - меняет любые буквы на маленькие

        for i in 'test':
            if body.lower().find(i) !=-1:
                vk.method('messages.send', {'peer_id': id, 'message': context_msg(id) })
                break


        if body.lower().find('клава') !=-1:
            vk.method('messages.send', {'peer_id': id, 'message':'куку','keyboard': json.dumps(keyboard,ensure_ascii=False).encode('utf-8')})

        if body.lower().find('клава2') !=-1:
            vk.method('messages.send', {'peer_id': id, 'message':'куку','keyboard': json.dumps(keyboardDZ,ensure_ascii=False).encode('utf-8')})

        if body.lower().find('клава3') !=-1:
            vk.method('messages.send', {'peer_id': id, 'message':'куку','keyboard': json.dumps(keyboardDZpredmet,ensure_ascii=False).encode('utf-8')})

        if body.lower().find('клава4') !=-1:
            vk.method('messages.send', {'peer_id': id, 'message':'куку','keyboard': json.dumps(keyboardDZday,ensure_ascii=False).encode('utf-8')})






#говорит расписание
        for i in raspisan:
            if body.lower().find(i) != -1:

                vk.method('messages.send', {'peer_id': id, 'message':information()})
                break

#узнать кто пользуется ботом
        for i in polzovateli:
            if body.lower().find(i) != -1:
                vk.method('messages.send', {'peer_id': id, 'message':  users_list()})
                break           #lower() - воспринемает буквы любого размера - меняет любые буквы на маленькие

#setdz - команда постановки расписания пользователй в структуру Rasp(расписание)
        if body.lower().find('setdz')!= -1  and id in admins : #setdz-пн-матем-упр 455

            if body in dni:
                infor=body.lower()[6:].split(delimeter)
                day = str(sokrdays [infor[0]])
                e=-1

                for urok in Rasp[day]:
                    #if dscp[dsc].find(infor[1])!=-1:
                    print(urok)
                    keys= Rasp[day][urok].keys()
                    if infor[1] in keys:
                        e=urok
                if e != -1:
                    Rasp[day][e][infor[1]]=infor[2]
                    saveschedule()
                    vk.method('messages.send', {'peer_id': id, 'message':  "Домашняя работа записана &#10004;"})
                else:
                   vk.method('messages.send', {'peer_id': id, 'message': "такого предмета в этот день нет &#10060;"})
                    #if not body.lower().find (dni)!=-1 :
                    #vk.method('messages.send', {'peer_id': id, 'message': "такого предмета в этот день нет &#10060;"})
            else:
                vk.method('messages.send', {'peer_id': id, 'message': "к сожалению,вы неправильно написали один из компонентов этой команды &#10060;"})

#говорит погоду около школы
        for i in pogoda:
            if body.lower().find(i) != -1:
                vk.method('messages.send', {'peer_id': id, 'message':  "Погодка такая : \n" + pogodka()})
                break


        for i in page:
            if body.lower().find(i) !=-1:
                vk.method('messages.send', {'peer_id': id, 'message': analyse_str(body.lower())})
                break


#если спросили про дз
        for i in Dz:
            if body.lower().find(i) != -1:
                vk.method('messages.send', {'peer_id': id, 'message':  analyze_dz(body.lower())})

                break

#рассказывает о себе
        for i in ktoty:
            if body.lower().find(i) != -1:
                vk.method('messages.send', {'peer_id': id, 'message':  "Я - искуственный интеллект 6-А класса.\n Я могу: \n рассказать анекдот , написать дз на завтра, сказать сколько сейчас градусов и многое другое"})
                break

#говорит что еще может
        for i in eshe:
            if body.lower().find(i) != -1:
                vk.method('messages.send', {'peer_id': id, 'message':  "Еще я могу сказать расписание и дз на завтра, а также показать любую страницу из учебника"})
                break

#рассказывает анекдот
        for i in anekdot:
            if body.lower().find(i) != -1:
                vk.method('messages.send', {'peer_id': id, 'message':  (random.choice(answ_anekdot))})
                break

#рассказывает как у него дела
        for i in dela:
            if body.lower().find(i) != -1: #### find возвращает -1 когда i не найден
                vk.method('messages.send', {'peer_id': id, 'message':  "Дела у меня, как у безчувственной машины "})
                break


        time.sleep(1) # подождать одну секунду

    else: #если сообщений нет
        time.sleep(3)
        continue

ScriptDebugTime = datetime.datetime.now()
print("Скрипт завершен в "  +   ScriptDebugTime)
