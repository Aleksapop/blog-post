---
title: "What is TypeScript? A Beginner’s Guide to Typed JavaScript"
date: "2025-03-20"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "JavaScript is the backbone of modern web development, powering everything from dynamic websites to complex web applications."
isFeatured: false
category: "Type Script"
---

Advanced TypeScript Type Guards: Writing Safer Code
TypeScript is a powerful language that offers static typing on top of JavaScript, helping developers catch errors early in development. However, ensuring type safety can become a challenge as complex projects grow. One of TypeScript's most powerful features to help with this is type guards.
In this blog post, we’ll dive deep into advanced TypeScript type guards, how they work, and how they can help you write safer, more maintainable code. Whether new to type guards or an experienced developer, this post will help you level up your TypeScript skills.

### What Are Type Guards?

Type Guards tell TypeScript to treat a variable as a specific type within a scope. They enable more precise type inference by evaluating certain conditions and refining the type of a variable based on those conditions. This is particularly useful when dealing with variables that have union types, where you may want to handle different kinds differently in various parts of the code.

For instance, if a variable could be a `string` or a `number`, TypeScript needs to know which type to expect to perform safe operations (like calling string methods or performing arithmetic). Type Guards help you do this.

### How Do Type Guards Work?

A **Type Guard function** is typically a function that checks a specific condition (like `typeof` or `instanceof`) and narrows down the type of the variable based on that condition.

One of the most common ways to create a Type Guard is by using the `value is Type` syntax. This tells TypeScript that the function will narrow the type of the given value.

#### Example: `isString` Type Guard

Here’s a simple example of how Type Guards work in TypeScript:

```typescript
function isString(value: any): value is string {
  return typeof value === "string";
}

function printLength(value: string | number) {
  if (isString(value)) {
    // TypeScript knows 'value' is a string here
    console.log(value.length);
  } else {
    // 'value' is a number here
    console.log(value.toString().length);
  }
}
```

In this example:

- The `isString` function checks whether a given `value` is a string.
- The function `isString(value)` serves as a Type Guard. It returns a `value is string` type, signaling to TypeScript that the type of `value` should be considered a string within the' if' block. This enables the use of string-specific methods, like `.length`.
- In the `else` block, TypeScript understands that `value` must be a number, since `isString(value)` returned `false`.

By using Type Guards, we make sure that TypeScript understands the type of `value` in each branch of the code, allowing for better type safety and preventing runtime errors.

### Benefits of Type Guards

1. **Safety:** Type Guards help avoid potential errors by ensuring only valid operations are performed on variables. For example, trying to access `.length` on a `number` would lead to a mistake, but with Type Guards, TypeScript ensures the variable is a string before such operations are allowed.

2. **Refined Type Inference:** TypeScript will infer the exact type within the scope of the condition, which means you can take advantage of specific methods or properties associated with that type.

3. **Better Readability and Maintainability:** By explicitly stating the type checks, Type Guards make the code more transparent to other developers, as the types are narrowed down explicitly.

### Advanced Type Guards

You can also define more complex Type Guards, especially when dealing with objects, classes, or more intricate conditions.

Example with **Instanceof** Type Guard:

```typescript
class Dog {
  bark() {
    console.log("Woof!");
  }
}

class Cat {
  meow() {
    console.log("Meow!");
  }
}

function isDog(animal: Dog | Cat): animal is Dog {
  return animal instance Dog;
}

function makeSound(animal: Dog | Cat) {
  if (isDog(animal)) {
    animal.bark(); // We are sure 'animal' is a Dog here
  } else {
    animal.meow(); // 'animal' must be a Cat
  }
}
```

In this example, the `isDog` function is a Type Guard that checks if the `animal` is an instance of the `Dog` class. This allows TypeScript to narrow down the type of `animal` within the conditional blocks.

### Conclusion

