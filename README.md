# SASS (Syntactically Awesome Stylesheets)

## Introduction

SASS is a `CSS preprocessor` that adds powerful features and functionalities, making `CSS more maintainable and efficient.`

---

## 1. Basics of SASS

- `SASS Syntax:` Indentation-based, no braces (`{}`) or semicolons (`;`), `python` like syntax.
- `SCSS Syntax:` CSS-like syntax with braces and semicolons.

```scss
// SCSS Syntax
body {
  font-size: 16px;
}

// SASS Syntax
body
  font-size: 16px
```

---

## 2. Variables

- store `reusable values` (e.g., colors, fonts, spacing).

```scss
$primary-color: #3498db;
body {
  background-color: $primary-color;
}
```

---

## 2a. Operators

#### `1. Arithmetic Operators`

Perform calculations in styles:

- `Addition (+)`: 100px + 50px; // 150px
- `Subtraction (-)`: 200px - 50px; // 150px
- `Multiplication (*)`: 10px \* 2; // 20px
- `Division (/)`: (100px / 2); // 50px
- `Modulo (%)`: 10 % 3; // 1

---

#### `2. Relational Operators`

Compare values, return `true` or `false`:

- `Equality (==)`: @if (5 == 5) { // true }
- `Inequality (!=)`: @if (5 != 3) { // true }

---

#### `3. Logical Operators`

Control flow with `@if`, `@else`:

- `And (and)`: @if (true and false) {}
- `Or (or)`: @if (true or false) {}
- `Not (not)`: @if (not false) { // true }

## 3. Nesting

- Allows `nested selectors` for better readability and structure.

```scss
nav {
  ul {
    margin: 0;
    li {
      list-style: none;
      &:hover {
        color: blue;
      }
    }
  }
}
```

---

## 4. Partials and Import

- `Partials`: Files prefixed with `_`, used for `modular styles`.
- `@import`: Includes partials.

```scss
// _variables.scss
$font-stack: Helvetica, sans-serif;

// main.scss
@import "variables";
body {
  font-family: $font-stack;
}
```

---

## 5. Mixins

- Create `reusable chunks of code`.

```scss
@mixin flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}
.container {
  @include flex-center;
}
```

---

## 6. Functions

- Create custom functions with `@function`.

```scss
@function calculate-rem($px) {
  @return $px / 16 * 1rem;
}
body {
  font-size: calculate-rem(24); // 1.5rem
}
```

---

## 7. Extend/Inheritance

- Share styles using `@extend`.

```scss
.button {
  padding: 10px;
  border: none;
}
.primary-button {
  @extend .button;
  background-color: blue;
}
```

---

## 8. Interpolation

- `Dynamically inject values` into selectors or properties.

```scss
$theme: dark;
body.#{$theme}-theme {
  background-color: black;
}
```

---

## 9. Placeholders

- Reusable styles defined with `%`, used with `@extend`.

```scss
%card {
  padding: 10px;
  border-radius: 5px;
}
.card {
  @extend %card;
  background: white;
}
```

---

## 10. Control Directives

### `@if`, `@else`, `@else if`

```scss
$theme: dark;
body {
  @if $theme == dark {
    background-color: black;
  } @else {
    background-color: white;
  }
}
```

### `@for`

```scss
@for $i from 1 through 5 {
  .item-#{$i} {
    width: #{$i * 10}px;
  }
}
```

### `@each`

```scss
$colors: red, green, blue;
@each $color in $colors {
  .#{$color}-text {
    color: $color;
  }
}
```

### `@while`

```scss
$i: 1;
@while $i < 5 {
  .item-#{$i} {
    margin: #{$i}px;
  }
  $i: $i + 1;
}
```

---

## 11. `@use` and `@forward`

- `@use`: Import files with namespace.
- `@forward`: Re-export imported files.

```scss
// _variables.scss
$primary-color: blue;

// styles.scss
@use "variables";
body {
  background-color: variables.$primary-color;
}
```

---

## 12. `@content`

- Pass a block of styles to a mixin.

```scss
@mixin card($bg-color) {
  background-color: $bg-color;
  @content;
}
.card {
  @include card(white) {
    border: 1px solid black;
  }
}
```

---

## 13. Media Queries

- Nest media queries directly within selectors.

```scss
.container {
  width: 100%;
  @media (max-width: 768px) {
    width: 50%;
  }
}
```

---

## 14. Error Handling

### `@error`

```scss
@function divide($num1, $num2) {
  @if $num2 == 0 {
    @error "Cannot divide by zero!";
  }
  @return $num1 / $num2;
}
```

### `@warn`

```scss
@warn "This feature is deprecated.";
```

### `@debug`

```scss
@debug $font-size;
```

---

## 15. Lists

- A collection of values separated by spaces or commas.

```scss
$colors: red, green, blue;
color: nth($colors, 2); // green
```

---

## 16. Maps

- Key-value pairs for managing related data.

```scss
$themes: (
  primary: blue,
  secondary: green,
);
color: map-get($themes, primary); // blue
```

---

## 17. Built-in Functions

### Number Functions

- `percentage()`, `round()`, `ceil()`, `floor()`, `abs()`.

### String Functions

- `str-length()`, `to-upper-case()`, `to-lower-case()`, `str-insert()`.

### List Functions

- `length()`, `nth()`, `join()`, `list-separator()`.

### Map Functions

- `map-get()`, `map-keys()`, `map-values()`, `map-merge()`.

---

## 18. Advanced Concepts

### `@at-root`

- `Moves nested styles to the root level`.

```scss
.wrapper {
  @at-root {
    .global-class {
      color: red;
    }
  }
}
```

### Custom Properties

- Managing CSS variables.

```scss
$primary-color: blue;
:root {
  --primary-color: #{$primary-color};
}
```

---

## 19. Best Practices

- Use variables for consistent theming.
- Modularize styles with partials.
- Avoid deep nesting (limit to 3 levels).
- Use `@use` for namespacing.
- Follow naming conventions (e.g., BEM methodology).

---

SASS provides a powerful toolset to write scalable, maintainable, and efficient styles, making it an indispensable tool for modern web development.
