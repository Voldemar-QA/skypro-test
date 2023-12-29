# GitHub Issues Stoliarov Vladimir

## Описание
Работа с коллекцией Postman для взаимодействия с API "GitHub Issues". 
Коллекция реализует функционал:
1. Создание Issue в репозитории GitHub.
2. Получение списка имеющихся в репозитории Issues.
3. Переименование Issue, созданного в шаге 1.
4. Получение информации о переименованном Issue.
5. Удаление переименованного Issue.

## Требования
- Postman версии 10.10.0 или выше.
- Браузер Chrome v.120.0.6099.130 или иной.
- Windows 10 или выше.
- Создан аккаунт GitHub.
- Создан или клонирован тестовый репозиторий с произвольным содержимым для работы с Issues.

## Установка
1. [Создать и сохранить](https://github.com/settings/tokens "Создание личных токенов в GitHub") персональный токен доступа к API GitHub с максимальными правами администратора.
2. [Импортировать коллекцию](https://drive.google.com/file/d/1LzZUqGwWVdP8J58xSOH2gKX0mFipyKen/view?usp=sharing "GitHub_Issues_Stoliarov_Vladimir.postman_collection") в Postman.
3. Настроить переменные окружения:
   - во вкладке Authorization выбрать Type = Bearer Token;
   - вставить в соответствующее поле персональный токен доступа к API GitHub;
   - во вкладке Variables создать переменную token;
   - вставить в соответствующие поля Initial value и Current value персональный токен доступа к API GitHub;
   - во вкладке Variables создать переменную baseURL;
   - вставить в соответствующие поля Initial value и Current value базовый URL, куда будут отправляться запросы - https://api.github.com/repos/[user]/[repo]/issues
     где [user] = логин хозяина репозитория, [repo] = название репозитория в строке адреса;
   - во вкладке Variables создать переменную number для передачи номера создаваемого / изменяемого issue.

## Использование
1. Открыть коллекцию в Postman.
2. Проверить переменные окружения.
3. Проверить тестовые скрипты, в том числе скрипты для передачи данных в переменные окружения.
4. Выполнить запросы в соответствии с описанием тест-кейсов в [тест-сьюте для API](https://drive.google.com/file/d/1H53cHaUDdPUKtZRh8yMFIs-NQc5ZzlOz/view?usp=sharing "Тест-ран с описанием тест-кейсов").

## Примеры ответов
1. Пример успешного ответа:  
Status code 201 Created  
PASS Status code is 200 or 2XX  
{"url": "https://api.github.com/repos/[user]/[repo]/issues/[number]",  
...  
"id": 2059193243,  
...  
"number": 18,        //как пример  
"title": "Issue 1",  
"user": {  
"login": "[user]",  
...  
"type": "User",  
"site_admin": false},  
"labels": [{...  
"url": "https://api.github.com/repos/[user]/skypro-test/labels/bug",  
"name": "bug",  
...  
"default": true,  
"description": "Something isn't working"}],  
...  
"assignee": {  
"login": "[user]",  
...  
"url": "https://api.github.com/users/[user]",  
"html_url": "https://github.com/[user]",  
...  
"type": "User",  
"site_admin": false},  
"assignees": [{  
"login": "[user]",  
...  
"url": "https://api.github.com/users/[user]",  
"html_url": "https://github.com/[user]",  
...  
"type": "User",  
"site_admin": false},]  

3. Пример ответа с ошибкой:  
   Status 404 Not Found  
   FAIL AssertionError: expected 404 to be one of [200, 201, 204].  
   {"message": "Not Found",  
   "documentation_url": "https://docs.github.com/rest"}  

## Проблемы и решения
Проблема выполнения последнего теста с удалением Issue через API остается нерешенной.  
Через внешний интерфейс удаление Issue происходит без проблем.  
Однако, не только через Postman, но и просто через командную строку удалить Issue не удается.  
Возможно, это баг. Пример команды на удаление Issue через Curl и результат:  

$ curl -X DELETE -H "Authorization: Bearer //токен авторизации//" https://api.github.com/repos/[user]/[repo]/issues/[number]  
% Total    % Received % Xferd  Average Speed   Time  Time  Time  Current  Dload  Upload   Total   Spent    Left  Speed  
100    84    100    84     0     0     99      0 --:--:-- --:--:-- --:--:--    99  
{ "message": "Not Found",  "documentation_url": "https://docs.github.com/rest" }  

## Лицензия
Этот проект распространяется под лицензией MIT (свобода использования, модификации, модификации, распространения, отсутствие гарантий.)

Предыдущая версия Readme.md: Skypro home work.
This is text file describing home work task from Skypro.
