<header class="fixed z-1000 w-full bg-paper">
	<nav
		class=" mx-auto flex h-[68px] w-full max-w-[1300px] items-center justify-between px-4 xl:px-0"
	>
		<!-- Logo -->
		<a href="/" class="flex items-center gap-1">
			<img src="/logo.svg" width="24" height="24" alt="" />
			<span class="font-display text-[17px] font-medium tracking-wide">ASCLEVOR</span>
		</a>

		<!-- Center links
		<div class="hidden items-center gap-9 md:flex">
			{#each ['Models', 'Product', 'Enterprise', 'Pricing', 'Resources'] as link (link)}
				<a href={'#' + link} class="text-[15px] text-ink transition-opacity hover:opacity-60"
					>{link}</a
				>
			{/each}
		</div> -->

		<!-- Right actions -->
		<div class="flex items-center gap-3">
			<a
				href="/contact"
				class="hidden h-[34px] items-center rounded-full border border-ink/15 px-4 text-[15px] text-ink transition-colors hover:border-ink/30 sm:flex"
				>Contact sales</a
			>
			<a
				href="https://app.asclevor.com"
				target="_blank"
				class="flex h-[34px] items-center rounded-full bg-ink px-4 text-[15px] font-medium text-paper transition-opacity hover:opacity-85"
				>Open Case Search</a
			>
		</div>
	</nav>
</header>
