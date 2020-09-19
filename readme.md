# Популярные ошибки и как их избегать

## 0. Не сохранили изменения/не обновили страницу

Редакторы кода показывают, что файл не сохранен кружком на вкладке. Можно включить авто сохранение (но к нему привыкаешь, а в другой среде оно может быть выключено).

Всегда обновляйте страницу. Иногда нужно обновить минуя кэш браузера (ctrl+f5 или ctrl+r). Есть расширения, которые будут обновлять сами (live server).

## Опечатки/ошибки
### 1. Опечатка в именах файлов, папок
### 2. Несоответствие расширений

Расширения файлов должны быть написаны в путях точно также как в имени файла. Например jpg и jpeg могут считаться разными именами.

### 3. Регистр имен и расширений

Копируйте все имена, а не переписывайте.

Если что-то работает у вас на ПК не означает, что это будет работать у других.

### 4. Пробелы и кириллица

Не используйте в названиях пробелы и кириллицы. На реальном сервере могут быть проблемы.

### 5. Кириллица вместо латиницы

Бывает, что случайно пишешь букву в слове на кириллице. Например русскую "с" вместо английской "c". Такое бывает сложно обнаружить. Тут опять же поможет копирование. Если опечатка в атрибуте, то косвенно подскажет валидатор (про это дальше).

### 6. Неверный относительный путь 

Нельзя использовать локальные пути в вебе. Как и с регистром имен, если что-то работает у вас на ПК не означает, что это будет работать у других. 

Изучите, как работают относительные пути. Убедитесь, что в них нет ошибки. Чтобы выйти из папки на уровень наверх нужно использовать "../". Чтобы зайти в папку на том же уровне, нужно начать с ее названия без всяких символов.

### 7. Каша в файловой структуре. 

Создайте у себя на пк отдельные папки для каждого проекта. Не кладите лишние файлы внутрь (макеты, другие проекты, заметки). Все типы ресурсов держите отдельно (картинки в папке img, стили в папке css, шрифты в папке fonts и т.д.). Главная страница всегда должна называться index.html и лежать в корневой папке. Убедитесь, что нет файлов с двумя расширениями или без расширений (если вы вообще не видите расширений их отображение нужно включить в ОС или в вашем файловом менеджере).

#### 7.1 Бэкапы 

Делайте бэкапы. Существуют разные инструменты для этого. Банальное копирование папки > облачные бэкапы > системы контроля версий.

#### 7.2 html и css в отдельных файлах

Хотя есть разные способы подключить css, в том числе внутри html документа, обычно лучше всего это делать отдельным css файлом. Нельзя просто так смешивать код разных языков в одном файле. Если вам нужно это сделать, то необходимо верно подключить css через инлайн стиль в атрибуте или через общий в head. 

### 8. Ошибки валидации и устаревшая информация

