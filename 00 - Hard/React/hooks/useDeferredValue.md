`useDeferredValue` — это хук, который позволяет отложить обновление части пользовательского интерфейса.

- `debouncing` означает, что вы будете ждать, пока пользователь перестанет печатать (например, на секунду), прежде чем обновлять список.
- `throttling` означает, что вы будете обновлять список время от времени (например, не чаще одного раза в секунду).

Хотя в некоторых случаях эти методы полезны, `useDeferredValue` лучше подходят для оптимизации рендеринга, поскольку он глубоко интегрирован с самим React и адаптируются к устройству пользователя.

В отличие от `debounce` или `throttle`, он не требует выбора фиксированной задержки. Если устройство пользователя быстрое (например, мощный ноутбук), отложенный повторный рендеринг произойдет почти сразу и не будет заметен. Если устройство пользователя работает медленно, список будет «отставать» от ввода пропорционально тому, насколько медленно работает устройство.

Кроме того, в отличие от устранения `debounce` или `throttle`, отложенный повторный рендеринг, выполняемый с помощью, `useDeferredValue` по умолчанию прерывается. Это означает, что если React находится в процессе повторного рендеринга большого списка, но пользователь делает еще одно нажатие клавиши, React прекратит этот повторный рендеринг, обработает нажатие клавиши, а затем снова начнет рендеринг в фоновом режиме. Напротив, устранение дребезга и регулирование по-прежнему вызывают неприятные ощущения, поскольку они _блокируют:_ они просто откладывают момент, когда рендеринг блокирует нажатие клавиши.

Если работа, которую вы оптимизируете, не происходит во время рендеринга, `debounce` или `throttle` все равно будут полезны. Например, они могут позволить вам отправлять меньше сетевых запросов. Вы также можете использовать эти методы вместе.