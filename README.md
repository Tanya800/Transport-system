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

ГЛОНАСС – это российская разработка, которая обеспечивает точное позиционирование объекта в пространстве с минимальной погрешностью. Для определения координат используется специальное оборудование, которое при поддержке наземной инфраструктуры связывается с сетью спутников, выведенных на околоземную орбиту.
Принцип работы системы:

- На объект, координаты которого необходимо определить, устанавливается приемно-передающее устройство – терминал.
- Для позиционирования терминал подает запрос на спутники. Чем больше спутников ответят на запрос (в идеале – не менее 4), тем точнее будут определены координаты.
- Ответный сигнал поступает в терминал, программный комплекс которого анализирует время задержки для разных спутников. На основе анализа ответной информации определяются координаты объекта, на котором установлено приемное оборудование.

При постоянной работе терминала (т.е. регулярной отправке запросов и анализе ответов) система ГЛОНАСС может определять не только положение, но и скорость движения объекта. При движении точность позиционирования снижается, но все равно остается достаточной для того, чтобы навигационное оборудования могло выполнить привязку координат объекта к электронной карте местности и построить маршрут.

Основная задача – координация работы транспортного департамента и отслеживание движения автомобилей, перевозящих пассажиров или грузы, в режиме реального времени. Координаты каждой машины определяются по спутнику с установленным интервалом и накладываются на карту, потому диспетчер или руководитель департамента получает максимально объективную и оперативную информацию.

Общественный транспорт необходимо обеспечить данным оборудованием для четкого функционирования системы. 
Частный трансорт можно отслеживатьчерез мобильные устройства водителей.
Как можно отследить телефон? Достаточно просто, ведь 92% телефонов подключены либо к GPS, либо к сотовым операторам, либо к мобильному интернету, либо к точкам раздачи Wi-Fi. И поэтому проследить, где находится человек через телефон, не составит никакой проблемы.

В разработываемом приложении можно разработать подсистему следующего типа для решения поставленной задачи.

Программы-трекеры. Это узкоспециализированные программы, которые могут определять координаты, предоставлять бесплатный чат и запись окружения. Устанавливаются быстро, не скрываются, т.е. человек будет знать об установленной программе. В подавляющем своем большинстве отвечают на вопрос о том, как проследить где находится телефон ребенка.

Также могут быть использованы в качестве отслеживания местоположения людей в походах или на экскурсиях. Все подключенные к данной программе телефоны будут высвечиваться на одной карте и будет общий групповой чат.

### 3. Умные светофоры

«Умный светофор» – это система динамического управления сигналами светофора, благодаря которой, улучшается  пропускная способность потоков улично — дорожной сети. Прежде всего, повышается безопасность дорожного движения. Другими словами, это светофор, работающий не в обычном, строго определённом режиме, независимо не отчего, а светофор, который переключает сигналы исходя из количества транспортных средств  в  каждом из направлений.
Система «умный светофор» состоит из контроллеров, удаленных  датчиков движения и видеокамер. Именно они, в режиме реального времени отслеживает загруженность перекрестков и  передает данную информацию на центральный сервер управления. Связь с которым осуществляется через радиосигналы или по оптическим линиям связи.
Видеокамера или датчики устанавливаются на определенной высоте и над конкретным участком трассы. Далее, сигнал от нее поступает в модуль обработки видеоинформации. Затем в данном модуле происходит выделение подвижных транспортных средств и определение различных интегральных оценок.
После этого, на основе этих показаний, центральный сервер дает команду контроллерам светофоров включить красный или зеленый свет и на какое время.
Прежде всего, системы видеоконтроля, ориентированные на транспорт, предоставляют данные трех типов:

Во-первых, это информация о трафике для статистической обработки:

- общее количество обнаруженных автомобилей;
- скорость;
- ускорение транспортного потока;
- плотность потока;
- загруженность полос движения;
- классификация автомобилей.

Во-вторых, информация о происшествиях на дороге:

- высокая скорость, плотность потока или занятость полос;

- наличие заторов или движения по встречной полосе;

- остановившиеся или медленно движущиеся автомобили;

- наличие на дороге подозрительных предметов.

В-третьих, информация о наличии/отсутствии автомобилей:

- наличие приближающихся автомобилей;

- наличие автомобилей, остановившихся на перекрестке;

