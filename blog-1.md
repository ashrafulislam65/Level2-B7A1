# Why `any` Is a Type Safety Hole and `unknown` Is the Safer Choice

## Introduction
TypeScript is designed to add safety on top of JavaScript. However, the `any` type completely bypasses this safety, making it dangerous in real-world applications. This blog explains why `any` is considered a "type safety hole" and how `unknown`, combined with type narrowing, provides a safer alternative.

## The Problem with `any`
When you use `any`, TypeScript stops checking types entirely.

```ts
let data: any;
data.toUpperCase();
data();


---
Why unknown Is Safer

The unknown type forces you to verify the type before using it.
---
let value: unknown;

if (typeof value === "string") {
  value.toUpperCase();
}
---
Here, TypeScript ensures that unsafe operations are not allowed unless the type is confirmed.

Type Narrowing

Type narrowing means reducing a broad type into a more specific one using checks like typeof, instanceof, or custom guards.
---
function process(input: unknown): string {
  if (typeof input === "number") {
    return input.toString();
  }
  return "Invalid input";
}
---
This approach prevents runtime errors while keeping flexibility.
---
Conclusion

any removes all guarantees provided by TypeScript, making your code risky and unpredictable. unknown, combined with proper type narrowing, ensures safety while still allowing you to work with dynamic data. For robust and maintainable applications, unknown is always the better choice.
---