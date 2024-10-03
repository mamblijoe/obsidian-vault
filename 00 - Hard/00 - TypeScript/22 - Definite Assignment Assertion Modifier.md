
## Модификатор утверждения не принадлежности значения к типу undefined

TypeScript содержит модификатор `definite assignment assertion modifier`, который указывается с помощью символа восклицательного знака ( `!` ), располагаемого после идентификатора поля или переменной.

```ts
class Identifier {
	public identifier!: Type;
}
// или
const identifier!: Type;
```

Применяя модификатор `definite assignment assertion modifier`, разработчик сообщает компилятору, что берет ответственность за инициализацию поля на себя.