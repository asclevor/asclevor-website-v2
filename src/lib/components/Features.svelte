<script>
	import ImgSlot from './ImgSlot.svelte';

	const installCmd = `curl -X POST https://api.asclevor.com/search -H "Content-Type: application/json" -d '{"query":"60-year-old female, ARDS from COVID-19, desaturation during physical therapy","k":5,"mode":"auto","include_text":true,"text_max_chars":600}'`;

	let copied = $state(false);

	async function copyInstall() {
		try {
			await navigator.clipboard.writeText(installCmd);
			copied = true;
			setTimeout(() => (copied = false), 1600);
		} catch {
			// clipboard unavailable — no-op
		}
	}
</script>

<!-- FEATURE 1 — Agents turn ideas into code        (text left / img right) -->
<section class="mx-auto mt-[104px] w-full max-w-[1300px] px-4 xl:px-0">
	<div class="grid items-center gap-8 rounded-xl bg-card p-4 lg:grid-cols-[1fr_1.62fr] lg:gap-4">
		<div class="px-3 lg:px-4">
			<h2 class="text-[21px] leading-[1.4] font-normal tracking-[-0.005em]">
				<span class="text-ink">Give frontier models access to clinical cases</span>
				<br />
				<span class="text-soft">
					Connect Asclevor to AI agents through the Model Context Protocol (MCP).</span
				>
			</h2>
		</div>

		<!-- IMAGE: static/images/mission-control.webp -->
		<ImgSlot
			src="/images/mission-control.webp"
			alt="Asclevor mission control dashboard for monitoring clinical case retrieval"
			label="Image placeholder — Mission Control UI"
			hint="static/images/mission-control.webp · 1400 × 1022"
			width={1400}
			height={1022}
			class="aspect-[5/4] w-full rounded-lg bg-frame"
		/>
	</div>
</section>

<!-- FEATURE 2 — Works autonomously                 (img left / text right) -->
<section class="mx-auto mt-[92px] w-full max-w-[1300px] px-4 xl:px-0">
	<div class="grid items-center gap-8 rounded-xl bg-card p-4 lg:grid-cols-[1.62fr_1fr] lg:gap-4">
		<!-- IMAGE: static/images/cloud-agents.webp -->
		<!-- <ImgSlot
			src="/images/cloud-agents.webp"
			alt="Asclevor cloud agents dashboard"
			label="Image placeholder — cloud agent dashboard"
			hint="static/images/cloud-agents.webp · 1400 × 1157"
			class="order-2 aspect-[5/4] w-full rounded-lg bg-frame lg:order-1"
		/> -->

		<ImgSlot
			src="/images/case-search.mp4"
			poster="/images/case-search-poster.webp"
			label="Video — clinical case search demo"
			hint="static/images/case-search.mp4"
			class="aspect-[13/10] w-full rounded-lg bg-frame"
		/>
		<div class="order-1 px-3 lg:order-2 lg:px-6">
			<h2 class="text-[21px] leading-[1.4] font-normal tracking-[-0.005em]">
				<span class="text-ink">Search clinical cases in seconds.</span>
				<br />
				<span class="text-soft">
					Explore clinical cases with natural-language search. Asclevor retrieves semantically
					similar cases</span
				>
			</h2>
			<a
				href="https://app.asclevor.com/"
				target="_blank"
				class="group mt-7 inline-flex items-center gap-1.5 text-[17px] text-accent"
			>
				Try Asclevor Case Search
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
	</div>
</section>

<!-- FEATURE 3 — In every tool, at every step       (text left / img right) -->
<section class="mx-auto mt-[92px] w-full max-w-[1300px] px-4 xl:px-0">
	<div class="grid items-center gap-8 rounded-xl bg-card p-4 lg:grid-cols-[1fr_1.62fr] lg:gap-4">
		<div class="px-3 lg:px-4">
			<h2 class="text-[21px] leading-[1.4] font-normal tracking-[-0.005em]">
				<span class="text-ink">Build medical applications with the Asclevor API.</span><br />
				<span class="text-soft">
					Integrate clinical case retrieval directly into your software with a simple HTTP API.</span
				>
			</h2>

			<!-- Install command -->
			<div
				class="mt-8 flex max-w-[420px] items-center gap-3 rounded-lg border border-line bg-paper py-2 pr-2 pl-4"
			>
				<code class="truncate font-mono text-[14px] text-ink">{installCmd}</code>
				<button
					onclick={copyInstall}
					class="ml-auto grid h-8 w-8 shrink-0 place-items-center rounded-md bg-ink text-paper transition-opacity hover:opacity-85"
					title={copied ? 'Copied!' : 'Copy'}
					aria-label="Copy install command"
				>
					{#if copied}
						<svg width="14" height="14" viewBox="0 0 16 16" fill="none">
							<path
								d="m3 8.5 3.2 3L13 4.5"
								stroke="currentColor"
								stroke-width="1.5"
								stroke-linecap="round"
								stroke-linejoin="round"
							/>
						</svg>
					{:else}
						<svg width="14" height="14" viewBox="0 0 16 16" fill="none">
							<rect
								x="5.5"
								y="5.5"
								width="8"
								height="8"
								rx="1.5"
								stroke="currentColor"
								stroke-width="1.4"
							/>
							<path
								d="M10.5 3.5A2 2 0 0 0 8.6 2H4a2 2 0 0 0-2 2v4.6a2 2 0 0 0 1.5 1.9"
								stroke="currentColor"
								stroke-width="1.4"
								stroke-linecap="round"
							/>
						</svg>
					{/if}
				</button>
			</div>
			<a href="/api" class="group mt-7 inline-flex items-center gap-1.5 text-[17px] text-accent">
				Learn More about Asclevor's API
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

		<!-- VIDEO: static/images/everywhere.mp4 (autoplays on loop, no controls) -->
		<ImgSlot
			src="/images/everywhere.mp4"
			poster="/images/everywhere-poster.webp"
			label="Video — Asclevor in your workflow"
			hint="static/images/everywhere.mp4"
			class="aspect-[13/10] w-full rounded-lg bg-frame"
		/>
	</div>
</section>
