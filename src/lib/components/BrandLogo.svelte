<script>
	/**
	 * Company logo slot. Shows static/images/logo-*.png when present,
	 * otherwise falls back to a styled text wordmark (children snippet).
	 */
	let { name, src = '', children } = $props();

	let imgEl = $state(null);
	let hasImg = $state(false);

	$effect(() => {
		// Cached images can finish loading before hydration attaches onload.
		if (imgEl?.complete) hasImg = imgEl.naturalWidth > 0;
	});
</script>

<span class="flex h-10 items-center">
	{#if src}
		<img
			bind:this={imgEl}
			{src}
			alt={name}
			class="max-h-10 w-auto max-w-[150px] object-contain"
			class:hidden={!hasImg}
			onload={() => (hasImg = true)}
			onerror={() => (hasImg = false)}
		/>
	{/if}
	{#if !hasImg}
		{@render children?.()}
	{/if}
</span>
