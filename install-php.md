# Установка php под windows

- Переходим по ссылке [http://windows.php.net/download/](http://windows.php.net/download/)
- Необходимо скачать версию php 5.6 (выбрать Non Thread Safe)
![php_download](php_download.jpg)
- Создаем дирикторию c:\php (должна быть пустой)
- Распаковываем содержимое скаченного архива, директорию c:\php
![install_php](install_php.jpg)
- Переименовываем файл c:\php\php.ini-development в php.ini

                                   Было | Стало  
----------------------------------------|---------------------
![ini-development](ini_development.jpg) | ![ini](ini.jpg)

- Открываем на редактирование файл php.ini. Далее необходимо заменить ряд  строк:

Было                        |Стало
----------------------------|------------------------------
;date.timezone =            | date.timezone = Europe/Moscow
;extension=php_curl.dll     | extension=ext/php_curl.dll
;extension=php_intl.dll     | extension=ext/php_intl.dll
;extension=php_mbstring.dll | extension=ext/php_mbstring.dll
;extension=php_openssl.dll  | extension=ext/php_openssl.dll
;extension=php_pdo_mysql.dll| extension=ext/php_pdo_mysql.dll
;extension=php_pdo_pgsql.dll| extension=ext/php_pdo_pgsql.dll
;extension=php_soap.dll     | extension=ext/php_soap.dll

![add_ext](add_ext.jpg)

# добавить php в переменные среды PATH

- выбрать меню пуск - мой компьютер - (щелчок правой кнопки мыши)- свойства
![ 	my_computer_property]( 	my_computer_property.jpg )

- дополнительные параметры системы
![advanced_setting](advanced_setting.jpg) 

- параметры среды 
![parametrs](parametrs.jpg)  

- выбираем переменную  path и нажимаем кнопку "изменить"
![path](path.jpg)   


