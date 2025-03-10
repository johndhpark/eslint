---
title: no-delete-var
layout: doc
edit_link: https://github.com/eslint/eslint/edit/main/docs/src/rules/no-delete-var.md
rule_type: suggestion
---

<!--RECOMMENDED-->

Disallows deleting variables.

The purpose of the `delete` operator is to remove a property from an object. Using the `delete` operator on a variable might lead to unexpected behavior.

## Rule Details

This rule disallows the use of the `delete` operator on variables.

If ESLint parses code in strict mode, the parser (instead of this rule) reports the error.

Examples of **incorrect** code for this rule:

::: incorrect

```js
/*eslint no-delete-var: "error"*/

var x;
delete x;
```

:::
