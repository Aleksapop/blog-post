---
title: "What is TypeScript? A Beginner’s Guide to Typed JavaScript"
date: "2025-03-20"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "JavaScript is the backbone of modern web development, powering everything from dynamic websites to complex web applications."
isFeatured: false
category: "Type Script"
---

How to Write and Use TypeScript Generic Functions: A Beginner's Guide
TypeScript is a powerful superset of JavaScript that adds static typing to the language. One of its most powerful features is Generics. With Generics, TypeScript allows you to write flexible and reusable functions, classes, and interfaces. In this post, we'll dive into TypeScript generic functions, explore how to write them and show you practical examples to help you level up your TypeScript skills

### What Are TypeScript Generics?

Generics in TypeScript are a powerful feature that allows you to write functions, classes, and interfaces that can work with multiple types. They enable you to create reusable, type-safe components without sacrificing flexibility. The key concept behind generics is to define a "placeholder" type that can be replaced with an actual type when calling the function, instantiating the class, or using the interface.

Instead of writing code tied to a specific type (e.g., only numbers or only strings), generics allow you to write code that can work with any type, ensuring that TypeScript's type system still enforces type safety. This means you can create more reusable and flexible code while avoiding the potential pitfalls of using `any`, which could lead to runtime errors.

#### Why Use Generics?

Generics provide several benefits:

1. **Reusability**: You can write a function or class once and use it with different types.
2. **Type Safety**: You still get the benefits of TypeScript's type system, ensuring that only valid types are used.
3. **Avoiding `any`**: With generics, you avoid using `any`, which would bypass the type system and could result in runtime errors.

#### Example 1: Generic Functions

Let's take a simple example of a function that returns the first element of an array:

```typescript
function getFirstElement<T>(arr: T[]): T {
  return arr[0];
}
```

In the above code:

- `T` is a **generic parameter**. It acts as a placeholder for any type.
- The function `getFirstElement` takes an array of type `T[]` (an array of elements of type `T`) and returns an element of type `T`.
- When you call this function, TypeScript will infer the type of `T` based on the argument you provide, but you can also explicitly specify the type if needed.

#### Example 2: Using Generics with Different Types

```typescript
const numberArray = [1, 2, 3];
const stringArray = ["apple", "banana", "cherry"];

const firstNumber = getFirstElement(numberArray); // Type is inferred as number
const firstString = getFirstElement(stringArray); // Type is inferred as string
```

- In this example, `getFirstElement` is used with two different types: `number[]` and `string[]`. TypeScript infers the correct type based on the array passed in.

#### Generic Constraints

Sometimes, you can restrict the types used with a generic function. For instance, you may only want to allow types with a `.length` property (like arrays or strings).

You can apply a **constraint** to a generic parameter:

```typescript
function logLength<T extends { length: number }>(value: T): void {
  console.log(value.length);
}
```

In the above code:

- The generic parameter `T` is constrained to types with a `length` property. This means `T` can only be types like `string`, `array`, or other objects with a `length` property.
- The function logs the length of `value` to the console, but TypeScript ensures that only types with a `.length` property can be used.

#### Example with Constraints

```typescript
logLength([1, 2, 3]); // OK, array has a length property
logLength("Hello!"); // OK, string has a length property
logLength(123); // Error: number doesn't have a length property
```

#### Generic Interfaces and Classes

You can also use generics with interfaces and classes to create more flexible, reusable components.

##### Generic Interface

```typescript
interface Box<T> {
  value: T;
}

const stringBox: Box<string> = { value: "Hello" };
const numberBox: Box<number> = { value: 42 };
```

In this example, the `Box` interface is generic, allowing you to define a `Box` with a value of any type (e.g., `string` or `number`).

##### Generic Class

```typescript
class Queue<T> {
  private items: T[] = [];

  enqueue(item: T): void {
    this.items.push(item);
  }

  dequeue(): T | undefined {
    return this.items.shift();
  }
}

const stringQueue = new Queue<string>();
stringQueue.enqueue("item1");
const item = stringQueue.dequeue(); // inferred as string
```

