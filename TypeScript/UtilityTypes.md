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

---

##### Omit

Выкидывает свойство из типа объекта    

```ts
interface PaymentPersistent {
	id: number;
	sum: number;
	from: string;
	to: string;
}

/**
 * Omit<TYPE, 'fieldToOmit'>
 */

type Payment = Omit<PaymentPersistent, 'id'>;

/**
 * Payment
 * {
 * 	sum: number;
 *	from: string;
 *	to: string;
 * }
 */
```

##### Pick

Берет нужные свойства из объекта   

```ts
interface PaymentPersistent {
	id: number;
	sum: number;
	from: string;
	to: string;
}

/**
 * Pick<TYPE, 'fieldToPick'>
 */

type Payment = Pick<PaymentPersistent, 'id' | 'sum' >;

/**
 * Payment
 * {
 *	id: number;
 *	sum: number;
 * }
 */
```


##### Extract

Вытаскивает из union типа только необходимые свойства.   

```ts
interface PaymentPersistent {
	id: number;
	sum: number;
	from: string;
	to: string;
}

type ExtractPayment = Extract<'from' | 'to' | PaymentPersistent, string>

/*
ExtractPayment = "from" | "to"
*/
```

##### Exclude

Работает в обратную сторону от Extract.   

```ts
interface PaymentPersistent {
	id: number;
	sum: number;
	from: string;
	to: string;
}

type ExcludePayment = Exclude<'from' | 'to' | PaymentPersistent, string>

/*
ExcludePayment = PaymentPersistent
*/
```


#### ReturnType, Parameters, ConstructorParameters

```ts
class User {
    constructor(public id: number, public name: string) {}
}

function getData(id: number) {
    return new User(id, 'Alice');
}

type RT = ReturnType<typeof getData>;
type RT2 = ReturnType<() => void>;
type RT3 = ReturnType<<T>() => T>;
type RT4 = ReturnType<<T extends string>() => T>;

type PT = Parameters<typeof getData>;

type CP = ConstructorParameters<typeof User>;
```


#### Awaited

```ts
type A = Awaited<Promise<string>>;

interface IMenu {
    name: string;
    url: string;
}

async function getMenu(): Promise<IMenu[]> {
    return [{ name: 'Backend Dev', url: 'backend' }];
}

type R = Awaited<ReturnType<typeof getMenu>>; // IMenu[]

async function fetchArray<T>(x: T): Promise<Awaited<T>[]> {
    return [await x];
}
```