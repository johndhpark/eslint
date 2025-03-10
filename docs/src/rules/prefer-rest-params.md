---
title: prefer-rest-params
layout: doc
edit_link: https://github.com/eslint/eslint/edit/main/docs/src/rules/prefer-rest-params.md
rule_type: suggestion
related_rules:
- prefer-spread
---

Suggests using rest parameters instead of `arguments`.

There are rest parameters in ES2015.
We can use that feature for variadic functions instead of the `arguments` variable.

`arguments` does not have methods of `Array.prototype`, so it's a bit of an inconvenience.

## Rule Details

This rule is aimed to flag usage of `arguments` variables.

## Examples

Examples of **incorrect** code for this rule:

::: incorrect

```js
/*eslint prefer-rest-params: "error"*/

function foo() {
    console.log(arguments);
}

function foo(action) {
    var args = Array.prototype.slice.call(arguments, 1);
    action.apply(null, args);
}

function foo(action) {
    var args = [].slice.call(arguments, 1);
    action.apply(null, args);
}
```

:::

Examples of **correct** code for this rule:

::: correct

```js
/*eslint prefer-rest-params: "error"*/

function foo(...args) {
    console.log(args);
}

function foo(action, ...args) {
    action.apply(null, args); // or `action(...args)`, related to the `prefer-spread` rule.
}

// Note: the implicit arguments can be overwritten.
function foo(arguments) {
    console.log(arguments); // This is the first argument.
}
function foo() {
    var arguments = 0;
    console.log(arguments); // This is a local variable.
}
```

:::

## When Not To Use It

This rule should not be used in ES3/5 environments.

In ES2015 (ES6) or later, if you don't want to be notified about `arguments` variables, then it's safe to disable this rule.
