<script>
	import Navbar from '$lib/components/Navbar.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import Seo from '$lib/components/Seo.svelte';
	import { SITE_NAME, SITE_URL } from '$lib/config/site.js';

	const jsonld = [
		{
			'@context': 'https://schema.org',
			'@type': 'SoftwareApplication',
			name: SITE_NAME,
			applicationCategory: 'BusinessApplication',
			operatingSystem: 'Web',
			url: `${SITE_URL}/pricing`,
			offers: [
				{ '@type': 'Offer', name: 'Free', price: '0', priceCurrency: 'USD' },
				{ '@type': 'Offer', name: 'Developer', price: '29', priceCurrency: 'USD' },
				{ '@type': 'Offer', name: 'Pro', price: '99', priceCurrency: 'USD' }
			]
		}
	];

	let billing = $state('monthly');
	let open = $state(-1);

	const plans = [
		{
			name: 'Free',
			tagline: 'For exploration and research',
			price: { monthly: '$0', yearly: '$0' },
			suffix: '/mo.',
			chips: null,
			includesLabel: 'Includes:',
			features: [
				'10,000 requests / month',
				'20 requests / minute',
				'No API key required',
				'Case Search',
				'Similar Patients',
				'MCP access',
				'JSON API'
			],
			cta: { label: 'Try Asclevor', href: 'https://app.asclevor.com', primary: false }
		},
		{
			name: 'Developer',
			tagline: 'For building applications',
			price: { monthly: '$29', yearly: '$24' },
			suffix: '/mo.',
			chips: null,
			includesLabel: 'Everything in Free, plus:',
			features: [
				'100,000 requests / month',
				'120 requests / minute',
				'API key',
				'All API endpoints',
				'MCP access',
				'Usage analytics',
				'Email support'
			],
			cta: { label: 'Contact sales', href: '/contact', primary: true }
		},
		{
			name: 'Pro',
			tagline: 'For production workloads',
			price: { monthly: '$99', yearly: '$79' },
			suffix: '/mo.',
			chips: null,
			includesLabel: 'Everything in Developer, plus:',
			features: [
				'1,000,000 requests / month',
				'600 requests / minute',
				'Advanced analytics',
				'Priority support',
				'Higher concurrency',
				'Production usage',
				'Priority API access'
			],
			cta: { label: 'Contact sales', href: '/contact', primary: true }
		},
		{
			name: 'Enterprise',
			tagline: 'For scaled organizations',
			price: { monthly: 'Custom', yearly: 'Custom' },
			suffix: '',
			chips: null,
			includesLabel: 'Everything in Pro, plus:',
			features: [
				'Custom request limits',
				'Custom rate limits',
				'Dedicated infrastructure',
				'Bulk data access',
				'Custom integrations',
				'Security review',
				'Dedicated support',
				'Contractual SLA'
			],
			cta: { label: 'Contact sales', href: '/contact', primary: true }
		}
	];

	const faqs = [
		{
			q: 'Do I need an API key to use Asclevor?',
			a: 'No. The Free plan works without an API key and provides access to the API at up to 20 requests per minute. API keys are available on paid plans for higher limits and production use.'
		},
		{
			q: 'What counts as a request?',
			a: 'Each API request to an Asclevor endpoint counts toward your monthly request limit. This includes case search, patient retrieval, similar-patient searches, and other API operations.'
		},
		{
			q: 'Can I use Asclevor for free?',
			a: 'Yes. The Free plan includes 10,000 requests per month, a 20 requests-per-minute rate limit, Case Search, Similar Patients, MCP access, and JSON API access.'
		},
		{
			q: 'Can I use the Free plan in a production application?',
			a: 'Yes, provided your usage stays within the Free plan limits and complies with our <a href="/terms" class="underline underline-offset-2 hover:opacity-70">Terms of Service</a>. For higher-volume production applications, we recommend the Developer or Pro plan.'
		},
		{
			q: 'What happens when I reach my monthly limit?',
			a: 'Requests are paused until your monthly quota resets or you upgrade to a higher plan. We do not automatically charge overage fees.'
		},
		{
			q: 'Can I upgrade or downgrade at any time?',
			a: 'Yes. You can change your plan at any time. Your new limits take effect according to the plan and billing period associated with your account.'
		},
		{
			q: 'Is MCP included?',
			a: 'Yes. MCP access is included across all plans. The Free plan can be used without an API key, while paid plans provide higher capacity for production workloads.'
		},
		{
			q: 'Do paid plans provide different medical data?',
			a: 'No. Plans primarily differ in usage limits, rate limits, and support. We do not artificially restrict the underlying case search to make the free tier less useful.'
		},
		{
			q: 'Do you offer enterprise plans?',
			a: 'Yes. Enterprise plans are designed for organizations requiring higher throughput, custom limits, dedicated infrastructure, bulk data access, custom integrations, or contractual SLAs.'
		},
		{
			q: 'Is there a free trial for paid plans?',
			a: 'The Free plan is available indefinitely, so you can evaluate Asclevor before paying. We do not require a separate trial period.'
		},
		{
			q: 'Can I cancel my subscription?',
			a: 'Yes. Paid subscriptions can be cancelled at any time. Your account remains available according to the applicable billing period.'
		},
		{
			q: 'Is Asclevor medical advice?',
			a: 'No. Asclevor provides access to medical case data and retrieval infrastructure. It is not a diagnostic system and should not be used as a substitute for professional medical judgment.'
		}
	];

	function toggleFaq(i) {
		open = open === i ? -1 : i;
	}
</script>

<Seo
	title="Asclevor Pricing — Free, Developer, Pro & Enterprise Plans"
	description="Start free with 10,000 API requests per month, no key required. Scale to Developer and Pro for higher limits, or talk to sales about Enterprise."
	path="/pricing"
	{jsonld}
