### Служебные типы
#### Partial, Required, Readonly

##### Partial
Делает все свойства объекта необязательными
```ts
interface User {
	name: string;
	age?: number;
	email: string;
}

type PartialUser = Partial<User>;

/*
interface User {
	name?: string;
	age?: number;
	email?: string;
}
*/
```

##### Required

Делает все свойства объекта обязательными

```ts
interface User {
	name: string;
	age?: number;
	email: string;
}

type PartialUser = Required<User>;

/*
interface User {
	name: string;
	age: number;
	email: string;
}
*/
```

##### Readonly

Делает все свойства объекта **readonly**

```ts
interface User {
	name: string;
	age?: number;
	email: string;
}

type PartialUser = Readonly<User>;

/*
interface User {
	readonly name: string;
	readonly age?: number;
	readonly email: string;
}
*/
```