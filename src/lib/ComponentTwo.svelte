<script lang="ts" context="module">
	type ElementType = 'a' | 'div' | 'span';
	type TRestProps<TAsProp> = TAsProp extends ElementType
		? svelte.JSX.HTMLAttributes<HTMLElementTagNameMap[TAsProp]>
		: {};

	type TProps<T extends ElementType> = TRestProps<T> & {
		element?: T;
		name: string;
	};
</script>

<script lang="ts">
	type TElement = $$Generic<ElementType>;

	// This is the same type as Component.svelte, but now there's no error.

	// But now it seems to have also lost the safety checks it was doing.
	// You can delete the `name` prop from TProps above, or change it to a different type
	// like `number`, and it will not error.
	type $$Props = TProps<TElement>;
	export let element: ElementType = 'div';
	export let name: string;
</script>

{#if element === 'a'}
	<a href="#test" {...$$restProps}>Hello, {name}</a>
{:else if element === 'div'}
	<div {...$$restProps}>Hello, {name}</div>
{:else if element === 'span'}
	<span {...$$restProps}>Hello, {name}</span>
{/if}
