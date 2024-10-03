
Модификаторы доступа — это ключевые слова, с помощью которых осуществляется управление сокрытием данных в классе.

В `TypeScript` существует три модификатора доступа, указывающихся с помощью ключевых слов `public` , `protected` и `private` . Влияние модификаторов доступа ограничивается `TypeScript` и после компиляции от них не остается ни следа. В скомпилированном коде нет никакой разницы между членами, к которым были применены те или иные модификаторы доступа.

```ts
class Animal {
	private static DEFAULT_NICKNAME: string = 'animal';
	
	protected static inputInfoDecor(text: string): string {
		return `[object ${text}]`;
	}

	private _nickname: string = Animal.DEFAULT_NICKNAME;
	
	public get nickname(): string {
		return this._nickname;
	}
	
	public set nickname(value: string) {
		this._nickname = value;
	}
	
	public constructor() {}

	public toString(): string {
		return Animal.inputInfoDecor('Animal');
	}
}
```

## Модификатор доступа public (публичный)

Члены, помеченные ключевым словом `public` , доступны в определяющих их классах, их потомках, а также к ним можно обращаться через экземпляр или, в случае статических членов, через ссылку на класс.

```ts
class Animal {
	public nickname: string;
	constructor() {
	this.nickname = 'animal';
	}
}

class Bird extends Animal {
	constructor() {
	super();
	super.nickname = 'bird';
	}
}

let animal: Animal = new Animal();
animal.nickname = 'newAnimal';
```

## Модификатор доступа private (закрытый или скрытый)

Модификатор доступа `private` является полной противоположностью модификатору доступа public . Члены, помеченные с помощью ключевого слова `private` , доступны только контексту класса, в котором они определены.

```ts
class Animal {
	private metainfo: string;
	
	constructor() {
		this.metainfo = '...';
	}
}

class Bird extends Animal {
	constructor() {
	super();
	super.metainfo = 'bird'; // Error
	}
}

let animal: Animal = new Animal();
animal.metainfo = 'newAnimal'; // Error
let bird: Bird = new Bird();
bird.metainfo = 'newBird'; // Error
```

## Модификатор доступа protected (защищенный)

Члены, которым установлен модификатор доступа `protected` , доступны только контексту класса, в котором они определенны, а также всем его потомкам. Попытка обратится к членам, помеченным как `protected` снаружи, приведет к возникновению ошибки.

```ts
class Animal {
	protected isUpdate: boolean;
	
	constructor() {
		this.isUpdate = false;
	}
}

class Bird extends Animal {
	constructor() {
		super();
		super.isUpdate = false;
	}
}

let animal: Animal = new Animal();
animal.isUpdate = true; // Error
let bird: Bird = new Bird();
bird.isUpdate = true; // Error
```

## Модификаторы доступа и конструкторы класса

В `TypeScript` существует возможность управлять доступом конструкторов. Конструктор, который не отмечен ни одним модификатором доступа эквивалентен конструктору, помеченному как `public` .

```ts
class A {
	public constructor() {} // модификатор public установлен явно
}

class B {
	constructor() {} // модификатор public установлен не явно
}
```

Если класс состоит только из статических свойств и методов, как например класс `Math`, то его конструктор более разумно пометить как приватный и, тем самым, запретить создание его экземпляров.

```ts
class AnimalUtil {
	private static MS_TO_DAY: number = 1000 * 60 * 60 * 24;
	
	public static ageFromMsToDayFormat(time: number): number {
		return Math.ceil(time / AnimalUtil.MS_TO_DAY);
	}

	private constructor() {};
}
	
class Animal {
	private _timeOfBirth: number = Date.now();
	
	public get age(): number {
		return this._timeOfBirth - Date.now();
}

let animal: Animal = new Animal();
let age: number = AnimalUtil.ageFromMsToDayFormat(animal.age);
let util = new AnimalUtil(); // Ошибка при компиляции, нельзя создать
экземпляр
```

Кроме того, класс, у которого конструктор объявлен с модификатором доступа `private` , нельзя расширять ( `extends` ).

Класс, в котором конструктор объявлен с модификатором доступа `protected` , как и в случае с модификатором доступа `private` , также не позволит создать свой экземпляр, но открыт для расширения ( `extends` ).

```ts
class Animal {
	protected constructor() {}
}

// можно наследоваться от класса с защищенным конструктором
class Bird extends Animal {
	constructor() {
	super();
	}
}

let animal: Animal = new Animal(); // Error
let bird: Bird = new Bird(); // Ok
```

## Быстрое объявление полей

Сокращенный способ инициализации полей класса:

```ts
class FishEntity {
	constructor(
		public name: string,
		public age: number,
		public isAlive: boolean
	) {}
}
```