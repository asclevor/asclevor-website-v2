<script>
	const columns = [
		{
			title: 'Product',
			links: [
				{ label: 'API', href: '/api' },
				{ label: 'Pricing', href: '/pricing' }
			]
		},
		{
			title: 'Resources',
			links: [
				{ label: 'Docs', href: 'https://docs.asclevor.com', external: true },
				{ label: 'Changelog', href: '/changelog' },
				{ label: 'Contact', href: '/contact' }
			]
		},
		{
			title: 'Company',
			links: [{ label: 'Leadership', href: '/leadership' }]
		},
		{
			title: 'Legal',
			links: [
				{ label: 'Terms of Service', href: '/terms' },
				{ label: 'Privacy Policy', href: '/privacy' },
				{ label: 'Imprint', href: '/imprint' }
			]
		},
		{
			title: 'Connect',
			links: [
				{ label: 'X', href: 'https://x.com/asclevor', external: true },
				{ label: 'LinkedIn', href: 'https://www.linkedin.com/company/asclevor', external: true },
				{ label: 'YouTube', href: 'https://www.youtube.com/@asclevor', external: true }
			]
		}
	];
</script>

<footer class="bg-card">
	<div class="mx-auto w-full max-w-[1300px] px-4 pt-16 pb-10 xl:px-0">
		<div class="grid grid-cols-2 gap-y-10 sm:grid-cols-3 lg:grid-cols-5">
			{#each columns as column (column.title)}
				<div>
					<p class="text-[15px] text-soft">{column.title}</p>
					<ul class="mt-5 space-y-3.5 text-[15px]">
						{#each column.links as link (link.label)}
							<li>
								<a
									href={link.href}
									class="transition-opacity hover:opacity-60"
									target={link.external ? '_blank' : undefined}
									rel={link.external ? 'noopener noreferrer' : undefined}
								>
									{link.label}
								</a>
							</li>
						{/each}
					</ul>
				</div>
			{/each}
		</div>

		<!-- Bottom bar -->
		<div class="mt-24 flex flex-col gap-4 lg:flex-row lg:items-center lg:justify-between">
			<div class="flex flex-wrap items-center gap-x-6 gap-y-2 text-[14px] text-soft">
				<p>© 2026 Asclevor</p>
			</div>
		</div>
	</div>
</footer>
