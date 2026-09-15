<script>
	import Navbar from '$lib/components/Navbar.svelte';
	import Hero from '$lib/components/Hero.svelte';
	import Features from '$lib/components/Features.svelte';
	import About from '$lib/components/About.svelte';
	import FinalCta from '$lib/components/FinalCta.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import Seo from '$lib/components/Seo.svelte';
	import { SITE_NAME, SITE_URL } from '$lib/config/site.js';

	const jsonld = [
		{
			'@context': 'https://schema.org',
			'@type': 'WebSite',
			name: SITE_NAME,
			url: SITE_URL
		},
		{
			'@context': 'https://schema.org',
			'@type': 'SoftwareApplication',
			name: SITE_NAME,
			applicationCategory: 'BusinessApplication',
			operatingSystem: 'Web',
			description:
				'Asclevor is a knowledge base for medical infrastructure: semantic search over 167,000+ real-world clinical cases, accessible via JSON API and MCP.',
			url: SITE_URL,
			offers: {
				'@type': 'Offer',
				price: '0',
				priceCurrency: 'USD',
				description: 'Free plan with 10,000 requests/month; paid plans for higher limits.'
			}
		}
	];
</script>

<Seo
	title="Asclevor — Clinical Knowledge Infrastructure"
	description="Asclevor is a knowledge base for medical infrastructure: semantic search over 167,000+ real-world patient cases via a simple JSON API and MCP. Start free."
	path="/"
	{jsonld}
/>

<Navbar />

<main>
	<Hero />
	<Features />
	<About />
	<FinalCta />
</main>

<Footer />
