`useLayoutEffect` — это версия [[useEffect]], которая срабатывает до того, как браузер перерисовывает экран.

>[!warning] `useLayoutEffect` может снизить производительность.
>Если это возможно, отдавайте предпочтение `useEffect`.

>[!warning] Рендеринг в два прохода и блокировка браузера снижают производительность. Постарайтесь избегать этого, когда можете.

