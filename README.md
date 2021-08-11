
## Typescript
- https://github.com/type-challenges/type-challenges
- https://medium.com/free-code-camp/typescript-curry-ramda-types-f747e99744ab
- https://typescript-exercises.github.io/#exercise=1&file=%2Findex.ts
```ts

type Awaited<T extends Promise<any>> = T extends Promise<infer R> ? R : never;

type Chainable<T = {}> = {
  option<K extends string, V>(key: K extends keyof T ? never: K, value: V): Chainable<T & { [key in K]: V }>;
  get(): T
}

type Concat<A extends any[], B extends any[]> = [...A, ...B];

type Drop<N extends number, T extends any[], I extends any[] = []> = {
    0: Drop<N, Tail<T>, Prepend<any, I>>
    1: T
}[ Length<T> extends N ? 1 : 0]

type If<C extends boolean, T, F> = C extends true ? T : F;

type First<T extends any[]> = T extends [any, ...any] : T[0] : never;

type HasTail<T extends any[]> = T extends ([] | [any]) ? false : true;

type PickReadonly<T, K extends keyof T = keyof T> = {
  readonly [P in K]: T[P];
} & {
  [P in Exclude<keyof T, K>]: T[P];
}

type DeepReadonly<T> = keyof T extends never ? T : {
  readonly [P in keyof T]: DeepReadonly<T[P]>;
} 

type Includes<T extends readonly any[], U> = {
  [P in T[number]]: true
}[U] extends true ? true : false;


type Last<T extends any[]> = {
    0: Last<Tail<T>>
    1: Head<T>
}[HasTail<T> extends true ? 1 : 0];

//type Dog = { type: 'dog', sound: 'woof' }
//type Cat = { type: 'cat', sound: 'meow' }v
//type Animal = Dog | Cat; 
//LookUp<Animal, 'dog'> should be type Dog
type LookUp<U extends { type: string; }, T extends string> = U extends { type: T } ? U : never;

type Omit<T, K extends keyof T> = {
  [P in Exclude<keyof T, K>]: T[P];
}

type Pop<T extends any[]> = T extends [...infer L, any] ? L : [];

type Push<T extends any[], E> = [...T, E];

type Shift<T extends any[]> = T extends [any, ...infer R] ? R : [];

type Tail<T extends any[]> = ((...t: T) => any) extends ((_: any, ...tail: infer TT) => any) ? TT : [];

type WhiteSpace = ' ' | '\t'  | '\n';
type TrimLeft<S extends string> = S extends `${WhiteSpace}${infer R}` ? TrimLeft<R> : S;

type TupleLength<T extends readonly any[]> = T['length'];

type TupleToObject<T extends readonly any[]> = {
  [P in T[number]]: P;
}

type TupleToUnion<T extends any[]> = T[number];

type Return<T extends (...args: any) => any> = T extends (...args: any) => infer R ? R : any;


type Unshift<T extends any[], E> = [E, ...T];

//declare global & modules
declare global {
  namespace NodeJS {
    interface ProcessEnv {
      GRAPHCMS_CONTENT_ENDPOINT: string;
      GRAPHCMS_AUTH_TOKEN: string;
      GRAPHCMS_MUTATION_TOKEN: string;
      FIREBASE_SERVICE_ACCOUNT_PRIVATE_KEY: string;
      FIREBASE_SERVICE_ACCOUNT_PRIVATE_KEY_ID: string;
      STRIPE_SECRET_KEY: string;
      NODE_ENV: 'development' | 'production';
      PORT?: string;
      PWD: string;
    }
  }
}
declare module 'str-utils' {
    export function strReverse(value: string): string;
    export function strToLower(value: string): string;
    export function  strToUpper(value: string): string;
    export function strRandomize(value: string): string;
    export function strInvertCase(value: string): string;
}
declare module 'stats' {
    type Comparator = (a: string, b: string) => number;
    type StatsUtil = (input: string, comparator: (input1: string, input2: string) => boolean) => number;
    export const getMaxIndex: StatsUtil;
    export const getMinIndex: StatsUtil;
    export const getMaxElement: StatsUtil;
    export const getMinElement: StatsUtil;
    export const getMedianIndex: StatsUtil;
    export const getMedianElement: StatsUtil;
    export const getAverageValue: StatsUtil;
}

```

## CSS
- Resources:
- https://thecsspodcast.libsyn.com/#
- https://cssreference.io/
```css
/* Create an animated underline for a link or text that goes across multiple lines */
.animated-text-underline {
  background-image: linear-gradient(90deg, red, blue);
  /* The height of the underline */
  background-size: 0% 3px;
  /* background-repeat keeps the background from covering the height of the text*/
  background-repeat: no-repeat;
  /* position at the left bottom of the first character */
  background-position: left bottom;
  transition: background-size 300ms ease;
}
.animated-text-underline:hover {
  background-size: 100% 3px;
}

.gradient-text {
  background-image: linear-gradient(90deg, red, blue);
  background-clip: text;
  color: transparent;
}

/* animation: name duration timing-function delay iteration-count direction */
.spin {
  animation: spin 1s ease 500ms infinite alternate;
}
/* feature query */
.title {
@supports (background-clip: text) {
    color: transparent;
    background-clip: text;
    background-image: radial-gradient(
      128.88% 128.88% at 103.9% -10.39%,
      #e84d70 0%,
      #a337f6 53.09%,
      #28a7ed 100%
    );
  }
}

```

## NX

```nx
nx g @nrwl/workspace:remove
```