---
title: no-bitwise
layout: doc
edit_link: https://github.com/eslint/eslint/edit/main/docs/src/rules/no-bitwise.md
rule_type: suggestion
---

Disallows bitwise operators.

The use of bitwise operators in JavaScript is very rare and often `&` or `|` is simply a mistyped `&&` or `||`, which will lead to unexpected behavior.

```js
var x = y | z;
```

## Rule Details

This rule disallows bitwise operators.

Examples of **incorrect** code for this rule:

::: incorrect

```js
/*eslint no-bitwise: "error"*/

var x = y | z;

var x = y & z;

var x = y ^ z;

var x = ~ z;

var x = y << z;

var x = y >> z;

var x = y >>> z;

x |= y;

x &= y;

x ^= y;

x <<= y;

x >>= y;

x >>>= y;
```

:::

Examples of **correct** code for this rule:

::: correct

```js
/*eslint no-bitwise: "error"*/

var x = y || z;

var x = y && z;

var x = y > z;

var x = y < z;

x += y;
```

:::

## Options

This rule has an object option:

* `"allow"`: Allows a list of bitwise operators to be used as exceptions.
* `"int32Hint"`: Allows the use of bitwise OR in `|0` pattern for type casting.

### allow

Examples of **correct** code for this rule with the `{ "allow": ["~"] }` option:

::: correct

```js
/*eslint no-bitwise: ["error", { "allow": ["~"] }] */

~[1,2,3].indexOf(1) === -1;
```

:::

### int32Hint

Examples of **correct** code for this rule with the `{ "int32Hint": true }` option:

::: correct

```js
/*eslint no-bitwise: ["error", { "int32Hint": true }] */

var b = a|0;
```

:::
