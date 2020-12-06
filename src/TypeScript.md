- You can the following formula to transform union type to intersection type, but don't think it's possible when in the opposite direction.
  ```typescript
  type UnionToIntersection<U> = (U extends any ? (k: U)=>void : never) extends ((k: infer I)=>void) ? I : never
  ```
- You can extract the property name which value is of function type
  ```typescript
  type TFnPropertyNames<T> = { [K in keyof T]: T[K] extends Function ? K : never }[keyof T]
  ``` 
- If you'd like to set the type of class anyway, you can try this: `type Class<T = any> = new (...args: any[]) => T;` 

