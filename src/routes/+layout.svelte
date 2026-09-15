<script>
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';
	import { SITE_URL, SITE_NAME, SOCIAL_LINKS } from '$lib/config/site.js';

	let { children } = $props();

	const organizationSchema = {
		'@context': 'https://schema.org',
		'@type': 'Organization',
		name: SITE_NAME,
		url: SITE_URL,
		logo: `${SITE_URL}/logo.svg`,
		sameAs: SOCIAL_LINKS
	};
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	{@html `<script type="application/ld+json">${JSON.stringify(organizationSchema).replaceAll('<', '\\u003c')}</script>`}
</svelte:head>
{@render children()}