/>

<Navbar />

<main>
	<!-- Heading + billing toggle + plan cards -->
	<div class="mx-auto w-full max-w-[1300px] px-4 pt-[100px] xl:px-0">
		<h1 class="text-center text-[44px] leading-none tracking-[-0.02em] text-ink">Pricing</h1>

		<div class="mt-6 flex justify-center">
			<div class="flex items-center gap-1 rounded-full bg-card p-1">
				<button
					onclick={() => (billing = 'monthly')}
					aria-pressed={billing === 'monthly'}
					class="h-8 rounded-full px-4 text-[14px] transition-colors {billing === 'monthly'
						? 'bg-btn2 text-ink'
						: 'text-soft hover:text-ink'}"
				>
					Monthly
				</button>
				<button
					onclick={() => (billing = 'yearly')}
					aria-pressed={billing === 'yearly'}
					class="h-8 rounded-full px-4 text-[14px] transition-colors {billing === 'yearly'
						? 'bg-btn2 text-ink'
						: 'text-soft hover:text-ink'}"
				>
					Yearly
				</button>
			</div>
		</div>

		<div class="mt-10 grid gap-3 md:grid-cols-2 xl:grid-cols-4">
			{#each plans as plan (plan.name)}
				<div class="flex flex-col rounded-xl bg-card p-6">
					<p class="text-[19px] font-medium text-ink">{plan.name}</p>
					<p class="mt-1 text-[15px] text-soft">{plan.tagline}</p>

					<p class="mt-8 text-[40px] leading-none font-medium tracking-[-0.01em] text-ink">
						{plan.price[billing]}{#if plan.suffix}<span
								class="ml-1 text-[16px] font-normal text-soft">{plan.suffix}</span
							>{/if}
					</p>

					{#if plan.chips}
						<div class="mt-6 inline-flex w-fit items-center rounded-full bg-btn2 p-1">
							{#each plan.chips as chip, i (chip)}
								<span
									class="rounded-full px-3.5 py-1 text-[14px] {i === 0
										? 'bg-[#d2d1cc] font-medium text-ink'
										: 'px-2.5 text-soft'}">{chip}</span
								>
							{/each}
						</div>
					{/if}

					<p class="mt-10 text-[15px] text-soft">{plan.includesLabel}</p>
					<ul class="mt-5 flex-1 space-y-3">
						{#each plan.features as feature (feature)}
							<li class="flex items-start gap-2.5 text-[15px] leading-[1.4] text-ink">
								<svg
									class="mt-[3px] shrink-0 text-ink"
									width="14"
									height="14"
									viewBox="0 0 16 16"
									fill="none"
									aria-hidden="true"
								>
									<path
										d="m3 8.5 3.2 3L13 4.5"
										stroke="currentColor"
										stroke-width="1.5"
										stroke-linecap="round"
										stroke-linejoin="round"
									/>
								</svg>
								{feature}
							</li>
						{/each}
					</ul>

					<a
						href={plan.cta.href}
						class="mt-8 inline-flex h-9 w-fit items-center rounded-full px-4 text-[15px] font-medium transition-colors {plan
							.cta.primary
							? 'bg-ink text-paper hover:opacity-85'
							: 'bg-btn2 text-ink hover:bg-line'}"
					>
						{plan.cta.label}
					</a>
				</div>
			{/each}
		</div>

		<!-- Trusted by -->
		<p class="mt-16 text-center text-[14px] text-ink">
			Trusted every day by teams that build world-class software.
		</p>
	</div>

	<!-- Questions & Answers (full-bleed band) -->
	<section class="mt-[140px] w-full bg-card">
		<div
			class="mx-auto grid w-full max-w-[1300px] gap-16 px-4 py-24 lg:grid-cols-[1fr_1.55fr] lg:gap-12 xl:px-0"
		>
			<h2 class="text-[34px] leading-tight tracking-[-0.015em] text-ink">
				Questions &amp; Answers
			</h2>

			<div class="border-t border-line">
				{#each faqs as faq, i (faq.q)}
					<div class="border-b border-line">
						<button
							onclick={() => toggleFaq(i)}
							aria-expanded={open === i}
							class="flex w-full items-center justify-between gap-4 py-5 text-left"
						>
							<span class="text-[16px] text-ink">{faq.q}</span>
							<svg
								class="shrink-0 text-soft transition-transform {open === i ? 'rotate-180' : ''}"
								width="16"
								height="16"
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
						</button>
						{#if open === i}
							<p class="pr-8 pb-5 text-[15px] leading-[1.55] text-soft">{@html faq.a}</p>
						{/if}
					</div>
				{/each}
			</div>
		</div>
	</section>

	<!-- Final CTA -->
	<section class="mx-auto w-full max-w-[1300px] px-4 pt-[150px] pb-[160px] text-center xl:px-0">
		<h2 class="text-[52px] leading-none tracking-[-0.02em] sm:text-[68px]">
			Get started with Asclevor.
		</h2>
		<div class="mt-8 flex flex-wrap justify-center gap-3">
			<a
				href="https://app.asclevor.com"
				target="_blank"
				class="flex h-[42px] items-center gap-2 rounded-full bg-ink px-6 text-[15px] font-medium text-paper transition-opacity hover:opacity-85"
			>
				Open Case Search
			</a>
			<a
				href="/contact"
				class="flex h-[42px] items-center rounded-full bg-btn2 px-6 text-[15px] font-medium text-ink transition-colors hover:bg-line"
			>
				Contact Sales
			</a>
		</div>
	</section>
</main>

<Footer />
