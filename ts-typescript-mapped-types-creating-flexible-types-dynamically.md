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
Introduction
TypeScript is a powerful tool for developers who want to write scalable and maintainable code. One of its lesser-known yet handy features is Mapped Types. Mapped Types allow developers to dynamically create flexible and reusable types, making TypeScript even more potent for complex applications.
In this article, we'll explore Mapped Types, how they work, and how you can use them to improve type safety in your projects.

### What Are Mapped Types?  

In TypeScript, mapped types offer a powerful way to create new types based on existing ones. By transforming properties dynamically, mapped types allow developers to enforce consistency, reduce redundancy, and adapt to changing requirements with minimal effort. They are instrumental when working with object types, enabling modifications such as making properties optional or read-only or altering value types.

At their core, mapped types use TypeScript's key remapping syntax to iterate over properties of an existing type and apply transformations. This approach ensures that changes are applied systematically rather than manually adjusting each property.

Consider a scenario where we want to create a read-only version of an object type. Instead of defining it manually, we can use a mapped type to automate the process:

"`typescript
type Readonly< T > = {
  readonly [K in key of T]: T[K];
};

This `Readonly<T>` type takes any object type `T` and transforms all its properties into `readonly`, preventing accidental modifications.

By leveraging mapped types, developers can construct flexible and reusable type definitions, making TypeScript a more expressive and maintainable language.

### Basic Syntax of Mapped Types  

Mapped types in TypeScript allow the creation of new types by transforming the properties of an existing type. This is particularly useful for dynamically generating variations of types without manually defining each one.

The basic syntax of a mapped type follows this structure:

```ts
type MappedType<T> = {
  [Key in keyof T]: <PropertyTransformation>;
};
```

Here’s a breakdown of the syntax:

- `[Key in keyof T]` iterates over each key in `T`, ensuring that all properties from `T` are represented in the new type.
- The transformation `<PropertyTransformation>` determines how the property types are modified.

### Example: Making All Properties Optional  

An everyday use case is creating a mapped type that makes all properties of a given type optional:

```ts
type Partial<T> = {
  [Key in keyof T]?: T[Key];
};
```

For instance, applying `Partial` to an object type:

```ts
type User = {
  id: number;
  name: string;
  email: string;
};

type PartialUser = Partial<User>;
```

The resulting `PartialUser` type is:

```ts
type PartialUser = {
  id?: number;
  name?: string;
  email?: string;
};
```

### Example: Readonly Mapped Type  

Similarly, we can create a mapped type that makes all properties read-only:

```ts
type Readonly<T> = {
  readonly [Key in keyof T]: T[Key];
};
```

Using it with the `User` type:

```ts
type ReadonlyUser = Readonly<User>;
```

This ensures that all properties in `ReadonlyUser` cannot be reassigned after initialization.

### Combining Multiple Transformations  

Mapped types can also apply multiple transformations at once. For example, making all properties both optional and read-only:

```ts
type ReadonlyPartial<T> = {
  readonly [Key in keyof T]?: T[Key];
};
```

Applying it to `User`:

```ts
type ReadonlyPartialUser = ReadonlyPartial<User>;
```

The resulting type will be:

```ts
type ReadonlyPartialUser = {
  readonly id?: number;
  readonly name?: string;
  readonly email?: string;
};
```

### Mapping Types with Constraints  

Mapped types can include constraints to filter properties based on their types. For example, if we only want to pick numeric properties of a kind:

```ts
type NumericOnly<T> = {
  [Key in keyof T as T[Key] extends number ? Key : never]: T[Key];
};
```

Applying this to `User`:

```ts
type NumericUser = NumericOnly<User>;
```

Since `id` is the only numeric property, `NumericUser` will be:

```ts
type NumericUser = {
  id: number;
};
```

### Conclusion  

Mapped types provide a powerful way to create flexible and reusable type transformations in TypeScript. By leveraging key iteration, property transformation, and conditional constraints, you can define dynamic types that adapt to different needs.

Practical Examples of Mapped Types

### 1. Making All Properties Readonly  

In TypeScript, mapped types allow us to create new kinds dynamically by transforming existing ones. One everyday use case is ensuring that all properties of a given type are read-only, preventing accidental modification.  

