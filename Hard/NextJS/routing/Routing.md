>[!info]
>По умолчанию компоненты внутри `app`— это [React Server Components](https://nextjs.org/docs/app/building-your-application/rendering/server-components) . Это оптимизация производительности и позволяет легко их внедрить, а также можно использовать [Client Components](https://nextjs.org/docs/app/building-your-application/rendering/client-components) .

## [Соглашения о файлах](https://nextjs.org/docs/app/building-your-application/routing#file-conventions)

Next.js предоставляет набор специальных файлов для создания пользовательского интерфейса с определенным поведением во вложенных маршрутах:

|Файл|Цель|
|---|---|
|[`layout`](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#layouts)|Общий пользовательский интерфейс для сегмента и его дочерних элементов|
|[`page`](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#pages)|Уникальный пользовательский интерфейс маршрута и возможность сделать маршруты общедоступными.|
|[`loading`](https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming)|Загрузка пользовательского интерфейса для сегмента и его дочерних элементов|
|[`not-found`](https://nextjs.org/docs/app/api-reference/file-conventions/not-found)|Не найден пользовательский интерфейс для сегмента и его дочерних элементов.|
|[`error`](https://nextjs.org/docs/app/building-your-application/routing/error-handling)|Пользовательский интерфейс ошибок для сегмента и его дочерних элементов|
|[`global-error`](https://nextjs.org/docs/app/building-your-application/routing/error-handling)|Глобальный интерфейс ошибок|
|[`route`](https://nextjs.org/docs/app/building-your-application/routing/route-handlers)|Конечная точка API на стороне сервера|
|[`template`](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#templates)|Специализированный переработанный интерфейс макета|
|[`default`](https://nextjs.org/docs/app/api-reference/file-conventions/default)|Резервный пользовательский интерфейс для [параллельных маршрутов](https://nextjs.org/docs/app/building-your-application/routing/parallel-routes)|
