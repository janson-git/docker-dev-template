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

Open you browser by `localhost:8086` (docker-compose.yml port assigned in section `web`) and it would work now!

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

Открываем в браузере `localhost:8086` (docker-compose.yml прописан порт в секции `web`) и это уже должно работать!