Here, the `Queue` class is generic. The type `T` allows the class to hold any items andntains type safety while enqueuing and dequeuing items. Conclusion

Generics in TypeScript are an essential feature for writing reusable, type-safe code. They allow you to work with different types while ensuring that the benefits of the type system are preserved. Using generic functions, classes, and interfaces, you can create highly flexible and robust code that works across multiple data types while avoiding the pitfalls of using `any`.

### Why Use Generics in TypeScript?

Generics in TypeScript are powerful tools that enhance code flexibility while preserving type safety. Here’s a deeper look into why you should use generics in your TypeScript code:

#### 1. **Reusability**

Generics allow you to write a function or class once and use it with multiple data types. This is particularly useful when you have similar logic that can apply to different types but don't want to duplicate code for each. With generics, you can create reusable components that handle any data type, without losing type safety.

**Example:**

```typescript
function identity<T>(value: T): T {
  return value;
}

const number = identity(42); // T inferred as number
const string = identity("hello"); // T inferred as string
```

In this case, the `identity` function is generic and works with numbers and strings, demonstrating its reusability.

#### 2. **Type Safety**

Even though generics allow flexibility by working with dynamic types, they still provide type safety. TypeScript will enforce that the types used in your generic functions or classes are consistent, ensuring you avoid type errors and potential bugs.

For example:

```typescript
function wrapInArray<T>(value: T): T[] {
  return [value];
}

let stringArray = wrapInArray("hello"); // Type of stringArray is string[]
let numberArray = wrapInArray(100); // Type of numberArray is number[]
```

In this example, TypeScript infers that `wrapInArray` returns an array of the same type as the argument passed. If you try to mix types, TypeScript will raise an error.

#### 3. **Improved Readability**

Generics improve readability because they make the code's intentions more explicit. Instead of seeing `any` (which could be anything) or having complex overloads, you can use meaningful type variables that explicitly state what types are expected. This makes it easier to understand the function or class, as it clarifies how the types are used and ensures they are consistent across the code.

**Example:**

```typescript
function merge<T, U>(object1: T, object2: U): T & U {
  return { ...object1, ...object2 };
}

const mergedObject = merge({ name: "Alice" }, { age: 30 });
```

Here, the intention is clear: `merge` takes two objects, possibly of different types, and combines them into a single object of both types (`T & U`). This approach clarifies how the function behaves and what types it expects.

### Summary

Generics are essential in TypeScript to enhance reusability, ensure type safety, and improve readability. You can write more maintainable, scalable, and error-free code using generics while allowing flexibility to work with various data types.

### How to Write and Use TypeScript Generic Functions

TypeScript generics are a powerful way to create reusable, type-safe functions and components. They allow you to define functions that can work with any data type while maintaining strict type checks.

Let's dive deeper into the steps for writing and using generic functions in TypeScript.

---

### Step 1: Declare the Generic Type

In TypeScript, a **generic type** is declared using angle brackets (`<T>`) following the function name. `T` is a placeholder representing any type that will be determined when the function is used. The letter `T` is commonly used, but you can name it anything you like (such as `U`, `K`, etc.).

Here’s an example of declaring a simple generic function:

```typescript
function myGenericFunction<T>(arg: T): T {
  return arg;
}
```

**Explanation**:

- `<T>`: Declares a generic parameter `T`. This is a placeholder for any type (like `number`, `string`, etc.).
- `(arg: T)`: The function parameter `arg` has the type `T`, so it can accept a value of any type.
- `: T`: The return type of the function is also of type `T`, meaning it will return whatever type is passed in.

**What this means**: This function can accept and return any type if the type passed in is consistent. For example, if you pass a `number`, it will return a `number`.

---

### Step 2: Using the Generic Function

TypeScript can automatically infer the type for `T` when calling the generic function based on your argument. Alternatively, you can specify the type for `T` if needed.

#### Example of type inference

```typescript
const result = myGenericFunction(42);  // inferred type is number
const resultString = myGenericFunction("Hello, TypeScript!");  // inferred type is string
```

**Explanation**:

- In the first example, TypeScript sees that `42` is a `number,` so it infers that `T` is a `number.`
In the second example, TypeScript sees that `"Hello, TypeScript!` is a `string` and infers that `T` is a `string`.

TypeScript automatically determines the type based on the argument passed in, but you can also explicitly specify the type if needed.

#### Explicit type definition

```typescript
const result = myGenericFunction<number>(42);  // T is explicitly set to number
const resultString = myGenericFunction<string>("Hello, TypeScript!");  // T is explicitly set to string
```

---

### Step 3: Using Generics with Multiple Parameters

Using multiple generic parameters, you can extend generic functions to handle more than one type. This is useful when your function works with more than one type of input or output.

#### Example with multiple generics

```typescript
function merge<T, U>(obj1: T, obj2: U): T & U {
  return { ...obj1, ...obj2 };
}

const result = merge({ name: "John" }, { age: 30 });
console.log(result); // { name: 'John', age: 30 }
```

**Explanation**:

- `T` represents the type of the first object (`{ name: "John" }`).
- `U` represents the type of the second object (`{ age: 30 }`).
- `T & U`: The return type `T & U` means that the function returns an object containing properties from both `T` and `U`. This is a **union** type combining both objects.

In the above example, the merged object will have properties from input objects (`name` from `T` and `age` from `U`).

---

### Step 4: Working with Default Generics

TypeScript also allows you to specify a default type for generics. This default is used if the user explicitly provides no type when the function is called.

#### Example with default generic

```typescript
function identity<T = string>(value: T): T {
  return value;
}

const numberResult = identity(123);  // Inferred as number
const stringResult = identity("Hello");  // Inferred as string
const defaultResult = identity();  // Uses default type, string
```

**Explanation**:

- `T = string`: This sets `string` as the default type for `T` if no type is specified.
- If `identity()` is called without an argument, `T` defaults to `string`.
- If an argument is passed (like `123` or `"Hello"`), TypeScript infers the correct type for `T`.

This is useful for functions where a common type is expected but you still want flexibility.

---

Summary

- **Generics** make functions reusable by allowing them to handle multiple types while keeping type safety.
- You declare generics with `T` (or any identifier) inside angle brackets `<T>`.
- You can use **type inference** to determine the type based on the argument passed automatically, or **explicitly specify** the type when calling the function.
- You can create **multi-parameter generics** to work with functions that involve multiple types, and use **default types** to set a fallback when no type is provided.

Generics make your code more flexible and type-safe by enforcing rules about what types can be passed and returned.

### Practical Examples of TypeScript Generic Functions

In TypeScript, **generics** allow you to write functions and classes that work with any data type while preserving the type information. This means you can create reusable and type-safe code.

Here are two practical examples of TypeScript generic functions:

---

#### **Example 1: Generic Function to Return the First Element of an Array**

In this example, the function `getFirstElement` takes an array of any type `T[]` and returns the first element of that array. The function signature ensures that the type of the input array (`T[]`) and the type of the returned element (`T`) are consistent.

```typescript
function getFirstElement<T>(arr: T[]): T {
  return arr[0];
}

const firstNumber = getFirstElement([1, 2, 3]);  // Type inferred as number, value: 1
const firstString = getFirstElement(["apple", "banana", "cherry"]);  // Type inferred as string, value: "apple"
```

- **How it works**:
  - The `<T>` in the function signature tells TypeScript that this function is generic and can work with any array (`T[]`).
  - TypeScript automatically infers the type when calling the function based on the argument passed in, but you can also explicitly specify the type.
  - The return type `T` ensures that whatever type the array holds, the first element will be returned with that same type.

---

#### **Example 2: Generic Function to Count the Number of Items in an Array**

This function, `getArrayLength,` is another generic function that works with any array and returns the array's length, regardless of the type of elements inside the array. The length is always of type `number`.

```typescript
function getArrayLength<T>(arr: T[]): number {
  return arr.length;
}

const numberCount = getArrayLength([1, 2, 3]);  // 3
const stringCount = getArrayLength(["a", "b", "c", "d"]);  // 4
```