#### **Using `Readonly<T>`**  

TypeScript provides a built-in utility type called `Readonly<T>`, which takes an object type and marks all its properties as `readonly`.  

```typescript
type User = {
  id: number;
  name: string;
};

const user: Readonly<User> = {
  id: 1,
  name: "Alice",
};

// Error: Cannot assign to 'name' because it is a read-only property.
user.name = "Bob";
```

While `Readonly<T>` is helpful, sometimes we need more **fine-grained control** over how properties are mapped. This is where **custom-mapped types** shine.  

#### **Creating a Custom Readonly Mapped Type**  

We can manually create a mapped type that applies `readonly` to each property:  

```typescript
type ReadonlyMapped<T> = {
  readonly [K in keyof T]: T[K];
};

type ReadonlyUser = ReadonlyMapped<User>;
```

This behaves exactly like `Readonly<T>`, making all properties immutable. The syntax `[K in keyof T]` iterates over each property of `T`, applying the `readonly` modifier dynamically.  

#### **Applying Readonly Conditionally**  

Sometimes, we can make only **some** properties readonly while leaving others mutable. This can be achieved using conditional types:  

```typescript
type PartiallyReadonly<T, K extends keyof T> = {
  readonly [P in K]: T[P];
} & {
  [P in Exclude<keyof T, K>]: T[P];
};

type PartialReadonlyUser = PartiallyReadonly<User, "id">;

const partialUser: PartialReadonlyUser = {
  id: 1, // Readonly
  name: "Alice", // Mutable
};

// Error: Cannot assign to 'id' because it is a read-only property.
partialUser.id = 2;

partialUser.name = "Bob"; // Allowed
```

Only the `id` field is readonly here, while `name` remains mutable.  

#### **Conclusion**  

Mapped types provide a powerful way to dynamically modify object types in TypeScript. By leveraging `read-only` modifiers, we can prevent unintended mutations, ensuring better type safety while maintaining flexibility.

### **Making All Properties Optional in TypeScript Mapped Types: Creating Flexible Types Dynamically**  

TypeScript's mapped types provide a powerful way to transform existing types dynamically. One of the most common transformations is making all properties of a given type optional. This is particularly useful when working with APIs, form validation, or configurations requiring partial updates.  

#### **Using the `Partial<T>` Utility Type**  

TypeScript provides a built-in utility type called `Partial<T>` that achieves this transformation effortlessly:  

```typescript
type User = {
  id: number;
  name: string;
  email: string;
};

type OptionalUser = Partial<User>;
```

The `Partial<T>` utility makes all properties in `User` optional, resulting in the equivalent type:  

```typescript
type OptionalUser = {
  id?: number;
  name?: string;
  email?: string;
};
```

While `Partial<T>` is a quick solution, understanding how it works internally can help us create customized mapped types.

#### **Manually Creating an Optional Mapped Type**  

The `Partial<T>` utility type is implemented using mapped types and the `?` modifier:

```typescript
type MyPartial<T> = {
  [K in keyof T]?: T[K];
};

type OptionalUser = MyPartial<User>;
```

Here, `[K in keyof T]?: T[K];` iterates over all keys in `T` and applies the `?` modifier to each property, making them optional.

#### **Use Cases for Optional Mapped Types**  

1. **Partial Updates**  
   - When updating only specific fields of an object without requiring all properties.  
2. **Flexible API Responses**  
   - When dealing with optional fields in API responses.  
3. **Configurable Interfaces**  
   - Creating flexible settings where only some properties are required.  

#### **Extending Mapped Types for More Control**  

Beyond making properties optional, we can extend this approach to create more dynamic transformations, such as making properties readonly or nullable.

Understanding mapped types unlock powerful ways to manipulate types dynamically in TypeScript, improving code flexibility and maintainability. 🚀

Here's a draft for the section "Converting Property Types" in the same writing style as the beginning of your content on TypeScript Mapped Types: Creating Flexible Types Dynamically:
3. Converting Property Types
One of the most powerful capabilities of TypeScript’s mapped types is dynamically transforming property types. This allows us to take an existing type and convert all or some of its properties to a different kind, ensuring flexibility and reducing redundancy in our code.
Transforming All Properties
Suppose we have a type representing a user with various properties of different types:
type User = {
  id: number;
  name: string;
  isActive: boolean;
};
If we need a version of this type where all properties are transformed into strings—for instance, for serializing data—we can use a mapped type:
type Stringified< T > = {
  [K in keyof T]: string;
};

