# Advent of TypeScript 2023 Solutions

My solutions for advent of typescript 2023 on [https://typehero.dev](https://typehero.dev). Will be updating as I go along.

### Day 1

```ts
type SantasFavoriteCookies = 'ginger-bread' | 'chocolate-chip';
```

### Day 2

```ts
type CookieSurveyInput<T extends Object> = keyof T;
```

### Day 3

```ts
type GiftWrapper<First, Second, Third> = {
  present: First;
  from: Second;
  to: Third;
}
```

### Day 4

```ts
type Address = { address: string; city: string };
type PresentDeliveryList<T extends Object> = {[K in keyof T]: Address};
```

### Day 5

```ts
type SantasList<Bad extends readonly unknown[], Good extends readonly unknown[]> = 
  [...Bad, ...Good]
```

### Day 6

```ts
type FilterChildrenBy<T, U> = T extends U ? never : T;
```

### Day 7

```ts
type AppendGood<T extends Record<string, unknown>> = {
	[K in keyof T & string as `good_${K}`]: T[K];
} 
```

### Day 8

```ts
type RemoveNaughtyChildren<T extends Object> = {
	[K in keyof T as K extends string & `naughty_${string}` ?  never: K]: T[K];
};
```

### Day 9

```ts
type Reverse<T extends string> = T extends `${infer First}${infer Rest}` 
  ? `${Reverse<Rest>}${First}` 
  : T;
```

### Day 10

```ts
type StreetSuffixTester<T extends string, U extends string> = T extends `${infer Rest}${U}` 
  ? true 
  : false;
```

### Day 11

```ts
type SantaListProtector<T extends Record<string, any>> = {
	readonly [K in keyof T]: T[K] extends Function 
		?	T[K]
		: T[K] extends Record<any, any> 
			? SantaListProtector<T[K]> 
			: T[K]
}
```

### Day 12

```ts
type FindSanta<T extends string[]> = T extends [...infer Rest extends string[], infer Last] 
	? Last extends "🎅🏼"
		? Rest['length']
		: FindSanta<Rest>
	: never;
```
