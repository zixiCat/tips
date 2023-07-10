- You can the following formula to transform union type to intersection type, but don't think it's possible when in the opposite direction.
  ```typescript
  type UnionToIntersection<U> = (U extends any ? (k: U)=>void : never) extends ((k: infer I)=>void) ? I : never
  ```
- You can extract the property name which value is of function type
  ```typescript
  type TFnPropertyNames<T> = { [K in keyof T]: T[K] extends Function ? K : never }[keyof T]
  ```
- If you'd like to set the type of class anyway, you can try this: `type Class<T = any> = new (...args: any[]) => T;`
- If you'd like to the interface that require only one of two property, try this:
  ```typescript
  type RequireOnlyOne<T, Keys extends keyof T = keyof T> = Pick<
    T,
    Exclude<keyof T, Keys>
  > &
    {
      [K in Keys]-?: Required<Pick<T, K>> &
        Partial<Record<Exclude<Keys, K>, undefined>>;
    }[Keys];
  ```
- 6 ways to narrow types in TypeScript...[ref](https://www.carlrippon.com/6-ways-to-narrow-types-in-typescript/)
  - using a conditional value check to remove `null` and `undefined` from a type
  - using `typeof` function to narrow the type to primitive types
  - using `instanceof` function to narrow the type to class types
  - using `in` function to determine if the type is in the object
  - using type predicates to narrow to some complex type you want
  - using `assert` function to narrow to some complex type if you wan throw some errors

- An excellent way to simplify the type `TUnitTransform`, it's related to several key points...[ref](https://stackoverflow.com/questions/65850619/is-there-an-function-to-simplify-the-following-union-type-tunittransform)
  ```typescript
  type TUnitTransform = ((...rest: [number]) => [number]) &
    ((...rest: [number, number]) => [number, number]) &
    ((...rest: [number, number, number]) => [number, number, number]) &
    ......

  type TUnitTransform = 
    <T extends [number, ...number[]]>(...rest: [...T]) => { [K in keyof T]: number; }
  ```

- The diffs among typescript properties of class...[ref](https://gist.github.com/zixiCat/edd02052a1bfa8ad14268b26b6c9d086)