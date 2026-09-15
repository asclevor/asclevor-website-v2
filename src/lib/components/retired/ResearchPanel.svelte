<script>
	import ImgSlot from '../ImgSlot.svelte';
</script>

<section class="mx-auto mt-[130px] w-full max-w-[1300px] px-4 xl:px-0">
	<div class="grid items-center gap-8 rounded-xl bg-card p-4 lg:grid-cols-[1fr_1.62fr] lg:gap-4">
		<div class="px-3 lg:px-6">
			<p class="max-w-[420px] text-[24px] leading-[1.35] tracking-[-0.005em] text-ink">
				Cursor is an applied research team focused on building the future of software development.
			</p>
			<a href="#" class="group mt-6 inline-flex items-center gap-1.5 text-[17px] text-accent">
				Join us
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
		</div>

		<!-- IMAGE: static/images/research-team.png -->
		<ImgSlot
			src="/images/research-team.png"
			alt="Cursor research team"
			label="Image placeholder — research team photo"
			hint="static/images/research-team.png · ~1680 × 1050"
			class="aspect-[8/5] w-full rounded-lg bg-frame"
		/>
	</div>
</section>
