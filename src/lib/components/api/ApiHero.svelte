<script>
	import ImgSlot from '../ImgSlot.svelte';
	import CopyButton from '../CopyButton.svelte';

	const installCmd = `curl -X POST https://api.asclevor.com/search -H "Content-Type: application/json" -d '{"query":"60-year-old female, ARDS from COVID-19, desaturation during physical therapy","k":5,"mode":"auto","include_text":true,"text_max_chars":600}'`;
</script>

<section class="mx-auto w-full max-w-[1300px] px-4 pt-[100px] xl:px-0">
	<p class="text-[14px] text-soft">API</p>
	<h1 class="mt-2 text-[30px] leading-[1.15] tracking-[-0.015em] sm:text-[40px]">
		<span class="text-ink">Build on clinical knowledge</span>
		<br />
		<span class="text-soft">Right from your stack.</span>
	</h1>

	<!-- Same commands, any environment -->
	<div
		class="mt-10 grid items-center gap-8 rounded-xl bg-card p-4 lg:grid-cols-[1fr_1.9fr] lg:gap-4"
	>
		<div class="px-3 lg:px-4">
			<p class="text-[20px] leading-[1.4] tracking-[-0.005em]">
				<span class="text-ink">Same commands, any environment.</span>
				<br />
				<span class="text-soft">Plug into your setup anywhere.</span>
			</p>

			<div
				class="mt-8 flex max-w-[420px] items-center gap-3 rounded-lg border border-line bg-paper py-2 pr-2 pl-4"
			>
				<code class="truncate font-mono text-[13px] text-ink">{installCmd}</code>
				<CopyButton text={installCmd} />
			</div>
		</div>

		<!-- IMAGE: static/images/api-hero.webp -->
		<ImgSlot
			src="/images/api-hero.webp"
			alt="Asclevor API returning structured JSON of clinically similar patient cases"
			label="Image placeholder — API product visual"
			hint="static/images/api-hero.webp · 1600 × 840"
			priority={true}
			width={1600}
			height={840}
			class="aspect-[16/9] w-full rounded-lg bg-frame"
		/>
	</div>
</section>
