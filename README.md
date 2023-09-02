# Development docker-compose template

This is template for new php project with docker usages. It used to fast pet-project infrastructure set up with docker-compose.

## Dependency 
You need already installed docker-compose:
  
https://github.com/Yelp/docker-compose/blob/master/docs/install.md

## How to use
1. git clone or download. Dont forget remove .git before work with pet-project.
2. add source code as though it's local project (for example - app directory with some code)
3. check docker-compose configuration. It already would works if you need nginx+php only.
4. go to terminal and run:
```
docker-compose up -d
```
Docker will build container from php image and install php extensions.

After built and start open you browser by `localhost:8087` (docker-compose.yml port assigned in section `app`) and it would work now!

You can also use `client` directory to create your frontend client here.
Nginx config already configured to route `localhost:8086` to client/public/index.html file.

Do not forget bind `build` directory for nginx of your client if you will use it.
Just change:
1. `docker-compose.yml` volumes for `nginx` section to bind build directory, like this:
```
    volumes:
        - ./.docker/nginx/conf.d:/etc/nginx/conf.d/
        - ./client/build:/var/www/public  # here a new client content binding
```
2. `.docker/nginx/conf.d/client.conf` should point to correct root dir and index file

---
# Шаблон docker-compose для разработчика

Это шаблон для новых проектов на php, с использованием docker. Применяется для быстрого поднятия инфраструктуры pet-проектов на основе docker-compose.

## Зависимости 
Должен быть уже установлен docker-compose:
  
https://github.com/Yelp/docker-compose/blob/master/docs/install.md

## Как пользоваться
1. git clone или download. Не забудьте удалить .git, до того как начинать разработку pet-проекта.
2. добавляем свой код как будто это локальный проект (ну например, директорию app и всё такое)
3. проверяем конфигурацию docker-compose. По-умолчанию конфигурация рабочая если вам нужен только nginx+php 
4. идём в терминал (консоль) и запускаем:
```
docker-compose up -d
```
Здесь сначала докер будет собирать контейнер из образа, устанавливать расширения для php.

После того как всё будет запущено, открываем в браузере `localhost:8086` 
(docker-compose.yml прописан порт в секции `app`) и это уже должно работать!

Вы также можете использовать директорию `client` для создания своего фронтенд-клиента.
Nginx уже сконфигурирован чтобы перенаправлять запросы с `localhost:8086` на файл client/public/index.html

Не забудьте привязать свою директорию `build` клиента в nginx если будете использовать эту функциональность.

Просто замените:
1. Проброс содержимого билда в `docker-compose.yml` для `nginx` , как-то так:
```
    volumes:
        - ./.docker/nginx/conf.d:/etc/nginx/conf.d/
        - ./client/build:/var/www/public  # вот это проброс билда внутрь nginx
```
2. `.docker/nginx/conf.d/client.conf` должен указывать на корректную root директрию и index.html файл внутри контейнера nginx
