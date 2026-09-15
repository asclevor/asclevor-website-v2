<script>
	import Navbar from '$lib/components/Navbar.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import LegalNav from '$lib/components/legal/LegalNav.svelte';
	import Seo from '$lib/components/Seo.svelte';
</script>

<Seo
	title="Imprint · Asclevor"
	description="Legal information about Asclevor: provider identification, contact, and responsible persons."
	path="/imprint"
/>

<Navbar />

<!--
	PLACEHOLDERS: The bracketed values below (legal form, address, registration,
	VAT ID, representatives) MUST be replaced with Asclevor's real entity details
	before this page is published. An imprint is a legal requirement (e.g. § 5 DDG
	in Germany); publishing incorrect or incomplete details carries legal risk.
-->

<main class="mx-auto w-full max-w-[1300px] px-4 pt-[140px] pb-[160px] xl:px-0">
	<div class="grid gap-12 lg:grid-cols-[200px_1fr] lg:gap-16">
		<LegalNav active="/imprint" />

		<article class="max-w-[680px]">
			<h1 class="text-[40px] leading-[1.1] tracking-[-0.02em] text-ink sm:text-[48px]">Imprint</h1>
			<p class="mt-3 text-[17px] text-soft">Legal information about Asclevor</p>

			<div class="mt-12 space-y-6 text-[17px] leading-[1.65] text-ink">
				<h2 class="pt-4 text-[17px] font-bold">Provider</h2>
				<p class="whitespace-pre-line">Asclevor Technologies</p>

				<h2 class="pt-4 text-[17px] font-bold">Contact</h2>
				<p>
					Email:
					<a
						href="mailto:contact@asclevor.com"
						class="underline underline-offset-2 transition-opacity hover:opacity-70"
						>contact@asclevor.com</a
					><br />
					Web:
					<a
						href="https://www.asclevor.com"
						class="underline underline-offset-2 transition-opacity hover:opacity-70"
						>www.asclevor.com</a
					>
				</p>

				<!-- <h2 class="pt-4 text-[17px] font-bold">Register &amp; Tax</h2>
				<p>
					Commercial register: [Register court, e.g. Amtsgericht …], register number [HRB …]<br />
					VAT ID (Umsatzsteuer-Identifikationsnummer) pursuant to § 27a UStG, if applicable: [DE…]
				</p> -->

				<h2 class="pt-4 text-[17px] font-bold">Representatives</h2>
				<p>Managing directors: Leander E. Guo</p>

				<!-- <h2 class="pt-4 text-[17px] font-bold">Responsible for content</h2>
				<p>
					Responsible for the content of this website pursuant to § 18 (2) MStV: [Name, address as
					above]
				</p> -->

				<h2 class="pt-4 text-[17px] font-bold">Dispute resolution</h2>
				<p>
					We are not obliged to participate in dispute-resolution proceedings before a consumer
					arbitration board and are generally not willing to do so. The European Commission provides
					a platform for online dispute resolution (ODR):
					<a
						href="https://ec.europa.eu/consumers/odr/"
						target="_blank"
						rel="noopener noreferrer"
						class="underline underline-offset-2 transition-opacity hover:opacity-70"
						>https://ec.europa.eu/consumers/odr/</a
					>
				</p>

				<h2 class="pt-4 text-[17px] font-bold">Liability for links</h2>
				<p>
					This website contains links to external third-party websites (for example our
					documentation and social profiles). We have no influence over the content of those
					websites and cannot accept liability for them. The respective provider or operator is
					always responsible for the content of linked pages.
				</p>
			</div>
		</article>
	</div>
</main>

<Footer />
