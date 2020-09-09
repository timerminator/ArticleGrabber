# Mini readability

Программа позволяет по указанному URL извлечь из веб-страницы
текст статьи без "мусорной" информации.

## Как установить

Для запуска скрипта необходим Python3.х версии и библиотеки из файла requirements.txt

Установить зависимости можно командой `pip install -r requirements.txt`

## Использование

Программа запускается из командной строки и имеет два аргумента:
* `url` - обязательный позиционный аргумент. Определяет URL для загрузки статьи.
* `-c --config` - необязательный аргумент. Позволяет задать путь до файла с конфигурацией.
Если параметр не задан, то используются стандартные настройки.

### Конфигурация из файла
Файл конфигурации (по умолчанию `config.ini`) позволяет 
задать некоторые переменные для управления поведением программы:
* `wrap` - ширина строки в итоговом текстовом файле. По умолчанию = 80
* `words_count` - количество слов, которое является достаточным для определения
содержимого блока `<div>` полезным контентом. По умолчанию = 20
* `scip_paragraphs` - количество параграфов(тегов `<p>`), с которого будет начинать определение 
его, как содержащего полезный контент. По умолчанию = 3
* `output_dir` - относительный путь до директории, в которой будут располагаться папки со скачанными статьями.
По умолчанию = `"."` (текущая директория)

### Пример запуска
`python grabber.py https://iz.ru/1058577/2020-09-09/lukashenko-rasskazal-o-neopublikovannoi-chasti-razgovora-frg-i-polshi 
--config config.ini`

При успешном выполнении программы на экране появится сообщение `Upload completed successfully`,
и появится файл `[CUR_DIR]/articles/iz.ru/1058577/2020-09-09/lukashenko-rasskazal-o-neopublikovannoi-chasti-razgovora-frg-i-polsh.txt`
со следующим содержимым:
~~~
Лукашенко рассказал о неопубликованной части разговора ФРГ и Польши

Президент Белоруссии Александр Лукашенко заявил о наличии неопубликованной части
перехваченного спецслужбами республики разговора Берлина с Варшавой об
«отравлении» блогера Алексея Навального, в которой содержатся сенсационные
подробности. Об этом в среду, 9 сентября, рассказал главный редактор
радиостанции «Говорит Москва» Роман Бабаян.

Накануне он принимал участие в большом интервью с белорусским лидером.

«Я дословно не процитирую, но смысл передам сейчас. У нас есть, говорит
[Лукашенко], весь этот разговор, хотите послушать? Мы, естественно, сразу
отреагировали: конечно, хотим, давайте послушаем! На это он говорит: но тогда
попросите руководителя ФСБ России, он даст ее вам послушать, потому что я
передал эту пленку ему», — заявил Бабаян в эфире радиостанции.

По словам Бабаяна, глава республики пообещал более сенсационные подробности во
второй части разговора.

«Но, говорит, я могу вам сказать, что это ерунда, это цветочки. Вы даже не
представляете, какая у нас есть информация и какие ягодки еще впереди», —
отметил он.

4 сентября государственное телевидение Белоруссии
обнародовало[https://iz.ru/1057031/2020-09-04/v-belorussii-obnarodovali-zapisi-
perekhvachennogo-razgovora-frg-i-polshi] запись разговора между Германией и
Польшей по ситуации с Навальным. Согласно этой записи, в начале разговора
представитель Варшавы интересуется, как обстоят дела в Берлине. Его германский
собеседник заявляет, что всё идет по некоему плану и материалы «по Навальному»
скоро передадут канцлеру ФРГ Ангеле Меркель.

Варшавский собеседник поинтересовался, подтверждается ли факт того, что
Навального отравили. Представитель ФРГ говорит, что доказательства «отравления»
не так важны, поскольку идет «война», а в ней хороши всякие методы.

В МИД Польши опровергли[http://iz.ru/1057723/2020-09-07/v-mid-polshi-oprovergli-
telefonnyi-razgovor-mezhdu-varshavoi-i-berlinom] информацию о телефонном
разговоре между Варшавой и Берлином о ситуации Навальным.

Навальный почувствовал себя плохо, когда летел в самолете из Томска в Москву 20
августа. Лайнер экстренно сел в Омске, блогера доставили в больницу скорой
медицинской помощи № 1. Его транспортировали в клинику «Шарите» в Берлине 22
августа.

