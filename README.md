# learn-ts

// keyof
type MyPartial<T> = { [P in keyof T]?: T[P]}
type MyRequire<T> = { [P in keyof T]-?: T[P]}
type MyReadonly<T> = { readonly [P in keyof T]: T[P]}
type MyPick<T, K extends keyof T> = { [P in K]: T[P]}

type MyRecord<K extends string | number | symbol, T> = { [P in K]: T }

// 条件类型  T extends U ？never : T
// T如果是联合类型 A | B的话，会被分解程 (A extends U ? never : T) | (B extends U ? never : T)
type MyExclude<T, U> = T extends U ? never : T
type MyExtract<T, U> = T extends U ? T : never

// keyof 和 条件类型一起使用的效果
type MyOmit<T, K> = MyPick<T, MyExtract<keyof T, K>>

// infer 条件类型的extends子语句中，允许出现infer声明,这个推断的类型变量可以在条件类型的true分支中被引用
type MyReturnType<T> = T extends (...args: any[]) => infer U ? U : any