Type Guards in TypeScript are crucial for writing safe, type-safe code, especially when dealing with union types or complex type checks. They allow TypeScript to infer and narrow down types based on certain conditions, ensuring that only appropriate operations are performed. By leveraging Type Guards, you can improve the robustness and maintainability of your codebase, reducing the risk of errors and making your code easier to understand.

### 1. **Preventing Runtime Errors from Null or Undefined**

One of the most common issues in JavaScript (and TypeScript to an extent) is working with `null` or `undefined` values. Without proper type guards, the TypeScript compiler may allow variables to potentially have a `null` or `undefined` value, leading to errors when accessing properties or methods on these variables. By using advanced type guards, you can explicitly check for `null` and `undefined` values, ensuring that your code doesn’t attempt operations on them. This avoids runtime errors that might otherwise occur.

### 2. **Safely Working with Union Types**

Union types are consequential in TypeScript, allowing a variable to be one of several types (e.g., `string | number`). However, union types introduce the need for checks to determine which type the variable is at runtime. Advanced type guards make it easier to safely discriminate between the different types in a union, allowing you to handle each type appropriately. For example, when dealing with a `string | number` union, an advanced type guard will help TypeScript narrow the type to `string` or `number` based on specific checks, preventing mistakes and ensuring that operations are only performed on valid types.

### 3. **Handling Intersection Types**

Intersection types combine multiple types, requiring all the properties of each kind. With advanced type guards, you can narrow down intersection types by checking the presence of properties from all constituent types. This enables safer manipulation of complex objects with different behaviors depending on their components, helping developers work with these intricate structures without risking runtime failures due to missing or incompatible properties.

### 4. **Working with Literal Types**

Literal types in TypeScript allow variables to take on specific, predefined values (e.g., `let status: 'active' | 'inactive'`). Advanced type guards enable precise checks for these values, clarifying what specific value a variable can take and ensuring that actions can be taken based on that value. This type of narrowing avoids potential misinterpretations of values and makes your code more predictable and robust.

### 5. **Improving Readability and Maintainability**

Advanced type guards make type assertions explicit, improving the code's readability and maintainability. Instead of relying on implicit behavior, you can write clear checks to anyone reading the code. This also reduces ambiguity in complex codebases, where different types may be passed around, and ensures that any future developers (or yourself) will clearly understand the type handling in place.

By leveraging advanced type guards, developers can write more predictable and type-safe code, preventing errors arising from incorrect assumptions about types. These guards are handy when working with more complex scenarios, ensuring that TypeScript's powerful type system is fully utilized to catch issues early in development.

### Advanced TypeScript Type Guards: Writing Safer Code

TypeScript guards are critical for ensuring the safe handling of various types in your code, preventing runtime errors, and making your codebase more predictable. While essential type guards like `type` and `instance of` are widely used, you can further apply several advanced techniques to enhance your code's safety and maintainability. Let's dive into some of the advanced types of type guards in TypeScript.

#### 1. **User-Defined Type Guards**

User-defined type guards (UDTGs) offer the most flexibility and power. By defining a custom function that returns a type predicate (`value is Type`), you can inform TypeScript about the specific variable type, allowing it to narrow types more precisely than the built-in guards.

##### Example: Narrowing to Specific Interface Types

In this example, you want to differentiate between `Circle` and `Square` types within a `Shape` union type. The function `isCircle` acts as a type guard that helps TypeScript narrow down the type to a `Circle` inside the conditional block:

```typescript
interface Circle {
  kind: 'circle';
  radius: number;
}

interface Square {
  kind: 'square';
  size: number;
}

type Shape = Circle | Square;

function isCircle(shape: Shape): shape is Circle {
  return shape.kind === 'circle';
}

function calculateArea(shape: Shape) {
  if (isCircle(shape)) {
    return Math.PI * shape.radius ** 2;
  } else {
    return shape.size ** 2;
  }
}
```

Here, the `isCircle` function is a user-defined type guard that checks the `kind` property of `shape`, thereby narrowing the type of `shape` to `Circle` if the check passes.

