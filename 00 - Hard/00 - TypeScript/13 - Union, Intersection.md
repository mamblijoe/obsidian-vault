## Тип Объединение (Union Types)

Объединение ( `Union` ) — это мощный механизм позволяющий создавать из множества существующих типов логическое условие по которому данные могут принадлежать только к одному из указанных типов. Объединение указывается с помощью оператора прямой черты `|` , по обе стороны которой располагаются типы данных.

Переменной, которой был указан тип объединения `A` или `B` или `C` , может быть присвоено значение, принадлежащие к одному из трех типов.

```ts
let v1: T1 | T2 | T3;
```

## Тип Пересечение (Intersection Type)

Пересечение ( `Intersection` ) — ещё один мощный механизм `TypeScript`, который позволяет рассматривать множество типов данных как единое целое. Пересечение указывается с помощью оператора амперсанда `&` по обе стороны от которого указываются типы данных.

Переменной, которой был указан тип пересечение `A` и `B` и `С` должно быть присвоено значение принадлежащее к типам `A` и `B` и `C` одновременно.

```ts
let v1: T1 & T2 & T3;
```