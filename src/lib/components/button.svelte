<script lang="ts">
	import type { HTMLButtonAttributes, SvelteHTMLElements } from 'svelte/elements';
	import { twMerge } from 'tailwind-merge';

	const sizes = [
		20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43,
		44, 45, 46, 47, 48
	] as const;
	type Size = (typeof sizes)[number];

	const variants = ['outlined', 'rounded', 'sharp'] as const;
	type Variant = (typeof variants)[number];

	const weights = [100, 200, 300, 400, 500, 600, 700] as const;
	type Weight = (typeof weights)[number];

	type Icon = {
		name: string;
		size?: Size;
		weight?: Weight;
		variant?: Variant;
	} & SvelteHTMLElements['i'];

	let { icon, children, ...rest }: HTMLButtonAttributes & { icon?: Icon } = $props();
</script>

{#snippet iconSnippet({ name, size, variant, weight, class: className }: Icon)}
	<i
		class={twMerge(
			className?.toString(),
			`material-symbols-${variant ?? variants.at(0)} fixed left-4 mx-auto`
		)}
		style={`font-variation-settings: 'FILL' 0, 'wght' ${weight ?? weights.at(0)}, 'GRAD' 0, 'opsz' ${size ?? sizes.at(0)}`}
	>
		{name}
	</i>
{/snippet}

<button
	{...rest}
	type={rest?.type ?? 'button'}
	class={twMerge(
		rest.class?.toString(),
		'relative flex cursor-pointer items-center justify-center rounded-full p-2 hover:bg-gray-800 active:bg-gray-700'
	)}
>
	{#if icon}
		{@render iconSnippet({ ...icon })}
	{/if}
	{@render children?.()}
</button>