#### 2. **In-Built Type Guards**

TypeScript provides built-in type guards that automatically narrow types for everyday use cases. These include:

- **`typeof`**: Used to check primitive types like `string`, `number`, etc.
- **`instanceof`**: Used to check if an object is an instance of a class.
- Checking for **null** or **undefined**.

##### Example: Using `typeof`

The `typeof` operator is useful for narrowing primitive types, such as checking if a value is a `number` or `string`:

```typescript
function isNumber(value: any): value is number {
  return typeof value === 'number';
}

function print(value: string | number) {
  if (isNumber(value)) {
    console.log(value.toFixed(2)); // `value` is inferred as a number
  } else {
    console.log(value.toUpperCase()); // `value` is inferred as a string
  }
}
```

##### Example: Using `instanceof`

The `instanceof` operator is handy when you need to check if an object is an instance of a specific class, allowing you to narrow the type:

```typescript
class Dog {
  bark() {
    console.log("Woof!");
  }
}

class Cat {
  meow() {
    console.log("Meow!");
  }
}

function isDog(animal: any): animal is Dog {
  return animal instanceof Dog;
}

function makeSound(animal: Dog | Cat) {
  if (isDog(animal)) {
    animal.bark();
  } else {
    animal.meow();
  }
}
```

#### 3. **Custom Type Guards with `in` Operator**

You can also use the `in` operator to check for the presence of a property in an object. This is especially useful when working with objects of different types that share some common properties.

##### Example: Using `in` Operator

In this example, the `hasRadius` function checks if a given object has a `radius` property, which is specific to `Circle` objects:

```typescript
function hasRadius(shape: any): shape is { radius: number } {
  return 'radius' in shape;
}

function describeShape(shape: any) {
  if (hasRadius(shape)) {
    console.log(`Circle with radius: ${shape.radius}`);
  } else {
    console.log("Not a circle.");
  }
}
```

Here, the `hasRadius` function acts as a type guard, helping TypeScript understand that if `shape` has a `radius` property, it must be a `Circle`.

#### 4. **Using `never` Type for Exhaustive Checks**

The `never` type is useful in scenarios where you want to ensure that all possible union-type cases are covered. By using `never` in a switch-case or similar structure, TypeScript will raise an error if any case is not handled, helping you catch missing cases at compile time.

##### Example: Exhaustive Check with `never`

In this example, we use a union type `Shape` and a switch statement to calculate the area of different shapes. By assigning `shape` to a `never` variable in the default case, TypeScript ensures that if a new shape type is added and not handled, it will raise an error.

```typescript
type Shape = 'circle' | 'square' | 'triangle';

function getArea(shape: Shape) {
  switch (shape) {
    case 'circle':
      return Math.PI * 5 ** 2;
    case 'square':
      return 5 * 5;
    default:
      // The 'never' type ensures all cases are covered
      const _exhaustiveCheck: never = shape;
      return _exhaustiveCheck; 
  }
}
```

The `never` type here guarantees that if any new type is added to `Shape`, TypeScript will trigger a compile-time error, ensuring that all cases are explicitly handled.

---

Conclusion

Mastering these advanced type guards in TypeScript allows you to write more type-safe, maintainable, and predictable code. Custom user-defined type guards control narrowing types, while built-in guards (`typeof`, `instanceof`) and the `in` operator provide essential tools for everyday use. The `never` type ensures that your code is always up to date and exhaustive, preventing future bugs and making your type handling even safer.

### Best Practices for Writing Type Guards in Advanced TypeScript

When working with **TypeScript**'s type guards, following certain best practices to ensure your code is safe and maintainable is crucial. Here’s a breakdown of some essential practices:

#### 1. **Leverage Value is Type Syntax**

When writing a type guard, you want to ensure that TypeScript can narrow down the type appropriately based on your logic. TypeScript allows you to use the `value is Type` syntax for custom type guards. This helps TypeScript understand that the variable has been narrowed to a specific type after the guard check.

