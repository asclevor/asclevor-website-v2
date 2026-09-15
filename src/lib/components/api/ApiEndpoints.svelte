<script>
	import CopyButton from '../CopyButton.svelte';

	const request = `curl -X POST https://api.asclevor.com/search \\
  -H "Content-Type: application/json" \\
  -d '{
    "query": "60-year-old female, ARDS from COVID-19, desaturation during physical therapy",
    "k": 5,
    "mode": "auto",
    "include_text": true,
    "text_max_chars": 600
  }'`;

	const faqs = [
		{
			q: 'Do I need an API key?',
			a: 'No. The Free plan works without an API key at up to 20 requests per minute. API keys are available on paid plans for higher limits.'
		},
		{
			q: 'What does a response look like?',
			a: 'Machine-readable JSON: the clinically most similar patient cases for your query, with associated medical literature when you request text.'
		},
		{
			q: 'Can AI agents use Asclevor?',
			a: 'Yes. Asclevor supports the Model Context Protocol (MCP), so agents can query clinical cases directly from your AI stack.'
		},
		{
			q: 'How much does it cost?',
			a: 'The Free plan includes 10,000 requests per month. Developer and Pro plans raise rate limits and monthly volume; Enterprise adds dedicated infrastructure and SLAs.'
		}
	];

	let open = $state(-1);
	function toggle(i) {
		open = open === i ? -1 : i;
	}
</script>

<!-- Request example — concrete specifics for developers and answer engines -->
<section class="mx-auto mt-[110px] w-full max-w-[1300px] px-4 xl:px-0">
	<h2 class="text-[24px] tracking-[-0.015em] text-ink">One call. Structured clinical data.</h2>
	<p class="mt-3 max-w-[720px] text-[15px] leading-[1.55] text-soft">
		Send a natural-language query describing the patient or scenario you're looking for. Asclevor
		returns the clinically most similar cases from its knowledge base as JSON — ready to parse in
		any language.
	</p>

	<div class="mt-8 rounded-xl bg-[#262520] p-5 sm:p-6">
		<div class="flex items-center justify-between gap-4">
			<p class="font-mono text-[13px] text-[#f7f7f4]/60">POST https://api.asclevor.com/search</p>
			<CopyButton text={request} class="bg-[#f7f7f4] text-[#262520]" />
		</div>
		<pre class="mt-4 overflow-x-auto font-mono text-[13px] leading-[1.6] text-[#f7f7f4]"><code
				>{request}</code
			></pre>
	</div>

	<!-- Good to know -->
	<div class="mt-12">
		<h3 class="text-[20px] tracking-[-0.01em] text-ink">Good to know</h3>
		<div class="mt-6 border-t border-line">
			{#each faqs as faq, i (faq.q)}
				<div class="border-b border-line">
					<button
						onclick={() => toggle(i)}
						aria-expanded={open === i}
						class="flex w-full items-center justify-between gap-4 py-4 text-left"
					>
						<span class="text-[15px] text-ink">{faq.q}</span>
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
						<p class="pr-8 pb-4 text-[15px] leading-[1.55] text-soft">{faq.a}</p>
					{/if}
				</div>
			{/each}
		</div>
		<p class="mt-6 text-[15px] text-soft">
			Full endpoint reference at
			<a
				href="https://docs.asclevor.com"
				target="_blank"
				rel="noopener noreferrer"
				class="text-accent transition-opacity hover:opacity-80">docs.asclevor.com</a
			>.
		</p>
	</div>
</section>
