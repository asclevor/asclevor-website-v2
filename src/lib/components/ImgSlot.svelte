<script>
	/**
	 * Drop-in media slot. Renders an image or video and, while the file is
	 * missing or loading, shows a placeholder label instead (via .img-slot
	 * global styles). Keep dropping files into static/images/ with these
	 * names and they appear automatically.
	 *
	 * Performance behaviour:
	 * - Videos load only when scrolled near the viewport (IntersectionObserver),
	 *   use preload="metadata", and should be given a `poster`.
	 * - Images below the fold are lazy-loaded; pass `priority` for the LCP hero.
	 * - Pass `width`/`height` so the browser can reserve space (CLS).
	 */
	let {
		src,
		alt = '',
		label = '',
		hint = '',
		class: klass = '',
		poster = '',
		priority = false,
		width = undefined,
		height = undefined
	} = $props();

	let loaded = $state(false);
	let failed = $state(false);
	let videoEl = $state(null);
	let imgEl = $state(null);
	let containerEl = $state(null);
	let nearViewport = $state(false);

	const isVideo = /\.(mp4|webm|mov)$/i.test(src ?? '');

	// Defer video loading until the slot is close to the viewport.
	$effect(() => {
		if (!isVideo || !containerEl || nearViewport) return;
		const observer = new IntersectionObserver(
			(entries) => {
				if (entries.some((entry) => entry.isIntersecting)) {
					nearViewport = true;
					observer.disconnect();
				}
			},
			{ rootMargin: '400px' }
		);
		observer.observe(containerEl);
		return () => observer.disconnect();
	});

	$effect(() => {
		// Media can finish loading before hydration attaches the event
		// listeners (cached images, small/fast videos), so also inspect the
		// element state directly once it's mounted.
		if (isVideo && videoEl) {
			videoEl.muted = true; // property is more reliable for autoplay than the attribute
			if (videoEl.error) failed = true;
			else if (videoEl.readyState >= 2) loaded = true;
		} else if (!isVideo && imgEl?.complete) {
			loaded = imgEl.naturalWidth > 0;
			failed = imgEl.naturalWidth === 0;
		}
	});
</script>

<div
	bind:this={containerEl}
	class="img-slot {loaded && !failed ? 'is-loaded' : 'is-empty'} {klass}"
	data-label={label}
	data-hint={hint}
>
	{#if isVideo}
		<video
			bind:this={videoEl}
			src={nearViewport ? src : undefined}
			poster={poster || undefined}
			autoplay
			loop
			muted
			playsinline
			preload={nearViewport ? 'metadata' : 'none'}
			onloadeddata={() => (loaded = true)}
			oncanplay={() => (loaded = true)}
			onplaying={() => (loaded = true)}
			onerror={() => (failed = true)}
		></video>
	{:else}
		<img
			bind:this={imgEl}
			{src}
			{alt}
			loading={priority ? 'eager' : 'lazy'}
			decoding="async"
			fetchpriority={priority ? 'high' : undefined}
			{width}
			{height}
			onload={() => (loaded = true)}
			onerror={() => (failed = true)}
		/>
	{/if}
</div>
