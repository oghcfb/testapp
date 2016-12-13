# testapp

Структура проекта:
- rest/contract   -  спецификация API в Swagger формате
- rest/collections -  POSTMAN testing suites (collection) 
- rest/env   - файлы параметров сред (environment) для POSTMAN

## Цель
1. поднять (на отдельной среде) mock API, описанного в спецификации Swagger2;
2. загрузить тестовые сценарии Postman на другой отдельный сервер;
3. запустить тест. сценарии Postman против mock API поднятого в 1ом шаге.


## Схема окружения
<img src="http://image.prntscr.com/image/e1c94c17179947aa9f6ecb4e24604288.png">


## Запуск MOCK сервера
для этого необходимо иметь установлен на локальной машине mock сервера package Prism (http://stoplight.io/platform/prism/)

### Help для работы с prism:
<code> prism -h </code>

### Запуск mock сервера с API COD
<code> prism run --list --mock --spec https://raw.githubusercontent.com/oghcfb/testapp/master/rest/contract/last.json -p 4020 </code>

## Запуск тестов против сервисам на mock сервере:
Для этого необходимо иметь наинсталирован на машине откуда запускаются тесты, package NEWMAN (https://github.com/postmanlabs/newman)

### Запуск тестов против сервисам на mock сервере:

<code> newman run https://raw.githubusercontent.com/oghcfb/testapp/master/rest/collections/COD_basic_process_collection_last.json -e https://raw.githubusercontent.com/oghcfb/testapp/master/rest/env/mock.postman_environment.json </code> 

## Запуск тестов против сервисам  api-sandbox:
разница только в файле с environment (switch -e)

<code> newman run https://raw.githubusercontent.com/oghcfb/testapp/master/rest/collections/COD_basic_process_collection_last.json -e https://raw.githubusercontent.com/oghcfb/testapp/master/rest/env/test.postman_environment.json </code> 
