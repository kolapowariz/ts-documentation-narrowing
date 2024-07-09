---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true
---

# Welcome to Slidev

Presentation slides for developers

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
---

<!-- # What is Slidev?  -->
# What is Narrowing in TypeScript?

Narrowing is the process by which TypeScript reduces the types of a variable within a specific block of code, typically as a result of type checks. This makes TypeScript code safer and more predictable, allowing developers to leverage the type system to catch potential errors at compile time.

It occurs when a variable moves from a less precise type to a more precise type.

Type narrowing in TypeScript enhances type safety by refining types through runtime checks and control flow analysis. This feature enables developers to write more predictable and less error-prone code, leveraging TypeScript's powerful type system to catch potential issues during development.

### Key Concepts in Narrowing
* Type Guards: These are expressions used to check the type of a variable at runtime. Type guards are critical for narrowing because they inform the TypeScript compiler about the specific type within a block of code.

* Control Flow Analysis: TypeScript tracks the type of a variable as the code executes, refining the type based on the code's control flow.

<!-- Slidev is a slides maker and presenter designed for developers, consist of the following features

- 📝 **Text-based** - focus on the content with Markdown, and then style them later
- 🎨 **Themable** - themes can be shared and re-used as npm packages
- 🧑‍💻 **Developer Friendly** - code highlighting, live coding with autocompletion
- 🤹 **Interactive** - embed Vue components to enhance your expressions
- 🎥 **Recording** - built-in recording and camera view
- 📤 **Portable** - export to PDF, PPTX, PNGs, or even a hostable SPA
- 🛠 **Hackable** - virtually anything that's possible on a webpage is possible in Slidev
<br>
<br>

