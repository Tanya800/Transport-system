Система для реорганизации и котроля городского потока гражданского и общественного транспорта
=============
Общая информация
------------------
Основные темы:
1. Карта города с дорогами 
2. Отслеживание частного и общественного транспорта 
3. Умные светофоры
4. Количество пешеходов и пользователей общественным транспортом
5. Составление маршрутов общественного транспорта и определение его манимального количества на линии
6. Система сбора данных

Серверная часть для обработки данных
Тип клиентской части - мобильное приложение, так как данная система предполагает помогать человеку перемешаться по городу, следовательно приложение должно быть карманным.

 Приложение будет иметь следующие разделы:
 
 1. Раздел с возможностью установки постоянного класса пользователя: пешеход, пользователь общественного транспорта, водитель и т. д. Однако, каждый день необходимо будет вносить корректироваки, если класс пользователя изменится. Если корректировок нет, то учитывается постоянный класс. То есть, если человек помечает, что он водитель, но сегодня он решил отказаться от собственного транспорта, то он должен отметить это в системе.
 
 2. Раздел карты города планируется сделать в нескольких режимах в зависимости от класса пользователя(пока выделены следующие):
    
    2.1 Автомобилист:
      
        2.1.1 Отображение светофоров
      
        2.1.2 Отображение загруженности дорог  
      
        2.1.3 Подбор удобного маршрута
      
    2.2 Пешеход:
  
        2.2.1 Отображение светофоров
  
    2.3 Пользователь общественного транспорта:
      
        2.3.1 Отображение маршрутов городского транспорта с возможностью выбора необходимого
       
        2.3.2 Отображение загруженности дорог
       
        2.3.3 Подбор лучшего маршрута с учетом загруженности транспорта
        
   3. Личный кабинет пользователя, который позволит запоминать/вносить постоянные маршруты, высчитывая наилучший
 
 Анализ предметной области 
---------

### 1. Карта города 

Карты – это функциональность, которая реализуется на стороне смартфона. На Android Google Maps стоят уже по умолчанию. Это нативные карты, которые идеально заточены под Android — это позволит пользователям загружать все быстрее, и затратиться меньше времени на интеграцию. C iOS Google Maps также замечательно работают. Документация для работы с картами <https://developers.google.com/maps/documentation>. 
Карта, в данном случае, явлеяется удобным способом представления собранной информации, которая прошла обработку на сервере. То есть, практически весь результат работы системы будет отбражаен на карте. 

### 2. Отслеживание частного и общественного транспорта 


### 3. Умные светофоры

«Умный светофор» – это система динамического управления сигналами светофора, благодаря которой, улучшается  пропускная способность потоков улично — дорожной сети. Прежде всего, повышается безопасность дорожного движения. Другими словами, это светофор, работающий не в обычном, строго определённом режиме, независимо не отчего, а светофор, который переключает сигналы исходя из количества транспортных средств  в  каждом из направлений.

Система «умный светофор» состоит из контроллеров, удаленных  датчиков движения и видеокамер. Именно они, в режиме реального времени отслеживает загруженность перекрестков и  передает данную информацию на центральный сервер управления. Связь с которым осуществляется через радиосигналы или по оптическим линиям связи.

Видеокамера или датчики устанавливаются на определенной высоте и над конкретным участком трассы. Далее, сигнал от нее поступает в модуль обработки видеоинформации. Затем в данном модуле происходит выделение подвижных транспортных средств и определение различных интегральных оценок.

После этого, на основе этих показаний, центральный сервер дает команду контроллерам светофоров включить красный или зеленый свет и на какое время.

Прежде всего, системы видеоконтроля, ориентированные на транспорт, предоставляют данные трех типов:

Во-первых, это информация о трафике для статистической обработки:

общее количество обнаруженных автомобилей;
скорость;
ускорение транспортного потока;
плотность потока;
загруженность полос движения;
классификация автомобилей.
Во-вторых, информация о происшествиях на дороге:

высокая скорость, плотность потока или занятость полос;

наличие заторов или движения по встречной полосе;

остановившиеся или медленно движущиеся автомобили;

наличие на дороге подозрительных предметов.

В-третьих, информация о наличии/отсутствии автомобилей:

наличие приближающихся автомобилей;

наличие автомобилей, остановившихся на перекрестке;

число автомобилей, проехавших через зоны обнаружения;

измерение длины очереди.

### 4. Количество пешеходов и потенциальных пассажиров общественного транспорта

Для составления наиболее гибких и продуктивных маршрутов на дороге для частного, а также для общественного транспорта, потребуется определять количество пешеходов и пользователей общественным транспортом. Следует обратить внимание, для пользователей общественным транспортом и пешеходов следует вести различные подходы к прогнозированию и определению маршрутов. Совершая свои перемещения пешком, пешеход загружает часть дорог, требуя множественных пешеходных переходов и тротуаров. Возникновение большого столпотворения на улицах и дорогах затрудняет проезд транспорту и другим участникам дорожного движения. Получая данные о количестве пешеходов на улице, возможно спроектировать наиболее оптимальные маршруты для передвижения частных, общественных и иных транспортных средств. 

Количество потенциальных пассажиров общественного транспорта дает возможность решения сразу нескольким вопросам городского движения:

- определение наиболее востребованных мест для остановок общественного транспорта,

- организация планов маршрутов общественного транспорта,

- подсчет необходимого количества транспортных средств на одно или нескольких маршрутов для удовлетворения нужд пассажиров,

- возможность пассажирам влиять на востребованность маршрутов и транспорта,

- построение быстрых и легких маршрутов для частных автомобилей или такси по маршрутам, не заполненными общественным транспортом.
 
 
### 5. Составление маршрутов общественного транспорта и определение его минимального количества на линии


### 6. Система сбора данных


