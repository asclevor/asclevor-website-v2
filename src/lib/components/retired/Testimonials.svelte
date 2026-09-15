<script>
	import Avatar from './Avatar.svelte';

	const testimonials = [
		{
			quote:
				'“It was night and day from one batch to another, adoption went from single digits to over 80%. It just spread like wildfire, all the best builders were using Cursor.”',
			name: 'Diana Hu',
			role: 'General Partner, Y Combinator',
			src: '/images/avatar-diana.png',
			initials: 'DH',
			bg: '#C9B8A3'
		},
		{
			quote:
				'“My favorite enterprise AI service is Cursor. Every one of our engineers, some 40,000, are now assisted by AI and our productivity has gone up incredibly.”',
			name: 'Jensen Huang',
			role: 'President & CEO, NVIDIA',
			src: '/images/avatar-jensen.png',
			initials: 'JH',
			bg: '#9FA694'
		},
		{
			quote:
				'“The best LLM applications have an autonomy slider: you control how much independence to give the AI. In Cursor, you can do Cmd+K for targeted edits, or let it rip with the full autonomy agentic version.”',
			name: 'Andrej Karpathy',
			role: 'CEO, Eureka Labs',
			src: '/images/avatar-karpathy.png',
			initials: 'AK',
			bg: '#A9A29B'
		},
		{
			quote:
				"“Cursor quickly grew from hundreds to thousands of extremely enthusiastic Stripe employees. We spend more on R&D and software creation than any other undertaking, and there's significant economic outcomes when making that process more efficient.”",
			name: 'Patrick Collison',
			role: 'Co-Founder & CEO, Stripe',
			src: '/images/avatar-collison.png',
			initials: 'PC',
			bg: '#B9AFC5'
		},
		{
			quote:
				"“The most useful AI tool that I currently pay for, hands down, is Cursor. It's fast, autocompletes when and where you need it to, handles brackets properly, sensible keyboard shortcuts, bring-your-own-model… everything is well put together.”",
			name: 'shadcn',
			role: 'Creator of shadcn/ui',
			src: '/images/avatar-shadcn.png',
			initials: 'SH',
			bg: '#8FA3B8'
		},
		{
			quote:
				"“It's definitely becoming more fun to be a programmer. We are at the 1% of what's possible, and it's in interactive experiences like Cursor where models like GPT-5 shine brightest.”",
			name: 'Greg Brockman',
			role: 'President, OpenAI',
			src: '/images/avatar-brockman.png',
			initials: 'GB',
			bg: '#A3A6AB'
		}
	];
</script>

<section class="mx-auto mt-[118px] w-full max-w-[1300px] px-4 xl:px-0">
	<h2 class="text-center text-[34px] font-normal tracking-[-0.015em]">
		The new way to build software.
	</h2>

	<div class="mt-16 grid gap-3 md:grid-cols-2 lg:grid-cols-3">
		{#each testimonials as t (t.name)}
			<div class="flex flex-col rounded-lg border border-line bg-card p-6">
				<p class="text-[16px] leading-[1.5] text-ink">{t.quote}</p>
				<div class="mt-auto flex items-center gap-3 pt-10">
					<Avatar src={t.src} initials={t.initials} bg={t.bg} class="h-7 w-7 text-[10px]" />
					<div>
						<p class="text-[15px] leading-tight text-ink">{t.name}</p>
						<p class="mt-0.5 text-[15px] leading-tight text-soft">{t.role}</p>
					</div>
				</div>
			</div>
		{/each}
	</div>
</section>