В немецкой клинике заявили, что
обнаружили[http://iz.ru/1052165/2020-08-24/nemetckie-vrachi-raskryli-rezultaty-
obsledovaniia-navalnogo] у блогера признаки интоксикации веществом из группы
ингибиторов холинэстеразы. Однако омские врачи не
выявили[http://iz.ru/1052236/2020-08-24/v-rossii-zaiavili-ob-otsutstvii-
ngibitorov-kholinesterazy-u-navalnogo] в ходе обследования больного интоксикации
этим веществом.

Кроме того, правительство Германии, опираясь на данные специальной лаборатории
бундесвера, заявило[https://iz.ru/1056085/2020-09-02/moskva-prizvala-berlin-
peredat-dannye-po-navalnomu] 2 сентября, что Навального отравили веществом из
группы «Новичок». Однако доказательств и фактов к этому заявлению приложено не
было.
~~~

## Тестирование

Тесты запускаются с помощью команды `python -m pytest`

Тестирование статей проводилось на следующем списке сайтов:
* "https://lenta.ru/news/2020/09/04/bogat/",
* "https://www.gazeta.ru/politics/2020/09/04_a_13236446.shtml",
* "https://vc.ru/tech/156713-amazon-apple-google-i-drugie-anonsirovali-edinyy-standart-dlya-ustroystv-umnogo-doma-v-2021-godu",
* "https://www.rbc.ru/politics/07/09/2020/5f55dda39a79472a56d81e24?utm_source=yxnews&utm_medium=desktop",
* "https://tass.ru/mezhdunarodnaya-panorama/9388223",
* "https://www.spb.kp.ru/daily/217178.5/4282326/",
* "https://meduza.io/news/2020/09/07/kurs-evro-prevysil-90-rubley-vpervye-s-fevralya-2016-goda",
* "https://www.kommersant.ru/doc/4482578",
* "https://rg.ru/2020/09/07/bmw-posmeialas-nad-novym-mercedes-s-class-no-sdelala-eto-s-uvazheniem.html",
* "https://news.rambler.ru/community/44791552-urnu-nadenu-na-bashku-darmoedy-i-nischebrody-uchitelnitsa-v-rossiyskoy-shkole-otchitala-uchenikov-za-bardak-v-klasse/",

Результаты тестирования можно увидеть в папке `/tests/articles/...`

## Описание алгоритма

Поиск информативного текста на сайте в первую очередь проводился поиском тегов `<p>`.

Как правило, новостные сайты располагают тексты статей именно в таких тегах. Обычно информативные теги `<p>`,
содержащие статью располагаются в пределах одного-двух родительских элементов 
и алгоритм ограничивает поиск текста в пределах этих родительских элементов. Для избежания справочной информации,
котора в верхней части сайта тоже может находиться в тегах `<p>` программа позволяет настроить количество тегов, которые
пропускаются перед тем, как алгоритм выберет тег, в котором наверняка уже есть текст статьи.

Если алгоритм не может найти тегов параграфов, то дальше поиск проводится напрямую в тегах `<div>`.
Теги `<div>` фильтруются так, чтобы остались только такие, которые не содержат других `<div>` как дочерних элементов,
либо те блоки, которые содержат внутри объекты `NavigableString`, то есть текстовые строки.
Для избежания коротких блоков, как полезный контент принимаются блоки, содержащие не меньше 20 слов. Данный параметр 
можно настраивать в файле конфиругации.

После того, как проведён поиск одним из двух методов, 
отформатировнный текст сохраняется в файл и записывается в соотествующую директорию.

## Направления дальнейшего улучшения программы

При дальнейшем развитии программы необходимо улучшать алгоритм поиска информативного текста на сайтах с различной 
степенью неадекватности вёрстки.

Добавить возможность сильнее персонализировать алгоритм к каждому сайту в отдельности, например позволяя задать имена 
или маски имён для css-классов искомых тегов.

Также можно добавить предварительную очистку от тегов, в которых точно не будет искомой информацией 
(рекламы, скриптов, баннеров, комментариев и прочего).

Кроме вывода в текстовый файл, можно добавить возмонжость экспорта в другие форматы, например pdf