- **How it works**:
  - Like the previous example, the function accepts an array of any type `T[]`.
  - The return type is always `number`, representing the array's length.
  - This function works for any array type (numbers, strings, objects, etc.), but the return type will always be a `number`, since it represents the length of the array.

---

### Key Points About Generic Functions in TypeScript

1. **Type Parameter (`<T>`)**:
   - The `<T>` part is called a **type parameter** and acts as a placeholder for a specific type that will be provided when the function is used.
   - You can use any name for the type parameter, but `T` is commonly used (short for **Type**).

2. **Type Inference**:
   - TypeScript can often **infer** the type of the parameter based on how the function is used. For example, in `getFirstElement([1, 2, 3])`, TypeScript automatically infers that `T` is `number` because the array contains numbers.

3. **Type Safety**:
   - Using generics ensures that the function maintains type safety. It guarantees that you won’t accidentally return the wrong type, which would happen if the function were not generic.

4. **Reusability**:
   - Generic functions are reusable for different types of data. You don’t need to write separate functions for each type (e.g., one for arrays of numbers and one for strings).

In TypeScript, generics provide a powerful way to write flexible, reusable, and type-safe functions, classes, and interfaces. Here are some best practices for using generics effectively:

### 1. **Use Descriptive Type Parameters**

While the placeholder `T` is commonly used for type parameters, using more descriptive names improves readability and maintainability. By using descriptive type names such as `TItem`, `TKey`, `TValue`, or `TResponse`, you make the code more self-documenting, making it easier for others (and your future self) to understand the purpose of each type.

**Example:**

```typescript
function getItem<TItem>(item: TItem): TItem {
  return item;
}
```

In this example, `TItem` clearly indicates that the function deals with an item, improving readability compared to just using `T`.

### 2. **Don’t Overuse Generics**

Generics are an excellent tool for making your code flexible and reusable, but they should only be used when necessary. Overusing generics can lead to more complex and difficult-to-follow code. If a function only needs to work with a specific type, it's better to use that type explicitly rather than try to use a generic type.

**Example:**
If your function only works with numbers, don't use a generic. Instead, directly specify the type:

```typescript
function addNumbers(a: number, b: number): number {
  return a + b;
}
```

This is simpler and clearer than introducing generics unnecessarily.

### 3. **Leverage Constraints with Generics**

Generics can be constrained only to accept types that extend a particular interface or class, which increases type safety. This ensures that you only work with types that meet certain conditions, avoiding potential runtime errors.

**Example:**
Here’s how you can constrain a generic only to accept types that extend the `Person` interface:

```typescript
interface Person {
  name: string;
  age: number;
}

function printName<T extends Person>(person: T): void {
  console.log(person.name);
}

printName({ name: "John", age: 30 });  // Works fine
```

In this case, the function `printName` only accepts objects of types that extend `Person`, ensuring that the `person` argument always has a `name` property (and any other properties defined in `Person`). This provides better safety, as TypeScript will give an error if you try to pass an object that doesn't conform to the `Person` interface.

### Summary of Best Practices

- **Use descriptive type names** to improve readability (e.g., `TItem` instead of `T`).
- **Avoid overusing generics** when they aren't necessary; use specific types for simplicity and clarity.
- **Leverage constraints** to limit the types a generic function can accept, improving type safety.

These practices make your TypeScript code more maintainable, understandable, and safer.
Conclusion
Generics are one of the most powerful features of TypeScript, enabling you to write more flexible, reusable, and type-safe code. Using generics in functions allows you to create code that works with multiple types while maintaining strong typing. Whether working on a large-scale application or experimenting with TypeScript, mastering generics will significantly improve your coding experience.

Happy coding!

\*\* Book Recommendation:

- [React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
- [React Key Concepts](https://amzn.to/43XOCJM)
- [Pragmatic Programmer](https://amzn.to/3W1P4oL) **_The: Your journey to mastery, 20th Anniversary Edition_**

[Mentorship & Consulting - Contact us for more info](/contact)

**_Join Our Discord Community_** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

**_For Consulting and Mentorship, feel free to contact_** [slavo.io](/contact)
