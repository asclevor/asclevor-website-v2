<script>
	import ImgSlot from '../ImgSlot.svelte';

	const cards = [
		{
			title: 'Access over 167,000 real-world patient cases',
			text: 'Search a large corpus of clinical cases and their associated medical literature through a single API.',
			img: '/images/api-167.png',
			label: 'Image placeholder — search results'
		},
		{
			title: 'Find clinically similar cases, not just keywords',
			text: 'Use semantic search to surface relevant patient cases based on clinical meaning, symptoms, diagnoses, and context.',
			img: '/images/api-semantic-search.png',
			label: 'Image placeholder — MCP / integrations'
		},
		{
			title: 'One API. Structured medical data.',
			text: 'Integrate medical case retrieval directly into your applications with simple HTTP requests and machine-readable JSON responses.',
			img: '/images/api-automation.png',
			label: 'Image placeholder — automation pipeline'
		}
	];
</script>

<section class="mx-auto mt-[110px] w-full max-w-[1300px] px-4 xl:px-0">
	<div class="grid gap-3 md:grid-cols-3">
		{#each cards as card (card.title)}
			<div class="flex flex-col justify-between rounded-xl bg-card p-4">
				<div class="px-1">
					<h3 class="text-[15px] font-medium text-ink">{card.title}</h3>
					<p class="mt-1.5 text-[15px] leading-[1.45] text-soft">{card.text}</p>
				</div>
				<!-- <ImgSlot
					src={card.img}
					alt={card.title}
					label={card.label}
					hint={card.hint}
					class="mt-5 aspect-[1/1.02] w-full rounded-lg bg-frame"
				/> -->
			</div>
		{/each}
	</div>
</section>
