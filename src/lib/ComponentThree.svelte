<script lang="ts" context="module">
	type ValidElementType = 'a' | 'div' | 'span';

	type ElementType = ValidElementType | number;

	type TRestProps<T> = T extends ValidElementType
		? svelte.JSX.HTMLAttributes<HTMLElementTagNameMap[T]>
		: {};

	type TProps<T extends ElementType> = TRestProps<T> & {
		element?: T;
		name: string;
	};
</script>

<script lang="ts">
	type TElement = $$Generic<ElementType>;
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