- число автомобилей, проехавших через зоны обнаружения;

- измерение длины очереди.

### 4. Количество пешеходов и потенциальных пассажиров общественного транспорта

Для составления наиболее гибких и продуктивных маршрутов на дороге для частного, а также для общественного транспорта, потребуется определять количество пешеходов и пользователей общественным транспортом. Следует обратить внимание, для пользователей общественным транспортом и пешеходов следует вести различные подходы к прогнозированию и определению маршрутов. Совершая свои перемещения пешком, пешеход загружает часть дорог, требуя множественных пешеходных переходов и тротуаров. Возникновение большого столпотворения на улицах и дорогах затрудняет проезд транспорту и другим участникам дорожного движения. Получая данные о количестве пешеходов на улице, возможно спроектировать наиболее оптимальные маршруты для передвижения частных, общественных и иных транспортных средств. 

Количество потенциальных пассажиров общественного транспорта дает возможность решения сразу нескольким вопросам городского движения:

- определение наиболее востребованных мест для остановок общественного транспорта,

- организация планов маршрутов общественного транспорта,

- подсчет необходимого количества транспортных средств на одно или нескольких маршрутов для удовлетворения нужд пассажиров,

- возможность пассажирам влиять на востребованность маршрутов и транспорта,

- построение быстрых и легких маршрутов для частных автомобилей или такси по маршрутам, не заполненными общественным транспортом.


### 5. Составление маршрутов общественного транспорта и определение его минимального количества на линии

Для наиболее удачного распределения общественного транспорта в течении длительного количества времени на остановках общественного транспорта будет собираться статистика о количестве людей, которые перемещаются по городу на общественном транспорте, по каким маршрутам они перемещаются, и в какие промежутки времени.
Таким образом, чем больше времени пройдет от начала сбора статистики, тем более прогнозируемые будут данные о количестве пассажиров на конкретный транспорт.
Таким образом получится максимально оптимизировать количество общественного транспорта на дорогах и избежать его чрезмерное количество и недостаток, для оптимального перемещения людей по городу.

### 6. Система сбора данных

Данные будут собираться в основном при помощь камер видеонаблюдения, установленных на дорогах и остановках общественного транспорта.
В дальнейшем данные будут обрабатываться как в формате реального времени, так и собираться в полноценную статистику, которая в дальнейшем будет оптимизировать движение транспорта и регулировку светофоров. 

Возможности бизнеса
------------------------
Создание данной системы будет включать в себя основные существующие системы навигации или системы, связанные с работой транспорта, однако основной особенностью является наличие всех систем в одном месте и непосредственное регулирование ой или иной структуры в различных ситуациях. Главным дополнением будет система, по работе с общественным транспортом. В итоге разрабатываемый проект будет решать проблемы с загруженностью дорог, как со стороны водителей, так и пешеходов и организации работы общественного транспорта начиная от создания эффективных маршрутов, заканчивая определением количества необходимых машин на линии.

Бизнес-цели
--------------------
1) Автоматизация создания эффективной системы работы общественного транспорта
2) Улучшение предоставления информации и объединение существующих информационных систем и(или) их усовершенствование для автомобилистов и пешеходов. 

Критерии успеха
---------------
Модель бизнес-целей для транспортной системы

Положение о концепции проекта
---------------
Для пешеходов, автомобилистов и пользователей общественным транспортом, которым необходимо перемещаться по городу с минимальными затратами по времени.
Данная "Единая транспортная система города" является информационной системой, которая позволяет людям выбирать самый оптимальный маршрут для передвижения по городу. 
В отличие от существующих систем, данная система будет объединять наилучшие функциональные возможности различных приложений, и учитывать все данные, по результатам которых будет составляться общая схема загруженности дорог в зависимости от гражданского, общественного транспорта и пешеходов.

Бизнес-риски
------------
1) Появление новых видов транспорта и способов передвижения 
Однако, смена будет происходить постепенно, следовательно, возможно дорабатывать приложение дополняя его соответвующими подсистемами. 

Предложения и зависимости
------------
Предполагается, что 98% от чисала жителей города будут скачивать данное приложение


Рамки и ограничения проекта 
=========================

Объем первоначально запланированной версии
--------------
Создание всех функциональных возможностей описанных в пункте 2.1

Объем последующих версий
---------------


