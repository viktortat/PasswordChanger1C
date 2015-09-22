<h1>Сброс паролей пользователей для файловой, клиент-серверной базы 1С и хранилища конфигураций</h1>

При утере паролей административных учеток к базам 1С есть разные варианты их восстановления. Если с клиент-серверными базами все просто, то с файловыми базами и хранилищем уже приходится использовать более сложные методы вплоть до ручного изменения определенных байтов в файлах.
Данное приложение на .NET, позволяет забыть об этих проблемах и менять пароли пользователей в пару кликов для файловых, клиент-серверных баз 1С, а также хранилища конфигураций.

<h3>В первую очередь, отказ от ответственности</h3>
<p>Это первая версия приложения, только частично протестированная на базах данных 8.3.<br />Используя приложение вы принимаете на себя всю ответственность и риски за некорректную работу алгоритмов и повреждение баз данных.<br />Перед использованием делайте бэкапы.</p>
<h3>Во-вторых:</h3>
<p>Огромная благодарность <a href="http://infostart.ru/profile/13819/" target="_blank">Валерию Агееву</a> за его работу по разбору внутренних форматов 1С и утилиту <a href="http://infostart.ru/public/19633/" target="_blank">Tool_1CD</a>.<a href="http://infostart.ru/public/19734/" target="_blank"><br />Краткое описание формата файлов *.1CD (файловых баз 1Сv8)</a></p>

<h3>Принцип работы</h3>
<p>В клиент-серверном варианте список пользователей хранится в таблице V8USERS, а хеш пароля в зашифрованном виде в поле DATA.<br />Приложение дешифрует строку из поля DATA, заменяет оба хеша (первый обычный, второй для пароля в верхнем регистре) на хеш введенной строки, шифрует строку с тем же ключем и записывает бинарные данные для указанного пользователя обратно в таблицу V8USERS.<br />Доступ к базе не требует монопольного режима.</p>
<p>В файловом варианте информационной базы логическая структура данных и алгоритмы обработки аналогичны, но данные упакованы в соответствии с внутренним форматом 1С.<br />Таблица пользователей считывается целиком, производится изменение в нужных строках, затем вся таблица BLOB данных для всех пользователей перезаписывается в файл информационной базы.<br />Требуется монопольный доступ для открытия ИБ и записи данных в нее.</p>
<p>В хранилище конфигурации 1С список пользователей хранится в таблице USERS, а некий хеш пароля в поле PASSWORD. Т.к. я не разобрал что это за формат хеша, то сделал только возможность установить пустой пароль (это фиксированная строка "d41d8cd98f00b204e9800998ecf8427e"). Таблица пользователей считывается целиком, производится изменение значений PASSWORD в нужных строках, затем вся таблица пользователей записывается в файл хранилища.<br />Требуется монопольный доступ для открытия ИБ и записи данных в нее.</p>
<h3>Скриншоты с примерами</h3>
<p>Файловая информационная база</p>
<p><img style="border: 1px solid black;" src="http://infostart.ru/upload/iblock/9d5/1.png" alt="" width="768" height="333" /></p>
<p>&nbsp;</p>
<p>Клиент-серверная информационная база</p>
<p><img style="border: 1px solid black;" src="http://infostart.ru/upload/iblock/a18/2.png" alt="" width="768" height="398" /></p>
<p>&nbsp;</p>
<p>Хранилище конфигурации 1С</p>
<p><img style="border: 1px solid black;" src="http://infostart.ru/upload/iblock/f0c/3.png" alt="" width="768" height="450" /></p>
<p>&nbsp;</p>
<h3>Поддержка и развитие</h3>
<p>Предложения, вопросы, комментарии, а также обнаруженные ошибки оставляйте, пожалуйста, в Issues.</p>
