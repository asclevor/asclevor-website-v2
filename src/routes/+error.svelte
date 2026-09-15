<script>
	import { page } from '$app/state';
	import Navbar from '$lib/components/Navbar.svelte';
	import Footer from '$lib/components/Footer.svelte';
</script>

<svelte:head>
	<title>Page not found · Asclevor</title>
	<meta name="robots" content="noindex" />
</svelte:head>

<Navbar />

<main
	class="mx-auto flex min-h-[60vh] w-full max-w-[1300px] flex-col justify-center px-4 pt-[100px] pb-[120px] xl:px-0"
>
	<p class="text-[14px] text-soft">404</p>
	<h1 class="mt-2 text-[36px] leading-[1.1] tracking-[-0.02em] text-ink sm:text-[44px]">
		This page doesn't exist.
	</h1>
	<p class="mt-4 max-w-[520px] text-[16px] leading-[1.55] text-soft">
		The page you're looking for may have moved. Try the
		<a href="/" class="text-accent transition-opacity hover:opacity-80">homepage</a>, the
		<a href="/api" class="text-accent transition-opacity hover:opacity-80">API</a>, or
		<a href="/pricing" class="text-accent transition-opacity hover:opacity-80">pricing</a>.
	</p>
</main>

<Footer />