Read more about [Why Slidev?](https://sli.dev/guide/why) -->

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
h3 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
Here is another comment.
-->

---
transition: slide-up
level: 2
---

# Common Type Guards and Narrowing Techniques.

* `typeof` Type Guard: Used to check primitive types (string, number, boolean, etc.).
* `Truthiness` narrowing: Used to refine the types of variables based on their truthy or falsy values in conditional statements.
* `Equality` narrowing: Used to refine the type of a variable based on equality checks (such as ===, !==, ==, !=) in conditional statements.
* `instanceof` Type Guard: Used to check if an object is an instance of a particular class.
* `in` Type Guard: Used to check if an object has a particular property.
* `assignment` narrowing: Used to narrow the type of a variable based on the value assigned to it.
* `User-Defined` Type Guards: Functions that return a type predicate to narrow the type.
* `Control flow analysis`: Used to refine type of a variable based on the control flow of the program.
* `type predicates`: Used to define custom or a user-defined type guards.
* `Assertion functions`: Used to assert specific conditions and help TypeScript to narrow down types based on these assertions.
<!-- # Navigation -->

<!-- Hover on the bottom-left corner to see the navigation's controls panel, [learn more](https://sli.dev/guide/navigation.html)

## Keyboard Shortcuts

|     |     |
| --- | --- |
| <kbd>right</kbd> / <kbd>space</kbd>| next animation or slide |
| <kbd>left</kbd>  / <kbd>shift</kbd><kbd>space</kbd> | previous animation or slide |
| <kbd>up</kbd> | previous slide |
| <kbd>down</kbd> | next slide | -->

<!-- https://sli.dev/guide/animations.html#click-animations -->
<!-- <img
  v-click
  class="absolute -bottom-9 -left-7 w-80 opacity-50"
  src="https://sli.dev/assets/arrow-bottom-left.svg"
  alt=""
/>
<p v-after class="absolute bottom-23 left-45 opacity-30 transform -rotate-10">Here!</p> -->

---
layout: two-cols
layoutClass: gap-16
---
`typeof` Type Guard: Used to check primitive types (string, number, boolean, etc.).

```ts
function printId(id: string | number) {
    if (typeof id === "string") {
        console.log("Your ID is: " + id.toUpperCase());
    } else {
        console.log("Your ID is: " + id);
    }
}
```

---
transition: slide-up
level: 2
---

`Truthiness` narrowing : TypeScript narrows the type of a variable within a specific scope based on the condition evaluated in that scope.

Falsy and Truthy Values
In JS and TS, values are categorized as either falsy or truthy. Falsy values include: false, 0, '' (empty string), null, undefined, NaN. Everything else is considered truthy.

```ts 
function printValue(value: string | number | null | undefined) {
    if (!value) {
        console.log('Value is either null, undefined, empty string, 0, or NaN.');
    } else {
        console.log('Value is:', value);
    }
}

```


---
transition: slide-up
level: 2
---
`Equality` narrowing : By checking if a variable equals or does not equal a specific value, TypeScript can narrow the possible types of that variable within a given scope. When you perform an equality check on a variable, TypeScript refines the type of the variable within the true and false branches of the condition. This allows TypeScript to infer more specific types, which can be helpful for type checking and avoiding runtime errors.

```ts
function processValue(value: string | number | null) {
    if (value === null) {
        // Here, TypeScript knows that 'value' is 'null'
        console.log('Value is null');
    } else if (typeof value === 'string') {
        // Here, TypeScript knows that 'value' is 'string'
        console.log('String value:', value.toUpperCase());
    } else {
        // Here, TypeScript knows that 'value' is 'number'
        console.log('Number value:', value.toFixed(2));
    }
}

processValue("Hello"); // String value: HELLO
processValue(42);      // Number value: 42.00
processValue(null);    // Value is null
```

---
transition: slide-left
level: 2
---
`instance of` narrowing : Used to check if an object is an instance of a particular class.

```ts
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

function speak(animal: Dog | Cat) {
    if (animal instanceof Dog) {
        animal.bark();
    } else {
        animal.meow();
    }
}


```

---
transition: slide-left
level: 2
class: px-20
---

`in` operator narrowing : Used to check if an object has a particular property.

```ts
interface Fish {
    swim: () => void;
}

interface Bird {
    fly: () => void;
}

function move(animal: Fish | Bird) {
    if ("swim" in animal) {
        animal.swim();
    } else {
        animal.fly();
    }
}

```


---

`assignment` narrowing : is a TypeScript feature where the type of a variable is narrowed based on the value assigned to it. This allows TypeScript to infer more specific types and provide better type safety in your code. When you assign a value to a variable, TypeScript can infer a more specific type from the assigned value. This is particularly useful when working with variables that have union types or generic types.

```ts
let value: string | number;

value = "Hello";
// Here, TypeScript narrows 'value' to 'string'
console.log(value.toUpperCase());

value = 42;
// Here, TypeScript narrows 'value' to 'number'
console.log(value.toFixed(2));

```

---
transition: slide-up
level: 2
---

`user-defined` type guard: Functions that return a type predicate to narrow the type.

```ts
function isFish(pet: Fish | Bird): pet is Fish {
    return (pet as Fish).swim !== undefined;
}

function move(pet: Fish | Bird) {
    if (isFish(pet)) {
        pet.swim();
    } else {
        pet.fly();
    }
}
```
---
transition: slide-up
level: 2
---
`Control flow analysis`: TypeScript tracks variables across conditions, loops, and other control flow constructs to narrow types.

```ts
function padLeft(value: string, padding: number | string) {
    if (typeof padding === "number") {
        return Array(padding + 1).join(" ") + value;
    }
    if (typeof padding === "string") {
        return padding + value;
    }
    throw new Error(`Expected string or number, got '${padding}'.`);
}
```

---
transition: slide-left
level: 2
---
`type predicates` : Functions that return a type predicate (pet is Fish) to inform TypeScript about the type within a condition.

```ts
function isNumber(x: any): x is number {
    return typeof x === "number";
}

function isString(x: any): x is string {
    return typeof x === "string";
}
```


---
transition: slide-left
level: 2
---

`Assertion functions`:  It tells TypeScript that a certain condition is true if the function doesn't throw an error. They are useful for ensuring that variables meet specific type criteria during runtime checks, especially when dealing with dynamic data or external sources like APIs.
```ts
function assert(condition: any, msg?: string): asserts condition {
  if (!condition) {
    throw new Error(msg);
  }
}
```

---
transition: slide-left
level: 2
---
`Discriminated` unions: also known as tagged unions or algebraic data types, are powerful feature in TypeScript that enable developers to create type-safe and flexible unions of different types. Each member of the union has a common property, called the discriminant or tag, which TypeScript uses to narrow the union to a specific member. This allows for more precise type checking and helps avoid runtime errors.

#### Key Concepts
Union Types: These are types formed by combining multiple types with a | (pipe) symbol.

Discriminant Property: A common property present in all members of the union, which has a different literal value for each type. This property is used to distinguish between the different types in the union.

Type Guards: Functions or expressions that check the discriminant property to narrow down the type.

---
transition: slide-left
level: 1
---
```ts
interface Circle {
    kind: "circle";
    radius: number;
}
interface Rectangle {
    kind: "rectangle";
    width: number;
    height: number;
}
type Shape = Circle | Rectangle;
```
```ts
function getArea(shape: Shape): number {
    switch (shape.kind) {
        case "circle":
            return Math.PI * shape.radius ** 2;
        case "rectangle":
            return shape.width * shape.height;
        default:
            throw new Error("Unknown shape kind");
    }
}
const myCircle: Circle = { kind: "circle", radius: 5 };
const myRectangle: Rectangle = { kind: "rectangle", width: 4, height: 6 };

console.log(getArea(myCircle)); // 78.53981633974483
console.log(getArea(myRectangle)); // 24
```
---
transition: slide-left
level: 1
---

`never` type: When narrowing, you can reduce the options of a union to a point where you have removed all possibilities and have nothing left. In those cases, TypeScript will use a never type to represent a state which shouldn’t exist.

The `never` type in TypeScript is a powerful tool for enhancing type safety and ensuring code completeness. It is used in the following scenarios:

* Functions that never return a value (e.g., throw an error or have an infinite loop).
* Exhaustiveness checking in discriminated unions to ensure all cases are handled.
* Type guards and assertion functions to indicate impossible cases.

By using the never type appropriately, you can catch potential errors at compile time and write more robust and maintainable TypeScript code.

---
transition: slide-left
level: 1
---

`Exhaustiveness` checking: The never type is assignable to every type; however, no type is assignable to never (except never itself). This means you can use narrowing and rely on never turning up to do exhaustive checking in a switch statement.
---
layout: center
class: text-center
---


# THANK YOU FOR LISTENING

---
layout: center
class: text-center
---

# Learn More

[Documentation](https://sli.dev) · [GitHub](https://github.com/slidevjs/slidev) · [Showcases](https://sli.dev/showcases.html)

<PoweredBySlidev mt-10 />
