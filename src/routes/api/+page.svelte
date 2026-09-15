<script>
	import Navbar from '$lib/components/Navbar.svelte';
	import ApiHero from '$lib/components/api/ApiHero.svelte';
	import ApiFeatures from '$lib/components/api/ApiFeatures.svelte';
	import ApiEndpoints from '$lib/components/api/ApiEndpoints.svelte';
	import ApiLearnMore from '$lib/components/api/ApiLearnMore.svelte';
	import ApiCta from '$lib/components/api/ApiCta.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import Seo from '$lib/components/Seo.svelte';
</script>

<Seo
	title="Asclevor API — Clinical Knowledge, Programmatically"
	description="Query the Asclevor clinical knowledge base from your stack with a single API call. Semantic search over 167,000+ patient cases, JSON responses, MCP support. Free to start."
	path="/api"
/>

<Navbar />

<main>
	<ApiHero />
	<ApiFeatures />
	<ApiEndpoints />
	<ApiLearnMore />
	<ApiCta />
</main>

<Footer />
