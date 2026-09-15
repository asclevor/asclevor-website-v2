<script>
	/**
	 * Sidebar navigation for legal pages, mirroring the Cursor-style
	 * legal layout: sticky list of links, active page in ink, rest soft.
	 */
	let { active = '' } = $props();

	const pages = [
		{ slug: '/terms', label: 'Terms of Service' },
		{ slug: '/privacy', label: 'Privacy Policy' },
		{ slug: '/imprint', label: 'Imprint' }
	];
</script>

<nav aria-label="Legal pages" class="lg:sticky lg:top-[140px] lg:self-start">
	<ul class="space-y-3 text-[17px]">
		{#each pages as page (page.slug)}
			<li>
				<a
					href={page.slug}
					aria-current={active === page.slug ? 'page' : undefined}
					class="transition-opacity hover:opacity-70 {active === page.slug
						? 'text-ink'
						: 'text-soft'}"
				>
					{page.label}
				</a>
			</li>
		{/each}
	</ul>
</nav>
