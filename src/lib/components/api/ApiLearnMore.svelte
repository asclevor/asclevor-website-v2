<script>
	const items = [
		{
			title: 'Get started with the Asclevor API',
			text: 'Authentication, endpoints, and quickstart guides.'
		},
		{
			title: 'Search endpoints',
			text: 'Query cases by semantic similarity, filters, and mode.'
		},
		{
			title: 'MCP integration',
			text: 'Connect AI agents to Asclevor through the Model Context Protocol.'
		},
		{
			title: 'Webhooks & automation',
			text: 'Trigger pipelines when new cases and guidelines land.'
		}
	];
</script>

<section class="mx-auto mt-[110px] w-full max-w-[1300px] px-4 xl:px-0">
	<h2 class="text-[24px] tracking-[-0.015em] text-ink">Learn more</h2>

	<div class="mt-6 grid gap-3 md:grid-cols-2">
		{#each items as item (item.title)}
			<a
				href="https://docs.asclevor.com"
				target="_blank"
				rel="noreferrer"
				class="rounded-lg bg-card p-5 transition-colors hover:bg-line"
			>
				<p class="text-[16px] text-ink">{item.title}</p>
				<p class="mt-1 text-[15px] leading-[1.45] text-soft">{item.text}</p>
				<p class="mt-4 inline-flex items-center gap-1.5 text-[15px] text-accent">
					Read documentation
					<svg width="14" height="14" viewBox="0 0 16 16" fill="none">
						<path
							d="M2.5 8h11m0 0L9 3.5M13.5 8 9 12.5"
							stroke="currentColor"
							stroke-width="1.5"
							stroke-linecap="round"
							stroke-linejoin="round"
						/>
					</svg>
				</p>
			</a>
		{/each}
	</div>
</section>
