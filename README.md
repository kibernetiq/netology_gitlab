# Домашнее задание к занятию 12 «GitLab»

## Основная часть

### DevOps

В репозитории содержится код проекта на Python. Проект — RESTful API сервис. Ваша задача — автоматизировать сборку образа с выполнением python-скрипта:

1. Образ собирается на основе [centos:7](https://hub.docker.com/_/centos?tab=tags&page=1&ordering=last_updated).
2. Python версии не ниже 3.7.
3. Установлены зависимости: `flask` `flask-jsonpify` `flask-restful`.  
[requirements.txt](https://github.com/kibernetiq/netology_gitlab/blob/main/requirements.txt)
4. Создана директория `/python_api`.
5. Скрипт из репозитория размещён в /python_api.
6. Точка вызова: запуск скрипта.  
[Dockerfile](https://github.com/kibernetiq/netology_gitlab/blob/main/Dockerfile)

7. При комите в любую ветку должен собираться docker image с форматом имени hello:gitlab-$CI_COMMIT_SHORT_SHA . Образ должен быть выложен в Gitlab registry или yandex registry.   
[.gitlab-ci.yml](https://github.com/kibernetiq/netology_gitlab/blob/main/.gitlab-ci.yml)
<p align="center">
  <img src="./Screenshots/1.png">
</p>
<p align="center">
  <img src="./Screenshots/2.png">
</p>


### Product Owner

Вашему проекту нужна бизнесовая доработка: нужно поменять JSON ответа на вызов метода GET `/rest/api/get_info`, необходимо создать Issue в котором указать:

1. Какой метод необходимо исправить.
2. Текст с `{ "message": "Already started" }` на `{ "message": "Running"}`.
3. Issue поставить label: feature.
<p align="center">
  <img src="./Screenshots/4.png">
</p>


### Developer

Пришёл новый Issue на доработку, вам нужно:

1. Создать отдельную ветку, связанную с этим Issue.
<p align="center">
  <img src="./Screenshots/5.png">
</p>  

2. Внести изменения по тексту из задания.
<p align="center">
  <img src="./Screenshots/6.png">
</p>  

3. Подготовить Merge Request, влить необходимые изменения в `master`, проверить, что сборка прошла успешно.
<p align="center">
  <img src="./Screenshots/7.png">
</p>  


### Tester

Разработчики выполнили новый Issue, необходимо проверить валидность изменений:

1. Поднять докер-контейнер с образом `python-api:latest` и проверить возврат метода на корректность.
```
$ curl localhost:5290/get_info
{"version": 3, "method": "GET", "message": "Running"}
```
2. Закрыть Issue с комментарием об успешности прохождения, указав желаемый результат и фактически достигнутый.
<p align="center">
  <img src="./Screenshots/8.png">
</p>


## Итог

В качестве ответа пришлите подробные скриншоты по каждому пункту задания:

- файл gitlab-ci.yml;  
[.gitlab-ci.yml](https://github.com/kibernetiq/netology_gitlab/blob/main/.gitlab-ci.yml)
- Dockerfile;   
[Dockerfile](https://github.com/kibernetiq/netology_gitlab/blob/main/Dockerfile)
- лог успешного выполнения пайплайна;
<p align="center">
  <img src="./Screenshots/9.png">
</p>  

- решённый Issue.
<p align="center">
  <img src="./Screenshots/8.png">
</p>
