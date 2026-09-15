<script>
	import Navbar from '$lib/components/Navbar.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import Avatar from '$lib/components/Avatar.svelte';
	import Seo from '$lib/components/Seo.svelte';
	import { SITE_NAME, SITE_URL } from '$lib/config/site.js';

	let email = $state('');
	let topic = $state('');
	let attempted = $state(false);
	let submitted = $state(false);

	const emailValid = $derived(/^[^\s@]+@[^\s@]+\.[^\s@]{2,}$/.test(email.trim()));
	const topicValid = $derived(topic !== '');
	const emailError = $derived(attempted && !emailValid);
	const topicError = $derived(attempted && !topicValid);

	// No backend yet — a valid submit opens the visitor's mail client with a
	// pre-filled message. Swap this for a real endpoint/form action later.
	const CONTACT_EMAIL = 'contact@asclevor.com';

	const jsonld = [
		{
			'@context': 'https://schema.org',
			'@type': 'ContactPage',
			name: `Contact ${SITE_NAME}`,
			url: `${SITE_URL}/contact`,
			about: {
				'@type': 'Organization',
				name: SITE_NAME,
				url: SITE_URL,
				email: CONTACT_EMAIL
			}
		}
	];

	function submit(event) {
		event.preventDefault();
		attempted = true;
		if (!emailValid || !topicValid) return;

		const subject = `Contact request: ${topic}`;
		const body = [
			'Hi Asclevor team,',
			'',
			'I reached out via the website contact form.',
			'',
			`Work email: ${email.trim()}`,
			`Topic: ${topic}`
		].join('\n');

		window.location.href = `mailto:${CONTACT_EMAIL}?subject=${encodeURIComponent(
			subject
		)}&body=${encodeURIComponent(body)}`;
		submitted = true;
	}
</script>

<Seo
	title="Contact Asclevor — Sales, Demos & Support"
	description="Talk to the Asclevor team about Enterprise plans, demos, security and compliance, billing, or support. We typically respond within one business day."
	path="/contact"
	{jsonld}
/>

<Navbar />

<main class="mx-auto w-full max-w-[1300px] px-4 pt-[100px] pb-[160px] xl:px-0">
	<div class="grid gap-16 lg:grid-cols-2 lg:gap-12">
		<!-- Left: headline, customer story, logos -->
		<div>
			<h1 class="text-[36px] leading-[1.1] tracking-[-0.02em] sm:text-[44px]">Contact us</h1>

			<figure class="mt-12 rounded-lg border border-line bg-card p-8">
				<blockquote class="text-[17px] leading-[1.55] text-ink">
					Medicine produces an enormous amount of knowledge, but too much of it remains difficult to
					access, connect, and use programmatically. We built Asclevor to change that. Our goal is
					simple: make medical knowledge infrastructure as accessible to developers and researchers
					as the tools they already use every day.
				</blockquote>
				<figcaption class="mt-8 flex items-center gap-3">
					<Avatar
						src="/images/leander-guo.webp"
						initials="PC"
						bg="#B9AFC5"
						class="h-10 w-10 text-[12px]"
					/>
					<div>
						<p class="text-[15px] leading-tight text-ink">Leander Guo</p>
						<p class="mt-0.5 text-[15px] leading-tight text-soft">CEO, Asclevor</p>
					</div>
				</figcaption>
			</figure>

			<!-- Direct contact + enterprise pointers -->
			<div class="mt-10 space-y-4 text-[15px] leading-[1.6] text-soft">
				<p>
					Prefer email? Write to
					<a href="mailto:{CONTACT_EMAIL}" class="text-accent transition-opacity hover:opacity-80"
						>{CONTACT_EMAIL}</a
					> and we'll get back to you.
				</p>
				<p>
					Enterprise inquiries: dedicated infrastructure, bulk data access, custom integrations,
					security review, and contractual SLAs — pick
					<span class="text-ink">Enterprise sales</span> above to start the conversation.
				</p>
			</div>
		</div>

		<!-- Right: contact form -->
		<div class="h-fit rounded-xl border border-line bg-paper p-8 sm:p-10">
			{#if submitted}
				<div class="flex min-h-[380px] flex-col items-start justify-center">
					<h2 class="text-[26px] tracking-[-0.01em] text-ink">Thanks — one more step.</h2>
					<p class="mt-3 text-[16px] leading-[1.5] text-soft">
						Your mail client should have opened with a message pre-filled for
						<a href="mailto:{CONTACT_EMAIL}" class="text-accent transition-opacity hover:opacity-80"
							>{CONTACT_EMAIL}</a
						>. Just hit send and we'll get back to you at
						<span class="text-ink">{email}</span>.
					</p>
				</div>
			{:else}
				<form onsubmit={submit} novalidate>
					<h2 class="text-[26px] tracking-[-0.01em] text-ink">Contact our team</h2>

					<label for="work-email" class="mt-8 block text-[15px] text-ink">
						Work email <span class="text-accent">*</span>
					</label>
					<input
						id="work-email"
						type="email"
						bind:value={email}
						placeholder="jane@acme.co"
						autocomplete="email"
						class="mt-3 h-[52px] w-full rounded-lg border bg-white px-4 text-[16px] text-ink transition-colors outline-none placeholder:text-soft/70 {emailError
							? 'border-[#d14343]'
							: 'border-line focus:border-ink/40'}"
					/>
					{#if emailError}
						<p class="mt-2 text-[14px] text-[#d14343]">Please enter a valid work email address</p>
					{/if}

					<label for="topic" class="mt-6 block text-[15px] text-ink">
						What can we help you with? <span class="text-accent">*</span>
					</label>
					<div class="relative mt-3">
						<select
							id="topic"
							bind:value={topic}
							class="h-[52px] w-full appearance-none rounded-lg border bg-white px-4 pr-10 text-[16px] transition-colors outline-none {topicError
								? 'border-[#d14343]'
								: 'border-line focus:border-ink/40'} {topic === '' ? 'text-soft/80' : 'text-ink'}"
						>
							<option value="" disabled>Select one</option>
							<option>Enterprise sales</option>
							<option>Request a demo</option>
							<option>Billing &amp; plans</option>
							<option>Security &amp; compliance</option>
							<option>Support</option>
							<option>Something else</option>
						</select>
						<svg
							class="pointer-events-none absolute top-1/2 right-4 -translate-y-1/2 text-soft"
							width="14"
							height="14"
							viewBox="0 0 16 16"
							fill="none"
						>
							<path
								d="m4 6 4 4 4-4"
								stroke="currentColor"
								stroke-width="1.5"
								stroke-linecap="round"
								stroke-linejoin="round"
							/>
						</svg>
					</div>
					{#if topicError}
						<p class="mt-2 text-[14px] text-[#d14343]">Please select what we can help you with</p>
					{/if}

					<button
						type="submit"
						class="mt-8 inline-flex h-[46px] items-center gap-2 rounded-full bg-ink px-6 text-[15px] font-medium text-paper transition-opacity hover:opacity-85"
					>
						Continue
						<svg width="15" height="15" viewBox="0 0 16 16" fill="none">
							<path
								d="M2.5 8h11m0 0L9 3.5M13.5 8 9 12.5"
								stroke="currentColor"
								stroke-width="1.5"
								stroke-linecap="round"
								stroke-linejoin="round"
							/>
						</svg>
					</button>
				</form>
			{/if}
		</div>
	</div>
</main>

<Footer />
