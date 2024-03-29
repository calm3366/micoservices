### Задание 1
#### Для обеспечения процесса разработки подойдет программный продукт **Gitlab**.

#### Он соответствует всем нужным критериям, имеет многофункциональный интерфейс управления CI-CD процессами.

- облачная система;
- система контроля версий Git;
- репозиторий на каждый сервис;
- запуск сборки по событию из системы контроля версий;
- запуск сборки по кнопке с указанием параметров;
- возможность привязать настройки к каждой сборке;
- возможность создания шаблонов для различных конфигураций сборок;
- возможность безопасного хранения секретных данных (пароли, ключи доступа);
- несколько конфигураций для сборки из одного репозитория;
- кастомные шаги при сборке;
- собственные докер-образы для сборки проектов;
- возможность развернуть агентов сборки на собственных серверах;
- возможность параллельного запуска нескольких сборок;
- возможность параллельного запуска тестов.

### Задание 2
#### Для обеспечения сбора и анализа логов сервисов подойдет стек ELK - Elasticsearch, Logstash и Kibana

Этот стек позволяет «из коробки» получить средство агрегации и трансформации, хранения и визуализации данных логирования

#### Logstash в Elastic-стеке сбора логов — инструмент для приёма данных, их преобразования и отправки в кластер БД Elasticsearch
#### Elasticsearch — база данных, адаптированная для полнотекстового поиска
#### Kibana — эффективное средство визуализации данных логов

Данный стек отвечает необходимым требованиям:
- сбор логов в центральное хранилище со всех хостов, обслуживающих систему;
- минимальные требования к приложениям, сбор логов из stdout;
- гарантированная доставка логов до центрального хранилища;
- обеспечение поиска и фильтрации по записям логов;
- обеспечение пользовательского интерфейса с возможностью предоставления доступа разработчикам для поиска по записям логов;
- возможность дать ссылку на сохранённый поиск по записям логов.

### Задание 3
#### Для обеспечения сбора и анализа состояния хостов и сервисов подойдет средство визуализации Grafana в совокупности с источниками данных для каждого сервиса
Данный продукт отвечает необходимым требованиям:
- сбор метрик со всех хостов, обслуживающих систему;
- сбор метрик состояния ресурсов хостов: CPU, RAM, HDD, Network;
- сбор метрик потребляемых ресурсов для каждого сервиса: CPU, RAM, HDD, Network;
- сбор метрик, специфичных для каждого сервиса;
- пользовательский интерфейс с возможностью делать запросы и агрегировать информацию;
- пользовательский интерфейс с возможностью настраивать различные панели для отслеживания состояния системы.

### Zabbix vs Prometheus
- Срок хранения данных. Prometheus создавался для оперативного мониторинга, то есть для краткосрочного хранения и обработки метрик (используется оптимизированная для временных рядов TSDB). Если возникнет необходимость проанализировать параметры за несколько недель или месяцев, то придется искать готовое решение. Prometheus же отлично справляется с долгосрочным хранением внушительных объемов данных благодаря поддержке PostgreSQL+ TSDB.
- Аутентификация/авторизация. В Zabbix продумана простая аутентификация с быстрой настройкой прав доступа к хостам, отдельным серверам. При использовании Prometheus в работе с некоторыми системами придется «поиграть» с ограничениями на файрволл или создать basic_auth.
- Установка. Zabbix инсталлируется «из коробки» и адаптируется ко всем видам ПО, а для Prometheus понадобится установка бинарника, юнита в Systemd или скрипта для автоматического запуска.
- Для доставки уведомлений в Prometheus необходима установка Alertmanager, а в Zabbix задействуются штатные приложения.

Это лишь часть отличий между этими программами мониторинга. При работе с ПО становится очевидным, что Prometheus – это сервис «от программиста программисту» , который больше подходит для динамических задач. А Zabbix универсален и подходит для мониторинга проектов любого масштаба.