type StringifiedUser = Stringified< User >;
Here, Stringified< T > iterates over all properties of T and forces their types to be string. The resulting StringifiedUser type is:
type StringifiedUser = {
  id: string;
  name: string;
  isActive: string;
};
This approach is practical when transforming data structures for storage, transmission, or display purposes.
Selective Property Transformation
Instead of converting every property, we suggest transforming only certain ones. TypeScript allows us to do this with conditional types. For example, let's say we want to convert only boolean properties into string:
type ConvertBooleans< T > = {
  [K in keyof T]: T[K] extends boolean ? string : T[K];
};

type ModifiedUser = ConvertBooleans< User >;
This ConvertBooleans< T > type iterates through T and checks if a property is of type boolean. If so, it converts it to a string; otherwise, it keeps the original type. The resulting type looks like this:
type ModifiedUser = {
  id: number;
  name: string;
  isActive: string;
};
This method is beneficial when dealing with APIs or UI layers where specific data types need transformation while others remain unchanged.
Applying Complex Transformations
We can further refine transformations by introducing additional logic. Suppose we want to:
Convert boolean to string
Convert number to boolean
Leave other types unchanged
We can achieve this with nested conditional types:
type AdvancedTransform< T > = {
  [K in keyof T]: T[K] extends boolean
    ? string
    : T[K] extends number
      ? boolean
      : T[K];
};

type TransformedUser = AdvancedTransform< User >;
Now, the TransformedUser type results in:
type TransformedUser = {
  id: boolean;
  name: string;
  isActive: string;
};
This pattern allows us to dynamically adapt our types to different use cases, making TypeScript’s type system highly flexible.
Conclusion
Converting property types with mapped types provides a powerful way to modify structures without rewriting them manually. Whether applying broad transformations or selecting certain types, TypeScript enables us to build dynamic and adaptable type definitions that enhance code maintainability and safety.
Would you like any refinements or additional examples? 🚀

### **4. Removing `readonly` Modifiers for TypeScript Mapped Types: Creating Flexible Types Dynamically**  

TypeScript’s `readonly` modifier ensures that object properties cannot be reassigned after initialization. While this is valuable for enforcing immutability, there are cases where we need to programmatically remove `readonly` from properties—especially when working with mapped types to create flexible, dynamic structures.  

#### **Using the `-readonly` Operator**  

TypeScript provides the `-readonly` operator to explicitly strip the `readonly` modifier from properties in a mapped type. This is particularly useful when transitioning from immutable to mutable objects, such as when handling API responses or modifying states in functional programming paradigms.  

Here’s a simple example:  

```typescript
type ReadonlyUser = {
  readonly id: number;
  readonly name: string;
};

type MutableUser = {
  -readonly [K in keyof ReadonlyUser]: ReadonlyUser[K];
};
```

In this transformation:  

- The `-readonly` operator is applied within the mapped type.  
- Each property from `ReadonlyUser` loses its `readonly` modifier, resulting in `MutableUser`, where properties can be reassigned.  

#### **Real-World Use Cases**  

- **Converting Immutable Data to Mutable Structures**:  
  Many frameworks, like Redux, rely on immutability, but sometimes modifications are needed before reassigning values.  
- **Enhancing API Response Objects**:  
  Some APIs return data marked as `readonly`, but we may need to modify it before further processing.  
- **Dynamic Object Transformations**:  
  Removing `readonly` dynamically allows us to construct new types without manually redefining each property.  

#### **Combining with Utility Types**  

To make this more reusable, we can define a utility type that generalizes the removal of `readonly`:  

```typescript
type Mutable<T> = {
  -readonly [K in keyof T]: T[K];
};

type MutableUser = Mutable<ReadonlyUser>;
```

By applying `Mutable<T>`, we can instantly create a mutable version of any type.

