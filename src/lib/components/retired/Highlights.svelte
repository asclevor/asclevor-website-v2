<script>
	import Avatar from './Avatar.svelte';

	const posts = [
		{
			meta: 'Mar 27, 2026 · Research',
			title: 'A technical report on Composer 2',
			byline: 'Sasha Rush · 3 min read',
			avatar: {
				src: '/images/avatar-sasha.png',
				initials: 'SR',
				bg: '#C9B8A3',
				class: 'h-6 w-6 text-[9px]'
			}
		},
		{
			meta: 'Aug 14, 2026 · Company',
			title: 'Cursor is now a part of SpaceX',
			byline: 'Cursor Team · 2 min read',
			avatar: { src: '/images/avatar-cursor.png', logo: true, bg: '#262520', class: 'h-6 w-6' }
		},
		{
			meta: 'Aug 12, 2026 · Research',
			title: 'Introducing Grok 4.6',
			byline: 'Cursor Team · 3 min read',
			avatar: { src: '/images/avatar-cursor.png', logo: true, bg: '#262520', class: 'h-6 w-6' }
		},
		{
			meta: 'Aug 18, 2026 · Research',
			title: 'Git at any scale',
			byline: 'Vicent Marti · 27 min read',
			avatar: {
				src: '/images/avatar-vicent.png',
				initials: 'VM',
				bg: '#A3A6AB',
				class: 'h-6 w-6 text-[9px]'
			}
		}
	];
</script>

<section class="mx-auto mt-[130px] w-full max-w-[1300px] px-4 xl:px-0">
	<h2 class="text-[21px] tracking-[-0.01em]">Recent highlights</h2>

	<div class="mt-6 grid gap-4 sm:grid-cols-2 lg:grid-cols-4">
		{#each posts as post (post.title)}
			<a
				href="#"
				class="flex flex-col rounded-lg border border-line bg-card p-5 transition-colors hover:border-ink/20"
			>
				<p class="text-[15px] text-soft">{post.meta}</p>
				<p class="mt-1 text-[16px] leading-snug text-ink">{post.title}</p>
				<div class="mt-auto flex items-center gap-2 pt-6">
					<Avatar src={post.avatar.src} bg={post.avatar.bg} class={post.avatar.class}>
						{#if post.avatar.logo}
							<svg width="11" height="11" viewBox="0 0 24 24" fill="none">
								<path d="M12 1.6 2.3 7l9.7 5.3L21.7 7 12 1.6Z" fill="#8B8A83" />
								<path d="M12 22.4V12.3L2.3 7v10l9.7 5.4Z" fill="#F2F1ED" />
								<path d="M12 22.4 21.7 17V7l-9.7 5.3v10.1Z" fill="#B8B7B0" />
							</svg>
						{:else}
							{post.avatar.initials}
						{/if}
					</Avatar>
					<p class="text-[15px] text-soft">{post.byline}</p>
				</div>
			</a>
		{/each}
	</div>

	<a href="#" class="group mt-8 inline-flex items-center gap-1.5 text-[17px] text-accent">
		View all blog posts
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
</section>
