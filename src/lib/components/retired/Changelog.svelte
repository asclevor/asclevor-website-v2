<script>
	const items = [
		{ date: 'Sep 10, 2026', title: 'Cursor Projects' },
		{ date: 'Sep 2, 2026', title: 'Self-hosted machines' },
		{ date: 'Aug 27, 2026', title: 'Start from scratch, without a repo' },
		{ date: 'Aug 19, 2026', title: 'Cloud Agents and Cursor Harness Improvements' }
	];
</script>

<section class="mx-auto mt-[130px] w-full max-w-[1300px] px-4 xl:px-0">
	<h2 class="text-[21px] tracking-[-0.01em]">Changelog</h2>

	<div class="mt-6 grid gap-4 sm:grid-cols-2 lg:grid-cols-4">
		{#each items as item (item.title)}
			<a
				href="#"
				class="rounded-lg border border-line bg-card p-5 transition-colors hover:border-ink/20"
			>
				<p class="text-[15px] text-soft">{item.date}</p>
				<p class="mt-1 text-[16px] text-ink">{item.title}</p>
			</a>
		{/each}
	</div>

	<a href="#" class="group mt-8 inline-flex items-center gap-1.5 text-[17px] text-accent">
		See what's new in Cursor
		<svg
			class="transition-transform group-hover:translate-x-0.5"
			width="15"
			height="15"
			viewBox="0 0 16 16"
			fill="none"
		>
			<path
				d="M2.5 8h11m0 0L9 3.5M13.5 8 9 12.5"
				stroke="currentColor"
				stroke-width="1.5"
				stroke-linecap="round"
				stroke-linejoin="round"
			/>
		</svg>
	</a>
</section>