Here's a continuation of the section in the same writing style:
Combining Mapped Types with Conditional Types
TypeScript’s mapped types are consequential on their own, allowing developers to transform object types dynamically. However, their true potential is unlocked when combined with conditional types. This combination enables even more precise type transformations, adding logic to processing properties.
Applying Conditional Logic in Mapped Types
A common use case is selectively modifying certain properties based on their type. For instance, you can convert all string properties in an object to number, while leaving other properties unchanged. This can be achieved by integrating conditional types within a mapped type:
type ConvertStringsToNumbers< T > = {
  [K in keyof T]: T[K] extends string ? number : T[K];
};

type Example = {
  name: string;
  age: number;
  isActive: boolean;
};

type Transformed = ConvertStringsToNumbers< Example >;
/*
  Transformed is:
  {
    name: number;
    age: number;
    isActive: boolean;
  }
*/
Here, ConvertStringsToNumbers< T > iterates over each key in T. If a property’s type extends the string, it is replaced with a number; otherwise, it remains unchanged.
Filtering Properties Using Conditional Mapped Types
Another practical pattern is filtering object properties based on their types. Suppose we want to extract only the keys of an object whose values are of a specific type:
type ExtractKeysOfType<T, Type> = {
  [K in keyof T]: T[K] extends Type ? K : never;
}[keyof T];

type Example = {
  id: number;
  title: string;
  isPublished: boolean;
};

type StringKeys = ExtractKeysOfType<Example, string>; // "title"
This works by mapping each key to itself only if its corresponding value matches the Type; otherwise, mapping it to never. Finally, [keyof T] extracts only the valid keys.
Creating Partial or Readonly Variants Conditionally
A more advanced pattern involves making properties optional or readonly based on their type. For example, we could make all function properties in an object readonly:
type ReadonlyFunctions< T > = {
  [K in keyof T]: T[K] extends (...args: any[]) => any ? Readonly<T[K]> : T[K];
};

type Example = {
  handler: (event: Event) => void;
  name: string;
};

type ReadonlyHandlers = ReadonlyFunctions< Example >;
/*
  ReadonlyHandlers is:
  {
    handler: Readonly<(event: Event) => void>;
    name: string;
  }
*/
Conclusion
By combining mapped types with conditional types, TypeScript provides fine-grained control over how object types are transformed. Whether modifying, filtering or selectively making properties read-only, this technique enhances type flexibility and ensures precise type definitions dynamically.
Here’s a section in the same style as the Why Use Mapped Types. Section from TypeScript Mapped Types: Creating Flexible Types Dynamically:
Why Use Mapped Types?
When working with TypeScript, you often need to transform existing types rather than create new ones from scratch. Mapped types offer a powerful way to modify types, making your code more flexible, reusable, and maintainable dynamically. Instead of manually defining similar types with slight variations, mapped types allow you to generate new types based on existing ones with minimal effort.
For example, consider a scenario where you have a type representing a user object, but you need a version where all properties are optional. Without mapped types, you’d have to manually redefine the type with optional modifiers, which can be tedious and error-prone. Mapped types automate this process, ensuring type safety and consistency while reducing boilerplate code.
By leveraging mapped types, you can create utility types for common transformations, such as making all properties read-only or optional or converting values to a specific type. This makes your TypeScript code more expressive and adaptable to evolving requirements.
Would you like me to extend this further or adjust the tone?
Conclusion
Mapped Types in TypeScript provide a powerful way to dynamically create flexible and reusable types. By understanding and using them effectively, you can enhance your code's maintainability and type safety.
Whether you need to make properties readonly, optional, or transform property types, Mapped Types are a valuable tool in your TypeScript arsenal.
Start experimenting with Mapped Types in your projects today and unlock the full potential of TypeScript’s type system!

Happy coding!

\*\* Book Recommendation:

- [React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
- [React Key Concepts](https://amzn.to/43XOCJM)
- [Pragmatic Programmer](https://amzn.to/3W1P4oL) **_The: Your journey to mastery, 20th Anniversary Edition_**

[Mentorship & Consulting - Contact us for more info](/contact)

**_Join Our Discord Community_** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

**_For Consulting and Mentorship, feel free to contact_** [slavo.io](/contact)
