<script>
	import Navbar from '$lib/components/Navbar.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import Seo from '$lib/components/Seo.svelte';
	import { SITE_NAME, SITE_URL } from '$lib/config/site.js';

	// Photos live in static/images/. Descriptive filenames + alt text +
	// captions + JSON-LD image data + image sitemap entries help Google
	// index them in Google Images.
	const leader = {
		name: 'Leander Guo',
		role: 'Co-founder & CEO',
		bio: 'Founded Asclevor to make medical knowledge infrastructure as accessible to developers and researchers as the tools they already use every day.',
		photos: [
			{
				src: '/images/leander-e-guo-portrait.webp',
				alt: 'Portrait of Leander Guo, co-founder and CEO of Asclevor, wearing a navy suit in front of a bookshelf',
				width: 1000,
				height: 1000,
				caption: ''
			},
			{
				src: '/images/leander-e-guo-speaking.webp',
				alt: 'Leander Guo, CEO of Asclevor, speaking at a conference podium',
				width: 711,
				height: 728,
				caption: 'Speaking at a conference'
			},
			{
				src: '/images/leander-e-guo-university-talk.webp',
				alt: 'Leander Guo giving a university guest lecture on medical knowledge infrastructure',
				width: 583,
				height: 557,
				caption: 'University guest lecture'
			}
		]
	};

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
			url: `${SITE_URL}/leadership`,
			image: leader.photos.map((photo) => ({
				'@type': 'ImageObject',
				contentUrl: `${SITE_URL}${photo.src}`,
				name: photo.alt,
				caption: photo.caption || photo.alt,
				width: photo.width,
				height: photo.height
			}))
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

	<!-- Leadership -->
	<section class="mt-[80px]">
		<h2 class="text-[24px] tracking-[-0.015em] text-ink">Leadership</h2>
		<div class="mt-8 grid gap-3 lg:grid-cols-[minmax(0,440px)_1fr]">
			<!-- Featured portrait -->
			<figure class="overflow-hidden rounded-xl bg-card">
				<img
					src={leader.photos[0].src}
					alt={leader.photos[0].alt}
					width={leader.photos[0].width}
					height={leader.photos[0].height}
					decoding="async"
					class="h-full w-full object-cover"
				/>
			</figure>

			<div class="flex flex-col rounded-xl bg-card p-6 sm:p-8">
				<p class="text-[26px] font-medium tracking-[-0.01em] text-ink">{leader.name}</p>
				<p class="mt-1 text-[15px] text-soft">{leader.role}</p>
				<p class="mt-4 max-w-[560px] text-[15px] leading-[1.55] text-soft">{leader.bio}</p>

				<!-- Speaking photos -->
				<div class="mt-8 grid gap-4 sm:grid-cols-2">
					{#each leader.photos.slice(1) as photo (photo.src)}
						<figure>
							<img
								src={photo.src}
								alt={photo.alt}
								width={photo.width}
								height={photo.height}
								loading="lazy"
								decoding="async"
								class="h-auto w-full rounded-lg object-cover"
							/>
							<figcaption class="mt-2 text-[13px] leading-[1.45] text-soft">
								{leader.name} — {photo.caption}
							</figcaption>
						</figure>
					{/each}
				</div>
			</div>
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
