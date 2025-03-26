---
title: "What is TypeScript? A Beginner’s Guide to Typed JavaScript"
date: "2025-03-20"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "JavaScript is the backbone of modern web development, powering everything from dynamic websites to complex web applications."
isFeatured: false
category: "Type Script"
---

TypeScript Mapped Types: Creating Flexible Types Dynamically
TypeScript is a powerful language that extends JavaScript by adding static typing. One of its most valuable features is Mapped Types, which allows developers to create flexible and reusable types dynamically. If you've ever wanted to transform or modify an existing type in a structured way, mapped types are your go-to tool.
This blog post'll explore mapped types, how they work, and some practical use cases to improve your TypeScript code. Whether you're a beginner or an advanced TypeScript user, this guide will help you understand how to leverage mapped types for better scalability and maintainability.

### **Mapped Types in TypeScript**  

Mapped types in TypeScript transform properties from an existing type into a new one. Instead of manually defining a new type, mapped types allow dynamic type generation, making TypeScript more flexible and scalable.

---

### **Syntax and Breakdown**  

A mapped type is defined using the following syntax:  

```ts
type MappedType<T> = {
  [Key in keyof T]: Transformation<T[Key]>;
};
```

Let’s break this down step by step:  

1. **`keyof T`** – This extracts the property keys of type `T`. It returns a union of all the keys in `T`.  
2. **`[Key in keyof T]`** – This iterates over each key in `T`, allowing modifications to its corresponding value type.  
3. **`Transformation<T[Key]>`** – This applies a transformation function (such as making a property optional, readonly, or changing its type) to the value associated with each key.  

---

### **Example: Basic Mapped Type**  

Here’s a simple example of a mapped type that makes all properties of a given type `T` optional:  

```ts
type PartialType<T> = {
  [Key in keyof T]?: T[Key];
};

type User = {
  name: string;
  age: number;
};

type PartialUser = PartialType<User>;

// Equivalent to:
// type PartialUser = {
//   name?: string;
//   age?: number;
// };
```

This works similarly to TypeScript’s built-in `Partial<T>` utility type.

---

### **Common Use Cases**  

Mapped types are helpful for various transformations, including:  

- **Making properties optional (`Partial<T>`)**  
- **Making properties readonly (`Readonly<T>`)**  
- **Changing all property types (`Record<K, T>`)**  
- **Filtering properties based on conditions (e.g., removing `null` types)**  

Here’s an example that converts all properties of a type to `string`:  

```ts
type Stringify<T> = {
  [Key in keyof T]: string;
};

type Product = {
  id: number;
  price: number;
};

type StringifiedProduct = Stringify<Product>;

// Equivalent to:
// type StringifiedProduct = {
//   id: string;
//   price: string;
// };
```

---

### **Advanced Example: Conditional Mapped Types**  

You can also use conditional types in mapped types. For instance, if you want to make only `string` properties `readonly`, you can do the following:

```ts
type ReadonlyStringProps<T> = {
  [Key in keyof T as T[Key] extends string ? Never: Key]: T[Key];
};

type Person = {
  name: string;
  age: number;
  isAdmin: boolean;
};

type ModifiedPerson = ReadonlyStringProps<Person>;

// Equivalent to:
// type ModifiedPerson = {
//   age: number;
//   isAdmin: boolean;
// };
```

In this example, the `as` clause removes properties whose values are of type `string`, effectively filtering out `name`.

---

### **Conclusion**  

Mapped types are one of TypeScript’s most powerful features, allowing dynamic type transformations based on existing structures. By leveraging `keyof`, transformations, and conditional types, you can create flexible and reusable type definitions that adapt to changing data structures.

### 5. Transforming Values with Mapped Types  

Mapped types allow you to modify the types of object properties dynamically. This is useful when you must transform an entire object’s properties into a different kind without manually rewriting each one.  

#### **Example: Converting Property Types to `string`**  

An everyday use case transforms an object's properties into `string` values. This can be useful when serializing objects for display or logging purposes.  

```ts
type Stringify<T> = {
  [K in keyof T]: string;
};
```

#### **Usage Example**  

```ts
interface User {
  id: number;
  age: number;
}

type StringifiedUser = Stringify<User>;
```

Here, `StringifiedUser` will have the following type:  

```ts
{
  id: string;
  age: string;
}
```

Every property in the original `User` type is now of type `string`.  

---

#### **Example: Converting Property Types to `boolean`**  

