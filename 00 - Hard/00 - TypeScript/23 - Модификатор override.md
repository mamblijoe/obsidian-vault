## Модификатор override и флаг --noImplicitOverride

В TypeScript существует модификатор overr
ide , который однозначно указывает на переопределение методов родительского
класса. При использовании модификатора override компилятор сможет понять, что
происходит переопределение несуществующих в суперклассе методов и сообщить об
этом с помощью ошибки.

```ts
class SuperClass {
/**
* Удалили a() и b() и добавили c().
*/
	с(){}
}

class SubClass extends SuperClass {
/**
* [*] Error ->
* This member cannot have an 'override' modifier
* because it is not declared in the base class
'SuperClass'.ts(4113)
*
* Теперь компилятор понимает, что происходи переопределение
* несуществующих методов.
*/
	override a(){} // [*]
	
	override b(){} // [*]
}
```