For example:

```typescript
function isString(value: unknown): value is string {
    return typeof value === 'string';
}

function processValue(value: unknown) {
    if (isString(value)) {
        // value is now narrowed to type 'string'
        console.log(value.toUpperCase()); // Safe operation
    }
}
```

In this example, the `value is string` in the type guard allows TypeScript to understand that within the `if` block, `value` is a string, enabling safer operations like calling `toUpperCase()`.

#### 2. **Type-safe Assertions**

TypeScript can use **type assertions** (e.g., `value as Type`), but they should be used sparingly and cautiously. Type assertions bypass TypeScript's type checking, leading to potential runtime errors if the asserted type is incorrect.

Instead of using type assertions, consider writing a custom type guard that safely narrows down the type. This can help prevent issues where you might otherwise incorrectly assert the value type.

Instead of:

```typescript
const value = someValue as string;
```

You can use a safer approach with a type of guard:

```typescript
function isString(value: unknown): value is string {
    return typeof value === 'string';
}

const value = someValue;
if (isString(value)) {
    // Safe to use 'value' as string
    console.log(value.toUpperCase());
}
```

Using a type guard like `string,` TypeScript will automatically infer the type of `value` without needing a potentially unsafe type assertion.

#### 3. **Exhaustive Checks**

When using **switch cases** or conditional statements with multiple possible types or values, it’s a good idea to implement **exhaustive checks**. This ensures that all possible cases are handled and that TypeScript will throw an error if a case is not handled.

A common way to do this is to use the `never` type in the default case of a switch statement. The `never` type indicates that the code should never reach that point if all possible cases have been handled, helping to catch any unhandled cases at compile time.

```typescript
type Animal = { type: 'dog'; bark: () => void } | { type: 'cat'; meow: () => void };

function handle animal(animal: Animal) {
    switch (animal.type) {
        case 'dog':
            animal.bark();
            break;
        case 'cat':
            animal.meow();
            break;
        default:
            // TypeScript will raise an error if there's a missing type
            const exhaustive check: never = animal;
            throw new Error(`Unhandled animal type: ${exhaustiveCheck}`);
    }
}
```

Here, the `default` case assigns the `animal` to a variable of type `never,` which will result in a TypeScript error if a new animal type is added without updating the switch statement.

Conclusion: Write Safer Code with TypeScript Type Guards
In conclusion, TypeScript type guards are a powerful feature that ensures your code is safer and more maintainable. They help you define and enforce precise types at runtime, which makes your code less prone to errors that would otherwise only surface during execution. By mastering basic and advanced type guards, you can leverage TypeScript's static type system to catch potential issues early, long before they become runtime problems.
Advanced type guards, like user-defined type guards, allow you to create custom logic to refine the type-checking process based on your specific use cases. This customization gives you more flexibility in handling complex types, ensuring you can safely manipulate and process data without introducing unforeseen bugs.
Incorporating in-built type guards (such as typeof and instanceof) and implementing exhaustive checks (e.g., through never types in switch-case statements) further improves type safety. These practices encourage you to cover every case in your code, making it easier to reason about and debug while preventing mistakes like accessing properties or methods on the wrong types.
In short, type guards help you write more predictable, robust, and secure code. They encourage you to define your types explicitly, minimizing the likelihood of bugs. So, the next time you deal with complex data structures or need to check types at runtime, consider using type guards to strengthen your codebase.

Happy coding!

\*\* Book Recommendation:

- [React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
- [React Key Concepts](https://amzn.to/43XOCJM)
- [Pragmatic Programmer](https://amzn.to/3W1P4oL) **_The: Your journey to mastery, 20th Anniversary Edition_**

[Mentorship & Consulting - Contact us for more info](/contact)

**_Join Our Discord Community_** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

**_For Consulting and Mentorship, feel free to contact_** [slavo.io](/contact)
