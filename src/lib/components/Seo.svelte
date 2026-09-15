<script>
	/**
	 * Shared SEO head: title, meta description, canonical, Open Graph,
	 * Twitter cards, and any JSON-LD blocks (pass an array of objects).
	 *
	 * Usage:
	 *   <Seo title="…" description="…" path="/pricing" jsonld={[{…}]} />
	 */
	import { SITE_URL, SITE_NAME, DEFAULT_OG_IMAGE, TWITTER_HANDLE } from '$lib/config/site.js';

	let {
		title,
		description,
		path = '/',
		ogType = 'website',
		ogImage = DEFAULT_OG_IMAGE,
		jsonld = []
	} = $props();

	const canonical = `${SITE_URL}${path === '/' ? '/' : path}`;
	const ogImageAbs = ogImage.startsWith('http') ? ogImage : `${SITE_URL}${ogImage}`;
</script>

<svelte:head>
	<title>{title}</title>
	<meta name="description" content={description} />
	<link rel="canonical" href={canonical} />

	<!-- Open Graph -->
	<meta property="og:site_name" content={SITE_NAME} />
	<meta property="og:type" content={ogType} />
	<meta property="og:title" content={title} />
	<meta property="og:description" content={description} />
	<meta property="og:url" content={canonical} />
	<meta property="og:image" content={ogImageAbs} />
	<meta property="og:image:width" content="1200" />
	<meta property="og:image:height" content="630" />

	<!-- Twitter -->
	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:site" content={TWITTER_HANDLE} />
	<meta name="twitter:title" content={title} />
	<meta name="twitter:description" content={description} />
	<meta name="twitter:image" content={ogImageAbs} />

	{#each jsonld as block (block['@type'])}
		<!-- eslint-disable-next-line svelte/no-at-html-tags -- static, JSON.stringify'd with < escaped -->
		{@html `<script type="application/ld+json">${JSON.stringify(block).replaceAll('<', '\\u003c')}</script>`}
	{/each}
</svelte:head>