Всегда проверяйте код на ошибки валидации через [валидатор](https://validator.w3.org/nu/). 

Ошибки вложенности ([как узнать это по спекам](https://youtu.be/7w9K34oL_LE) и [онлайн инструмент](https://caninclude.glitch.me/)). 

Неверное написание элементов/атрибутов.

Незакрытые элементы. Принцип: если у элемент есть закрывающий тег всегда ставьте его.

#### 8.1 Символы, которые нельзя использовать в коде

В коде не должно быть типографских кавычек. Только обычные (как правило двойные в html и одинарные в css). Символы, которые могут что-то означать в коде нужно заменять на html спецсимволы.

#### 8.2 Устаревшая информация

Часто источник ошибок - устаревшая информация в интернете (посмотрите лекцию про Поиск информации). Есть множество элементов, атрибутов, которых больше не существует в современных спецификациях. Их нельзя использовать. 

### 9. Ошибки в CSS 

Лишние пробелы. Несуществующее свойство, значение или единица измерения. Не хватает точки с запятой, что ломает следующее правило. Смотрите на подсветку кода в редакторе, она подскажет наличие проблемы. Валидация. Девтулзы (предупреждения и перечеркивания). Расширения линтеры. css validate в vs code.

Никогда не спешите изменять разметку или верстку. Сначала всегда проверьте все на ошибки/опечатки.

## Верстка

### 10. Фикс. отступы для центрирования

Отступы по бокам контента на макете нельзя переносить в верстку. Макет - зафиксированная картинка. А экраны у всех разные. Поэтому контент выравнивается через авто марджины. Или через флексбокс/гриды.

Вообще фикс отступы нужны для расстояний между элементами.

### 11. Ширина больше вьюпорта

Если вы видите горизонтальный скролл, значит что-то выходит за пределы вьюпорта. Этого не должно быть. Часто это означает, что ширина чего-то больше вьюпорта/родителя. Можно отловить такие элементы через девтулзы, поводив указателем за краем вьюпорта или по всем элементам или удаляя их.

Не используйте единицы vw для ширины оберток. Они будут вести себя непредсказуемо и выходить за пределы вьюпорта. Используйте проценты и пиксели (для макс. ширины).

Не используйте для скрытия того, что выходит за вьюпорт overflow: hidden. Он скрывает проблемы, но не решает их. Это может привести к неприятностям в будущем

### 12. Абсолютное позиционирование

Нельзя использовать позиционирование в раскладке. Оно нужно в отдельных случаях, чтобы расположить элемент в углу или за пределами родителя, или сдвинуть что-то для ПП.

Если вы попиксельно располагаете каждый элемент, то скорее всего вы делаете что-то не так:)

### 13. Усложнение раскладки

Если вы делаете практику А2, то вам нужно делать фиксированную верстку. Не усложняйте и не спешите с вещами, которые вы еще не проходили:) Не пытайтесь использовать проценты для половин секции. Вы не сможете нормально их выровнять. Просто задайте размеры и отступ в пикселях.
В А3 тоже не спешите делать адаптив. Сначала освойте флексбокс с фиксированной версткой.

### 14. Фикс. высота

Нельзя ограничивать высоту элементов в вебе, содержимое которых может поменяться (добавится текст, новые элементы, изменится ширина при адаптиве). Стоит проверять элементы на переполнение (добавить в параграф текста или еще один параграф). Там, где без этого не обойтись можно задавать минимальную высоту (но не максимальную или фиксированную).

### 15. Обертки

Прежде чем начать верстать посмотрите на макет. Разделите его на минимальное количество прямоугольников. Если вы верстаете на флексбоксе, то смотрите, какие элементы и обертки можно поставить в ряд. Если на гридах, то можно перенести в верстку дизайнерскую сетку, если она есть. Или составить ее самому. Можете рисовать прямо на макете. Старайтесь не создавать лишних оберток, но и экономить не надо:)

## Вопросы
### 16. Самопроверка
Проверяйте, что вы написали. Часто помогает отложить код и вернуться к нему позже.

### 17. Как задавать самому себе вопросы
Задавайте вопросы сами себе. Это развивает логическое мышление, которое поможет вам найти источник проблемы, а часто и ее решение. Не всегда просто это сделать. Начните с того, что вы видите и уже знаете. 

Например, вы видите на экране только содержимое без всякого оформления. Начинаем с определения проблемы: что не так? Есть содержимое, но нет оформления. Вопрос: что отвечает за оформление? Ответ: css файл. Если оформления вообще нет, значит css вообще "не работает". То есть от не подключен. Значит нужно проверить подключение. Как подключается css файл? Через элемент link внутри head. Вот вы уже сузили поиск до одно строчки. Осталось проверить все в link по списку выше. Опечатки в тегах и атрибутах, ошибки в относительном пути.

Всегда спрашивайте, что вы видите, в чем проблема, что может на это влиять. Вы удивитесь, как часто вы сами можете ответить на свой же вопрос.