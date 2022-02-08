<script lang="ts">
	type ElementType = 'a' | 'div' | 'span';
	type TRestProps<TAsProp> = TAsProp extends ElementType
		? svelte.JSX.HTMLAttributes<HTMLElementTagNameMap[TAsProp]>
		: {};

	type TElement = $$Generic<ElementType>;
	// This errors with `Argument of type '{element: ElementType; name: string; }' is not assignable to parameter of type Partial<$$Props>
	// type $$Props = TRestProps<TElement> & {
	// 	element?: TElement;
	// 	name: string;
	// };
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
