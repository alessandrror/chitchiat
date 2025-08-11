<script lang="ts">
	import type { HTMLAttributes } from 'svelte/elements';

	type TooltipProps = {
		title?: string;
		description?: string;
		position?: 'top' | 'bottom' | 'left' | 'right';
	} & HTMLAttributes<HTMLElement>;

	let show = $state(false);
	let showTimeout: ReturnType<typeof setTimeout> | null = null;
	let hideTimeout: ReturnType<typeof setTimeout> | null = null;

	let { children, title, description, position = 'top' }: TooltipProps = $props();

	const positionClasses = {
		top: 'bottom-full left-1/2 -translate-x-1/2 mb-3',
		bottom: 'top-full left-1/2 -translate-x-1/2 mt-3',
		left: 'right-full top-1/2 -translate-y-1/2 mr-3',
		right: 'left-full top-1/2 -translate-y-1/2 ml-3'
	};

	const delayShow = (ms = 150) => {
		if (hideTimeout) {
			clearTimeout(hideTimeout);
			hideTimeout = null;
		}
		if (!show) {
			showTimeout = setTimeout(() => (show = true), ms);
		}
	};

	const delayHide = (ms = 150) => {
		if (showTimeout) {
			clearTimeout(showTimeout);
			showTimeout = null;
		}
		hideTimeout = setTimeout(() => (show = false), ms);
	};
</script>

<div
	role="dialog"
	tabindex="0"
	class="group relative w-full"
	onblur={() => delayHide()}
	onfocus={() => delayShow()}
	onmouseenter={() => delayShow()}
	onmouseleave={() => delayHide()}
>
	{@render children?.()}
	{#if show}
		<div
			role="tooltip"
			class={` absolute z-50 w-auto rounded-lg bg-gray-900 p-3 text-white opacity-100 shadow-lg transition-opacity duration-300 ${positionClasses[position]}`}
		>
			{#if title}
				<div class="mb-1 text-base font-semibold text-nowrap">{title}</div>
			{/if}
			{#if description}
				<div class="text-sm text-nowrap opacity-80">{description}</div>
			{/if}
		</div>
	{/if}
</div>
