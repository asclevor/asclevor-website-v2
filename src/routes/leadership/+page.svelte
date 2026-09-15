<script>
	import Navbar from '$lib/components/Navbar.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import Seo from '$lib/components/Seo.svelte';
	import { SITE_NAME, SITE_URL } from '$lib/config/site.js';

	// PLACEHOLDERS: Only Leander Guo is a confirmed team member (from the
	// contact page). The bracketed entries below are placeholders — replace
	// names, roles, bios, and add photos to static/images/ before publishing.
	// Photos: drop portrait files into static/images/ and set `img` below.
	const leaders = [
		{
			id: 'ceo',
			name: 'Leander Guo',
			role: 'Chief Executive Officer',
			bio: 'Founded Asclevor to make medical knowledge infrastructure as accessible to developers and researchers as the tools they already use every day.',
			img: '/images/leander-guo.webp',
			initials: 'LG',
			bg: '#B9AFC5'
		}
	];

	const values = [
		{
			title: 'Clinically grounded',
			text: 'We work with real-world clinical cases and associated literature, and we treat sourcing and accuracy as core product work — not an afterthought.'
		},
		{
			title: 'Developer-first',
			text: 'A simple HTTP API, machine-readable JSON, MCP support, and a free tier without artificial data restrictions. We build the tools we would want to use.'
		},
		{
			title: 'Trustworthy infrastructure',
			text: 'Medical data demands care. HTTPS everywhere, plan limits that are enforced fairly, security reviews and contractual SLAs for organizations that need them.'
		}
	];

	const jsonld = [
		{
			'@context': 'https://schema.org',
			'@type': 'WebPage',
			name: `Leadership · ${SITE_NAME}`,
			url: `${SITE_URL}/leadership`
		},
		{
			'@context': 'https://schema.org',
			'@type': 'Person',
			name: 'Leander Guo',
			jobTitle: 'Co-founder & CEO',
			worksFor: { '@type': 'Organization', name: SITE_NAME },
			url: `${SITE_URL}/leadership`
		}
	];
</script>

<Seo
	title="Leadership · Asclevor"
	description="Meet the team behind Asclevor — the people building the knowledge base for medical infrastructure: semantic search over 167,000+ real-world clinical cases."
	path="/leadership"
	{jsonld}
/>

<Navbar />

<main class="mx-auto w-full max-w-[1300px] px-4 pt-[100px] pb-[160px] xl:px-0">
	<!-- Hero -->
	<p class="text-[14px] text-soft">Team</p>
	<h1
		class="mt-2 max-w-[720px] text-[36px] leading-[1.1] tracking-[-0.02em] text-ink sm:text-[44px]"
	>
		The people behind Asclevor.
	</h1>
	<p class="mt-6 max-w-[640px] text-[17px] leading-[1.65] text-soft">
		Asclevor exists because too much medical knowledge remains difficult to access, connect, and use
		programmatically. We're a small team of engineers and researchers building the knowledge base
		for medical infrastructure — one API call at a time.
	</p>

	<!-- Leadership grid -->
	<section class="mt-[80px]">
		<h2 class="text-[24px] tracking-[-0.015em] text-ink">Leadership</h2>
		<div class="mt-8 grid gap-3 sm:grid-cols-2 xl:grid-cols-4">
			{#each leaders as leader (leader.id)}
				<div class="flex flex-col items-start rounded-xl bg-card p-6">
					<!-- Avatar: photo when present, initials fallback otherwise -->
					<span
						class="relative grid h-24 w-24 shrink-0 place-items-center overflow-hidden rounded-full text-[24px] font-bold text-white"
						style:background-color={leader.bg}
					>
						{#if leader.img}
							<img
								src={leader.img}
								alt="Portrait of {leader.name}"
								loading="lazy"
								decoding="async"
								width="96"
								height="96"
								class="absolute inset-0 h-full w-full object-cover"
							/>
						{:else}
							{leader.initials}
						{/if}
					</span>
					<p class="mt-5 text-[19px] font-medium text-ink">{leader.name}</p>
					<p class="mt-1 text-[15px] text-soft">{leader.role}</p>
					<p class="mt-4 text-[15px] leading-[1.55] text-soft">{leader.bio}</p>
				</div>
			{/each}
		</div>
	</section>

	<!-- Values -->
	<section class="mt-[110px]">
		<h2 class="text-[24px] tracking-[-0.015em] text-ink">What we value</h2>
		<div class="mt-8 grid gap-3 md:grid-cols-3">
			{#each values as value (value.title)}
				<div class="rounded-xl bg-card p-6">
					<h3 class="text-[16px] font-medium text-ink">{value.title}</h3>
					<p class="mt-2 text-[15px] leading-[1.5] text-soft">{value.text}</p>
				</div>
			{/each}
		</div>
	</section>

	<!-- CTA -->
	<section class="mt-[140px] text-center">
		<h2 class="text-[44px] leading-none tracking-[-0.02em] text-ink sm:text-[60px]">
			Build with us.
		</h2>
		<p class="mx-auto mt-5 max-w-[520px] text-[17px] leading-[1.6] text-soft">
			Whether you want to partner, integrate the API, or join the team — we'd like to hear from you.
		</p>
		<div class="mt-8 flex flex-wrap justify-center gap-3">
			<a
				href="/contact"
				class="flex h-[42px] items-center rounded-full bg-ink px-6 text-[15px] font-medium text-paper transition-opacity hover:opacity-85"
			>
				Contact the team
			</a>
			<a
				href="https://app.asclevor.com"
				target="_blank"
				rel="noopener noreferrer"
				class="flex h-[42px] items-center rounded-full bg-btn2 px-6 text-[15px] font-medium text-ink transition-colors hover:bg-line"
			>
				Try Asclevor
			</a>
		</div>
	</section>
</main>

<Footer />
