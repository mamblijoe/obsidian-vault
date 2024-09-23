
---
date: {{date}}T{{time}}
tags: [Daily]
cssclasses: [daily, {{date:dddd}}]
---

## Что такое PWA, какие есть преимущества и недостатки
Progressive Web Apps (PWA) или прогрессивные веб-приложения — это не какой-то фреймворк или SDK. Это философия того, как надо строить современные веб-приложения.

`Прогрессивное веб-приложение (PWA) `— это веб-приложение, которое использует прогрессивные улучшения, чтобы предоставить пользователям более надежный интерфейс, использует новые возможности для обеспечения более интегрированного взаимодействия и может быть установлено. А поскольку это веб-приложение, оно может быть доступно кому угодно, где угодно и на любом устройстве, и все это с помощью единой базы кода. После установки PWA выглядит как любое другое приложение, а именно:

- У него есть значок на главном экране, в средстве запуска приложений, на панели запуска или в меню «Пуск».
- Он появляется при поиске приложений на устройстве.
- Он открывается в отдельном окне, полностью отделенном от пользовательского интерфейса браузера.
- Он имеет доступ к более высоким уровням интеграции с ОС, например, обработке URL-адресов или настройке строки заголовка.
- Он работает в автономном режиме.

## Какие обязательные составляющие PWA

## Какие критерии нужны для возможности установки приложения
Чтобы сделать сайт доступным для установки, ему необходимы следующие вещи:

- Веб-манифест с [правильно заполненными полями](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Guides/Making_PWAs_installable#manifest)
- Сайт должен использовать защищённый (HTTPS) домен
- Иконка для предоставления приложения на устройстве
- Зарегистрированный service worker, чтобы приложение работало в off-line режиме (на данный момент требуется только для Chrome на Android)

## manifest.json
Ключевым элементом является файл манифеста, в котором представлена вся информация о веб-сайте в JSON формате.

Обычно находится в корневой папке веб-приложения. Содержит информацию, такую как название приложения, paths пути к значкам разных размеров, которые можно использовать для представления приложения в мобильных операционных системах (например, в качестве значка домашнего экрана), и цвет фона для использования при загрузке. Эта информация необходима браузеру для правильного отображения приложения при установке и на домашнем экране.

## Везде ли можно использовать сервис воркеры?
Service workers могут быть использованы практически везде, где поддерживается браузером. Однако есть некоторые ограничения и рекомендации:

1. **HTTPS**: Service workers требуют использования HTTPS из соображений безопасности. Это означает, что вы не сможете использовать их на незащищенных сайтах (без SSL-сертификата).
2. **Scope**: Service workers работают в рамках своего собственного URL-адреса (scope). Это означает, что они не могут перехватывать запросы для других доменов.
3. **Браузерная поддержка**: Хотя большинство современных браузеров поддерживают service workers, стоит проверить поддержку для конкретных функций, если вы используете какие-то продвинутые возможности.
4. **Ограничения операционной системы и устройства**: Некоторые операционные системы и устройства могут иметь свои собственные ограничения на использование service workers. Например, мобильные устройства могут приостанавливать работу фоновых сервисов для экономии заряда батареи.
5. **Клиентская поддержка**: Некоторые пользователи могут отключить JavaScript или другие веб-технологии, которые используются для регистрации и управления service workers. Это следует учитывать при проектировании сайта.

## В чем разница с нативными приложениями

## Где хранится кеш?
CacheStorage

## Что стоит хранить в кеше?
* assets
* vendors
* html
* json
## Статический / динамический кеш

## Жизненный цикл сервис воркера
With service workers, the following steps are generally observed for basic setup:

1. The service worker code is fetched and then registered using [`serviceWorkerContainer.register()`](https://developer.mozilla.org/en-US/docs/Web/API/ServiceWorkerContainer/register). If successful, the service worker is executed in a [`ServiceWorkerGlobalScope`](https://developer.mozilla.org/en-US/docs/Web/API/ServiceWorkerGlobalScope); this is basically a special kind of worker context, running off the main script execution thread, with no DOM access. The service worker is now ready to process events.
2. Installation takes place. An `install` event is always the first one sent to a service worker (this can be used to start the process of populating an IndexedDB, and caching site assets). During this step, the application is preparing to make everything available for use offline.
3. When the `install` handler completes, the service worker is considered installed. At this point a previous version of the service worker may be active and controlling open pages. Because we don't want two different versions of the same service worker running at the same time, the new version is not yet active.
4. Once all pages controlled by the old version of the service worker have closed, it's safe to retire the old version, and the newly installed service worker receives an `activate` event. The primary use of `activate` is to clean up resources used in previous versions of the service worker. The new service worker can call [`skipWaiting()`](https://developer.mozilla.org/en-US/docs/Web/API/ServiceWorkerGlobalScope/skipWaiting) to ask to be activated immediately without waiting for open pages to be closed. The new service worker will then receive `activate` immediately, and will take over any open pages.
5. After activation, the service worker will now control pages, but only those that were opened after the `register()` is successful. In other words, documents will have to be reloaded to actually be controlled, because a document starts life with or without a service worker and maintains that for its lifetime. To override this default behavior and adopt open pages, a service worker can call [`clients.claim()`](https://developer.mozilla.org/en-US/docs/Web/API/Clients/claim).
6. Whenever a new version of a service worker is fetched, this cycle happens again and the remains of the previous version are cleaned during the new version's activation.
![[pwa-lifecycle.png]]
## Как продебажить PWA на разных устройствах / браузерах

## Как кастомизировать кнопку установки

