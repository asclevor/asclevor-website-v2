<script>
	import ImgSlot from '../ImgSlot.svelte';

	const cards = [
		{
			title: 'Use the best model for every task',
			text: 'Choose between every cutting-edge model from OpenAI, Anthropic, Gemini, SpaceXAI, and Cursor.',
			link: 'Explore models',
			img: '/images/model-picker.png',
			label: 'Image placeholder — model picker',
			hint: 'static/images/model-picker.png · ~800 × 800'
		},
		{
			title: 'Build with autonomous agents',
			text: 'Launch fleets of agents that work in parallel on ambitious tasks for hours or days.',
			link: 'Learn about cloud agents',
			img: '/images/mobile-agents.png',
			label: 'Image placeholder — mobile agents UI',
			hint: 'static/images/mobile-agents.png · ~800 × 800'
		},
		{
			title: 'Develop enduring software',
			text: 'Trusted by over half of the Fortune 500 to accelerate development, securely and at scale.',
			link: 'Explore enterprise',
			img: '/images/enterprise.png',
			label: 'Image placeholder — enterprise',
			hint: 'static/images/enterprise.png · ~800 × 800'
		}
	];
</script>

<section class="mx-auto mt-[138px] w-full max-w-[1300px] px-4 xl:px-0">
	<h2 class="text-[21px] tracking-[-0.01em]">Stay on the frontier</h2>

	<div class="mt-6 grid gap-4 md:grid-cols-2 lg:grid-cols-3">
		{#each cards as card (card.title)}
			<div class="rounded-xl bg-card p-4">
				<div class="px-1">
					<h3 class="text-[17px] font-medium text-ink">{card.title}</h3>
					<p class="mt-1.5 text-[16px] leading-[1.45] text-soft">{card.text}</p>
					<a href="#" class="group mt-4 inline-flex items-center gap-1 text-[16px] text-accent">
						{card.link}
						<svg
							class="transition-transform group-hover:translate-x-0.5 group-hover:-translate-y-0.5"
							width="14"
							height="14"
							viewBox="0 0 16 16"
							fill="none"
						>
							<path
								d="M4 12 12 4m0 0H5.5M12 4v6.5"
								stroke="currentColor"
								stroke-width="1.5"
								stroke-linecap="round"
								stroke-linejoin="round"
							/>
						</svg>
					</a>
				</div>
				<ImgSlot
					src={card.img}
					alt={card.title}
					label={card.label}
					hint={card.hint}
					class="mt-5 aspect-square w-full rounded-lg bg-frame"
				/>
			</div>
		{/each}
	</div>
</section>
