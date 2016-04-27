# Авторизация в gitlab'e с помощью ssh ключей

## Проверка ssh ключей на компьюетере тестировщкика.

- Открываем консоль Git Bash (Пустк -> Все программы -> Git -> Git Bash)

![open git bash](Open_Git_Bash.jpg)

- В открывшейся консоли вводим команду 

```bash
 ls -al ~/.ssh
```

Эта команда выводит содержимое директории .ssh находящейся в домашнем каталоге пользователя. 

Если директория .ssh отсутствует:
![dir .ssh not found](Check_ssh_key_1.jpg)

Или директория .ssh пустая
![dir .ssh not found](Check_ssh_key_2.jpg)


Значит в системе нет сгенерированных .ssh ключей. Тогда необходимо перейтий к пунтку [Генерация ssh ключей](#Генерация ssh ключей)

Если в директории .ssh есть сгенерированные ключи:
![ssh key exists](Ssh_key_exsists.jpg)

То переходим к пункту [Добавление ssh ключей в ssh-agent](#Добавление ssh ключей в ssh-agent)

## Генерация ssh ключей

- В консоль Git Bash вводим: ssh-keygen -t rsa -b 4096 -C "email@email.ru" , где email@email.ru электропочта пользователя.

На вопрос:

- Enter file in which to save the key (/c/Users/UserName/.ssh/id_rsa): - нажмаем Enter
- Enter passphrase (empty for no passphrase):  - нажмаем Enter
- Enter same passphrase again:  - нажмаем Enter

```bash
ssh-keygen -t rsa -b 4096 -C "email@email.ru"
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/UserName/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/UserName/.ssh/id_rsa.
Your public key has been saved in /c/Users/UserName/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:Dpfi6jar0WjMC+kliTrxpcEBvAlEWCFLpSKWE9in4Mc email@email.ru
The key's randomart image is:
+---[RSA 4096]----+
|BB+o             |
|B+= .            |
|*B+o             |
|+++E     .       |
| ...  o S        |
|o++o.. =         |
|+=*=. . .        |
|+o=oo.           |
|.oo++o           |
+----[SHA256]-----+
```

![generate ssh key](Generate_ssh_key.jpg)

## Добавление ssh ключей в ssh-agent

- Запускаем ssh агент, для этого в консоли вводим команду:

```bash
eval "$(ssh-agent -s)"
```
![ssh key exists](Run_ssh_agent.jpg)

- Добавляем в ssh агент ключ, для этого в консоли вводим команду:

```bash
ssh-add ~/.ssh/id_rsa
```

![ssh key exists](Add__key_ssh_agent.jpg)

## Добавление ключей в GitLab

- Переходим на сайт GitLab'a компании, и авторизуемся

![ssh key exists](Login_GetLab.jpg)

- Переходим в настройки профиля

![ssh key exists](GetLab_profile_settings.jpg)

- В настройках профиля выбираем вкадку "SSH Keys"

![ssh key exists](Ssh_key.jpg)

- Щелкаем по кнопке "Add SSH Key"

![ssh key exists](Add_Ssh_key.jpg)

- Копируем в буфер обмена текст ключа. Для этого в консоли Git Bash выполняем следующую команду:

```bash
clip < ~/.ssh/id_rsa.pub
```

![ssh key exists](Copy_Ssh_key_in_clipboard.jpg)

- В GitLab'e в поле добавления ключей вставляем из буфера обмена (cntrl+v), текст SSH ключа, нажимаем кнопку "Add Key"

![ssh key exists](Add_key_2.jpg)


## Проверка корректности добавления ssh ключей

В Git Bash консоли вводим команду:

```bash
 ssh -T git@imc-git.mte-telecom.ru
```

При правильном выполнении всех предыдущих действий ожидается следующий результат:

![ssh key exists](Ssh_key_add_complited.jpg)


