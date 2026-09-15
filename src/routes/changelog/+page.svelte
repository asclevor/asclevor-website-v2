<script>
	import Navbar from '$lib/components/Navbar.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import Seo from '$lib/components/Seo.svelte';

	/* ────────────────────────────────────────────────────────────────────
	   HOW TO ADD A NEW CHANGELOG ENTRY
	   Append an object to `entries` below (newest first). Available block
	   types inside `blocks`:
	     { type: 'p',   text: 'Paragraph text. **bold** and [links](/url) work.' }
	     { type: 'h2',  text: 'Section heading inside the entry' }
	     { type: 'img', src: '/images/whatever.webp', alt: 'describe the image' }
	   Keep images in static/images/. The divider between entries is automatic.
	   ──────────────────────────────────────────────────────────────────── */

	// NOTE: dates below are examples — align them with your real release dates.
	const entries = [
		{
			date: 'Sep 7, 2026',
			title: 'Asclevor MCP Server',
			blocks: [
				{
					type: 'p',
					text: 'Today we’re launching the **Asclevor MCP server**, giving AI agents a direct interface to Asclevor’s clinical knowledge infrastructure through the [Model Context Protocol](https://modelcontextprotocol.io/).'
				},
				{
					type: 'h2',
					text: 'Clinical knowledge, one tool call away'
				},
				{
					type: 'p',
					text: 'The MCP server lets compatible AI applications search clinical cases, retrieve patient cases, and find similar patients directly through Asclevor — without having to build a custom integration around the API.'
				},
				{
					type: 'p',
					text: 'The endpoint is available at **[mcp.asclevor.com/mcp](https://mcp.asclevor.com/mcp)** and uses streamable HTTP, making it straightforward to connect from MCP-compatible clients and agent frameworks.'
				},
				{
					type: 'h2',
					text: 'Built for developers'
				},
				{
					type: 'p',
					text: 'Asclevor MCP exposes the same clinical retrieval capabilities available through our API in a protocol designed specifically for tool-using AI systems. Developers can give their agents access to real-world clinical cases without implementing their own retrieval layer.'
				},
				{
					type: 'p',
					text: 'MCP access is available on all Asclevor plans. [Read the documentation](https://docs.asclevor.com) to get started.'
				}
			]
		}
	];

	// Minimal inline formatting: escape HTML, then allow **bold** and [text](url).
	function format(text) {
		const escaped = text
			.replaceAll('&', '&amp;')
			.replaceAll('<', '&lt;')
			.replaceAll('>', '&gt;')
			.replaceAll('"', '&quot;');
		return escaped
			.replace(/\*\*(.+?)\*\*/g, '<strong>$1</strong>')
			.replace(
				/\[(.+?)\]\((.+?)\)/g,
				'<a href="$2" class="text-accent transition-opacity hover:opacity-80">$1</a>'
			);
	}
</script>

<Seo
	title="Changelog · Asclevor — What's New"
	description="Latest Asclevor updates and release notes: new plans, API improvements, MCP support, and changes to the clinical knowledge base."
	path="/changelog"
/>

<Navbar />

<main class="mx-auto w-full max-w-[1300px] px-4 pt-[100px] pb-[160px] xl:px-0">
	{#each entries as entry, i (entry.date + entry.title)}
		<article
			class="grid gap-4 py-16 lg:grid-cols-[160px_minmax(0,1fr)] lg:gap-10 {i > 0
				? 'border-t border-line'
				: ''}"
		>
			<!-- Date rail -->
			<p class="text-[14px] text-soft lg:pt-[6px]">{entry.date}</p>

			<!-- Entry content (centered column, like the reference design) -->
			<div class="mx-auto w-full max-w-[680px]">
				{#if i === 0}
					<p class="text-[14px] text-soft">Changelog</p>
				{/if}
				{#if i === 0}
					<h1 class="text-[30px] leading-[1.15] tracking-[-0.015em] text-ink sm:text-[36px]">
						{entry.title}
					</h1>
				{:else}
					<h2 class="text-[30px] leading-[1.15] tracking-[-0.015em] text-ink sm:text-[36px]">
						{entry.title}
					</h2>
				{/if}

				<div class="mt-8 space-y-6 text-[17px] leading-[1.65] text-ink">
					{#each entry.blocks as block, j (j)}
						{#if block.type === 'p'}
							<p>{@html format(block.text)}</p>
						{:else if block.type === 'h2'}
							<h3 class="pt-4 text-[20px] font-bold tracking-[-0.01em]">{block.text}</h3>
						{:else if block.type === 'img'}
							<img
								src={block.src}
								alt={block.alt}
								loading="lazy"
								decoding="async"
								class="w-full rounded-xl bg-frame"
							/>
						{/if}
					{/each}
				</div>
			</div>
		</article>
	{/each}
</main>

<Footer />
