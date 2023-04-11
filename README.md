<p align="center">
      <img src="https://ibb.co/q5J3FXq" alt="Project Logo">
</p>

## ParaDice
- Данный проект представляет собой онлайн-магазин настольных игр ParaDice. 
- На данный момент реализовано локальное развертывание проекта.
- Подключение к базе данных и работа с ней через pgAdmin.
- Информирование об ошибках через электронный адрес.

## Расположение исходных файлов
Ввиду объема данных и сокращения времени для установки всех дополнительных плагинов – файл с проектом можно найти здесь – [google диск](https://drive.google.com/drive/u/0/folders/1M1rPz1LwzC1u4PJAeoKyoBrIau6FNCOi).

## Запуск с помощью VS Code и pgAdmin

### Установка ПО
1.	Скачать проект и базу данных для него с [google диска]((https://drive.google.com/drive/u/0/folders/1M1rPz1LwzC1u4PJAeoKyoBrIau6FNCOi)).
2.	Установить обеспечение для работы с [node.js](https://nodejs.org/en/download).
3.	Установить [pgAdmin](https://www.pgadmin.org/download/).

### Запуск базы данных 
1.	Открыть pgAdmin 4.
2.	Придумать и ввести пароль для сервера.
3.	Перейти через вложения Servers -> PostgreSQL -> Databases.
4.	Создать базу данных. ПКМ по Databases. Create.
5.	Ввести название – возможно любое.
6.	Восстановить базу данных из файла, который также находится на google диске. (online-store.sql) Restore -> Filename -> Выбрать скачанный файл.
6.1.	На данном этапе может возникнуть проблема. Отсутствует путь к PostgreSQL. Решение:
File -> Preference -> Paths -> Binary Paths -> PostgreSQL Binary Path. 
Выбрать версию (15, предположительно). Прописать путь к PostgreSQL. Пример: C:\Program Files\PostgreSQL\15\bin

### Запуск проекта
1.	Открыть проект через папку. Open folder.
2.	Найти и открыть вложение server и перейти к файлу .env.
3.	Ввести локальные данные:
```env
    PORT=5000
    DB_NAME=...
    DB_USER=postgres
    DB_PASSWORD=...
    DB_HOST=localhost
    DB_PORT=...
    SECRET_KEY=POG_CHAMP_random_key30
```

- **-** DB_NAME – название созданной базы данных
- **-** DB_USER – по умолчанию
- **-** DB_PASSWORD – пароль, который вводится при запуске pgAdmin
- **-** DB_HOST – по умолчанию
- **-** DB_PORT – можно найти –> pgAdmin -> Servers. ЛКМ по PostgreSQL 15. Скопировать значение из Port.

4.	После этого перейти в файл server->index.js и ввести свои данные в строки 28-36 и 38-44. Эти строки отвечают за информирование об ошибках с помощью электронной почты. При возникновении ошибки с emailer – возможно пригодится данная [информация](https://www.courier.com/error-solutions/535-authentication-failed-nodemailer/).
```js
    let transporter = nodemailer.createTransport({
        host: 'smtp.ethereal.email',
        port: 587,
        secure: false,
        auth: {
            user: "antonio80@ethereal.email",
            pass: "PCS7FrnZKDDEpbK35Y",
        },
    })

    let result = await transporter.sendMail({
        from:'"Node js" <antonio80@ethereal.email>',
        to: 'lempi.okuneva44@ethereal.email',
        subject: 'Message from node',
        text: 'This message was sent',
        html:'this <i>message<i/> was sent from <strong>Node.js</strong> server'
    })
```
5.	Создать 2 терминальных окна. Server и Client. (Ctrl+Shift+` по умолчанию)
6.	В Server прописать: cd server -> npm run dev
7.	В Client: cd client -> npm start
8.	Через браузер по умолчанию на localhost откроется данный проект.

## Запуск проекта может быть произведен с помощью другого ПО. Приведены ошибки, столкнуться с которыми можно вероятнее всего.

## Авторы
- **-** Соболевский С.
- **-** Дедина А.
- **-** Шалесный Н.

## Лицензия
Проект распространяется под MIT license.
