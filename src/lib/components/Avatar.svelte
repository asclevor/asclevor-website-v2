<script>
	/**
	 * Small round avatar. Shows images/avatar-*.png when present,
	 * otherwise falls back to `initials` or a custom snippet (e.g. a logo).
	 */
	let { src = '', initials = '', bg = '#cccccc', class: klass = 'h-7 w-7', children } = $props();

	let hasImg = $state(false);
</script>

<span
	class="avatar-slot grid {klass} place-items-center overflow-hidden rounded-full font-bold text-ink"
	style:background-color={bg}
>
	{#if src}
		<img
			{src}
			alt=""
			class:hidden={!hasImg}
			onload={() => (hasImg = true)}
			onerror={() => (hasImg = false)}
		/>
	{/if}
	{#if !hasImg}
		{@render children?.()}
	{/if}
</span>
