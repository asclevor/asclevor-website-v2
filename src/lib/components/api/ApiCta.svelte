<script>
	import CopyButton from '../CopyButton.svelte';

	const installCmd = `curl -X POST https://api.asclevor.com/search -H "Content-Type: application/json" -d '{"query":"60-year-old female, ARDS from COVID-19, desaturation during physical therapy","k":5,"mode":"auto","include_text":true,"text_max_chars":600}'`;
</script>

<section class="mx-auto w-full max-w-[1300px] px-4 pt-[150px] pb-[150px] text-center xl:px-0">
	<!-- Mark -->
	<h2 class="mt-8 text-[52px] leading-none tracking-[-0.02em] sm:text-[68px]">Try Asclevor API.</h2>

	<div class="mt-8 flex justify-center">
		<div
			class="flex max-w-full items-center gap-3 rounded-lg border border-line bg-paper py-2 pr-2 pl-4"
		>
			<code class="truncate font-mono text-[14px] text-ink">{installCmd}</code>
			<CopyButton text={installCmd} />
		</div>
	</div>
</section>
