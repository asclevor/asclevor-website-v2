<script>
	/** Dark copy button; copies `text` to the clipboard and flashes a check. */
	let { text, label = 'Copy', class: klass = '' } = $props();

	let copied = $state(false);

	async function copy() {
		try {
			await navigator.clipboard.writeText(text);
			copied = true;
			setTimeout(() => (copied = false), 1600);
		} catch {
			// clipboard unavailable — no-op
		}
	}
</script>

<button
	onclick={copy}
	class="ml-auto grid h-8 w-8 shrink-0 place-items-center rounded-md bg-ink text-paper transition-opacity hover:opacity-85 {klass}"
	title={copied ? 'Copied!' : label}
	aria-label={label}
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
