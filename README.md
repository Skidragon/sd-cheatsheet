
## Typescript
- https://github.com/type-challenges/type-challenges
- https://medium.com/free-code-camp/typescript-curry-ramda-types-f747e99744ab
```ts

type Awaited<T extends Promise<any>> = T extends Promise<infer R> ? R : never;

type Concat<A extends any[], B extends any[]> = [...A, ...B];

type Drop<N extends number, T extends any[], I extends any[] = []> = {
    0: Drop<N, Tail<T>, Prepend<any, I>>
    1: T
}[ Length<T> extends N ? 1 : 0]

type If<C extends boolean, T, F> = C extends true ? T : F;

type First<T extends any[]> = T extends [any, ...any] : T[0] : never;

type HasTail<T extends any[]> = T extends ([] | [any]) ? false : true;

type Includes<T extends readonly any[], U> = {
  [P in T[number]]: true
}[U] extends true ? true : false;


type Last<T extends any[]> = {
    0: Last<Tail<T>>
    1: Head<T>
}[HasTail<T> extends true ? 1 : 0];

type Omit<T, K extends keyof T> = {
  [P in Exclude<keyof T, K>]: T[P];
}

type Tail<T extends any[]> = ((...t: T) => any) extends ((_: any, ...tail: infer TT) => any) ? TT : [];

type TupleLength<T extends readonly any[]> = T['length'];

type TupleToObject<T extends readonly any[]> = {
  [P in T[number]]: P;
}

type Return<T extends (...args: any) => any> = T extends (...args: any) => infer R ? R : any;

```
