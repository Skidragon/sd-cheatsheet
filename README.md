
## Typescript
```ts

type Awaited<T extends Promise<any>> = T extends Promise<infer R> ? R : never;

type Concat<A,B> = [...A, ...B];

type If<C extends boolean, T, F> = C extends true ? T : F;

type First<T extends any[]> = T extends [any, ...any] : T[0] : never;

type HasTail<T extends any[]> = T extends ([] | [any]) ? false : true;

type Includes<T extends readonly any[], U> = {
  [P in T[number]]: true
}[U] extends true ? true : false;


type Last<T extends any[]> = {
    0: Last<Tail<T>>,
    1: Head<T>
}[HasTail<T> extends true ? 1 : 0];

type Omit<T, K extends keyof T> = {
  [P in Exclude<keyof T, K>]: T[P];
}

type Tail<T extends any[]> = ((...t: T) => any) extends ((_: any, ...tail: infer TT) => any) ? TT : [];

type TupleLength<T extends readonly any[]> = T['length'];

type Return<T extends (...args: any) => any> = T extends (...args: any) => infer R ? R : any;

```