You might also need to convert all properties of an object to `boolean`, for example, when dealing with feature flags or permission checks:  

```ts
type Booleanify<T> = {
  [K in keyof T]: boolean;
};
```

##### **Usage Example:**  

```ts
interface FeatureFlags {
  darkMode: string;
  betaAccess: number;
}

type BooleanFlags = Booleanify<FeatureFlags>;
```

Resulting type:  

```ts
{
  darkMode: boolean;
  betaAccess: boolean;
}
```

All properties are now of type `boolean`, ensuring consistent type usage across the application.  

---

#### **Example: Transforming Properties to `Promise<T>`**  

Another robust use case is converting all object properties to return `Promise<T>`. This is useful when working with asynchronous APIs.  

```ts
type Promisify<T> = {
  [K in keyof T]: Promise<T[K]>;
};
```

Usage Example:

```ts
interface UserData {
  name: string;
  age: number;
}

type AsyncUserData = Promisify<UserData>;
```

Now, `AsyncUserData` will have the following structure:  

```ts
{
  name: Promise<string>;
  age: Promise<number>;
}
```

This approach ensures that every property is wrapped in a `Promise`, making it ideal for scenarios requiring data fetching or asynchronous operations.  

---

### **Why Use Value Transformations in Mapped Types?**  

1. **Code Reusability** – Instead of manually creating new types for different transformations, you can reuse generic mapped types.
2. **Consistency** – Ensures uniform changes across all properties.
3. **Flexibility** – You can apply different transformations (e.g., `string`, `boolean`, `Promise<T>`) based on requirements.
4. **Type Safety** – TypeScript ensures that transformations are correctly applied, reducing runtime errors.

This technique benefits API response handling, UI state management, and feature flag implementations.

### **Advanced Usage: Conditional Mapped Types**  

In TypeScript, **mapped types** allow you to transform each property of a given type. When combined with **conditional types**, they become even more powerful, enabling highly flexible and dynamic transformations.

---

### **Example: Converting Properties to Nullable**  

Consider a scenario where we want to make every property of a given type `T` nullable. We can achieve this using a mapped type:

```ts
type NullableType<T> = {
  [K in keyof T]: T[K] | null;
};
```

#### **How It Works:**

- `keyof T`: Retrieves all keys (property names) from `T`.
- `[K in keyof T]`: Iterates over each key in `T`.
- `T[K] | null`: Keeps the original type but also allows `null`.

This transformation ensures that every property in `T` can hold its original value or `null`.

Usage Example:

```ts
type User = {
  id: number;
  name: string;
  isActive: boolean;
};

type NullableUser = NullableType<User>;
```

The resulting `NullableUser` type will be:

```ts
type NullableUser = {
  id: number | null;
  name: string | null;
  isActive: boolean | null;
};
```

Now, an object of type `NullableUser` can look like this:

```ts
const user: NullableUser = {
  id: null,
  name: "Alice",
  isActive: null,
};
```

---

### **Extending with Conditional Types**

We can take this further by introducing conditional types, making the transformation even more dynamic.

For example, we might want to make only properties of a particular type nullable:

```ts
type NullableSpecific<T, U> = {
  [K in keyof T]: T[K] extends U ? T[K] | null : T[K];
};
```

Usage Example:

```ts
type User = {
  id: number;
  name: string;
  isActive: boolean;
};

type NullableStrings = NullableSpecific<User, string>;
```

Here, only `string` properties become nullable:

```ts
type NullableStrings = {
  id: number;
  name: string | null;
  isActive: boolean;
};
```

This approach enables more **fine-grained control** over type transformations.

---

### **Why Use Conditional Mapped Types?**

1. **Reusability** – Define generic transformations that can be applied to multiple types.
2. **Type Safety** – Prevent errors by explicitly defining how properties should change.
3. **Flexibility** – Modify only specific properties based on their types.
4. **Code Maintainability** – Avoid manually defining variations of similar types.

Conditional mapped types are a powerful feature in TypeScript, allowing developers to write **more generic, flexible, and type-safe** code.

Happy coding!

\*\* Book Recommendation:

- [React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
- [React Key Concepts](https://amzn.to/43XOCJM)
- [Pragmatic Programmer](https://amzn.to/3W1P4oL) **_The: Your journey to mastery, 20th Anniversary Edition_**

[Mentorship & Consulting - Contact us for more info](/contact)

**_Join Our Discord Community_** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

**_For Consulting and Mentorship, feel free to contact_** [slavo.io](/contact)
