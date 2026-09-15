<script>
	import ImgSlot from './ImgSlot.svelte';
</script>

<section class="mx-auto w-full max-w-[1300px] px-4 xl:px-0">
	<div class="pt-[100px]">
		<h1 class="max-w-[640px] text-[28px] leading-[1.2] tracking-[-0.01em] sm:text-[30px]">
			Asclevor is your knowledge base for medical infrastructure.
		</h1>

		<div class="mt-7 flex flex-wrap items-center gap-3">
			<a
				href="https://app.asclevor.com"
				target="_blank"
				class="flex h-[42px] items-center gap-2 rounded-full bg-ink px-6 text-[15px] font-medium text-paper transition-opacity hover:opacity-85"
			>
				Open Case Search
			</a>
			<a
				href="/contact"
				class="flex h-[42px] items-center gap-2 rounded-full bg-btn2 px-6 text-[15px] font-medium text-ink transition-colors hover:bg-line"
			>
				Request a demo
				<svg width="15" height="15" viewBox="0 0 16 16" fill="none">
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
	</div>

	<!-- IMAGE: static/images/hero-app.webp -->
	<ImgSlot
		src="/images/hero-app.webp"
		alt="Asclevor case search interface showing a clinical query and matching patient cases"
		label="Image placeholder — hero app screenshot"
		hint="static/images/hero-app.webp · 1600 × 887"
		priority={true}
		width={1600}
		height={887}
		class="mt-14 aspect-[1300/720] w-full rounded-xl bg-frame"
	/>

	<div class="mt-12">
		<p class="text-center text-[14px] text-ink">
			Trusted every day by teams that build world-class software
		</p>
	</div>
</section>
