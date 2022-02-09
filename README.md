# Bugs in this repository

## language-tools

* A cryptic error with $$Props + $$Generic + a type intersection in Component.svelte
* Moving some types away into a `context="module"` block in ComponentTwo.svelte resolves the issue, but now the check for if the type of $$Props is valid doesn't seem to be working any more.

## kit

* `npm run package` only produces a type definition file for Base.svelte, but not for Component.svelte / ComponentTwo.svelte / ComponentThree.svelte
