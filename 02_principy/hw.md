### Задание 1
**Kubernetes Gateway API** - предлагает единообразный интерфейс для настройки и эксплуатации API-шлюзов независимо от их реализации
- GatewayClass: определяет набор шлюзов с общей конфигурацией, управляемых контроллером, реализующим этот класс.
- HTTPRoute: определяет специфичные для HTTP правила для сопоставления трафика от прослушивателя шлюза с представлением конечных точек внутренней сети
- Шлюз: определяет экземпляр инфраструктуры обработки трафика, например облачный балансировщик нагрузки

**Yandex API Gateway** - Архитектурный паттерн, который предоставляет веб‑ и мобильным приложениям единую точку входа в API и за которым скрываются внутренние микросервисы

Yandex API Gateway значительно расширяет возможности разработчиков сервисов:
- упрощает создание, публикацию и обслуживание как серверных, так и бессерверных приложений;
- служит «входной дверью» для веб-сайтов и мобильных приложений,
- c помощью Yandex API Gateway приложения получают доступ к данным, бизнес‑логике или функциональности из внутренних сервисов: Yandex Cloud Functions, Yandex Serverless Containers, YDB и других.

#### Для данной задачи подходит следующий Gateway API:
Если уже имеется API-портал и экосистема, построенная вокруг него, то имеет место быть развернуть свой API Gateway и использовать связку **nginx+Lua** - надежный, протестированный software, поддерживающий масштабирование

- Авторизацию и аутентификацию можно построить с помощью доступов по сертификату
- Чтобы обеспечить высокую доступность данных клиентов, можно использовать инструмент Hazelcast
  - быстрый доступ к данным,
  - возможность организовать кластер из нескольких нод с реплицированными на разных нодах данными.
- терминация HTTPS присутствует
- маршрутизация запросов к нужному сервису осуществляется с помощью файлов конфигурации

### Задание 2

Apache Kafka представляет собой брокер, который хранит все сообщения в виде распределённого лога, причём гарантируется, что порядок сообщений отражает последовательность их поступления в систему.
- обеспечивается поддержка кластеризации, для балансирования рабочей нагрузки
высокая скорость работы
- простая настройка, быстрое восстановление
- высокая пропускная способность
- хранение сообщений на внутреннем сервере
- cуществуют различные форматы сообщений: API, проводной протокол или дисковое хранилище. Существуют встроенные библиотеки SerDes для строк, Long, ByteArrays, ByteBuffers и множество библиотек SerDes сообщества для JSON, ProtoBuf, Avro, а также форматов сообщений, специфичных для приложения
- получатели сами делают запрос у брокера на получение сообщений, брокер выдает только те сообщения, которые предназначаются данному получателю