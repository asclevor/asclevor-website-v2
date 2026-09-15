<script>
	import Navbar from '$lib/components/Navbar.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import LegalNav from '$lib/components/legal/LegalNav.svelte';
	import Seo from '$lib/components/Seo.svelte';
</script>

<Seo
	title="Privacy Policy · Asclevor"
	description="How Asclevor collects, uses, discloses, and protects personal data when you use our website, API, and services — and the rights you have over your data."
	path="/privacy"
/>

<Navbar />

<main class="mx-auto w-full max-w-[1300px] px-4 pt-[140px] pb-[160px] xl:px-0">
	<div class="grid gap-12 lg:grid-cols-[200px_1fr] lg:gap-16">
		<LegalNav active="/privacy" />

		<article class="max-w-[680px]">
			<h1 class="text-[40px] leading-[1.1] tracking-[-0.02em] text-ink sm:text-[48px]">
				Privacy Policy
			</h1>
			<p class="mt-3 text-[17px] text-soft">Last updated September 15, 2026</p>

			<div class="mt-12 space-y-6 text-[17px] leading-[1.65] text-ink">
				<p>
					This Privacy Policy explains how Asclevor ("<strong>we</strong>," "<strong>us</strong>")
					collects, uses, discloses, and protects personal data when you visit
					<a
						href="https://www.asclevor.com"
						class="underline underline-offset-2 transition-opacity hover:opacity-70"
						>www.asclevor.com</a
					>
					or use the Asclevor Service (the clinical knowledge base, API, and related tools). It also describes
					the rights you have over your data.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">1. Data We Collect</h2>
				<p>
					<strong>1.1. Information you provide.</strong> When you contact us (for example through the
					contact form or by email), we receive the information you send: your name, work email address,
					and the content of your message. When you create an account or purchase a plan, we process account
					details (such as email address) and payment is handled by our payment provider; we do not store
					full payment card details on our servers.
				</p>
				<p>
					<strong>1.2. Usage and technical data.</strong> When you use the Service, we process request
					metadata necessary to operate the API: request timestamps, endpoints called, request volumes,
					rate-limit state, and API key identifiers, as well as server log data (including IP address)
					collected for security and abuse prevention.
				</p>
				<p>
					<strong>1.3. Query content.</strong> The content of API queries (Inputs) and the outputs returned
					are processed to provide the Service. We do not use query content to train machine-learning
					models unless you have explicitly opted in.
				</p>
				<p>
					<strong>1.4. No marketing cookies.</strong> The website sets no advertising or tracking cookies.
					Please note that loading web fonts from Google Fonts involves a technical request to Google's
					servers, which receives your IP address (see Section 5).
				</p>

				<h2 class="pt-4 text-[17px] font-bold">2. How We Use Data</h2>
				<p>
					We use personal data to: provide, operate, and secure the Service; enforce plan limits and
					prevent abuse; respond to inquiries and provide support; process payments and administer
					subscriptions; comply with legal obligations; and improve the Service on an aggregated
					basis. We do not sell personal data, and we do not use personal data for third-party
					advertising.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">3. Legal Bases</h2>
				<p>
					Where the GDPR applies, we process personal data on the following bases: performance of a
					contract (Art. 6(1)(b)) — providing the Service and handling your account; legitimate
					interests (Art. 6(1)(f)) — securing and improving the Service, and defending legal claims;
					consent (Art. 6(1)(a)) — where you have given it, for example for optional communications;
					and legal obligations (Art. 6(1)(c)) — for example commercial record-keeping.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">4. Retention</h2>
				<p>
					We keep personal data only as long as necessary for the purposes described above: contact
					inquiries for as long as needed to handle them and any follow-up; account and billing
					records for the duration of the subscription and as long as required by commercial and tax
					law; server logs for a short period consistent with security needs, typically 30 days or
					less unless needed for a specific investigation.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">5. Service Providers and Transfers</h2>
				<p>
					We share personal data with a limited set of processors that help us operate the Service,
					such as hosting and infrastructure providers, payment processors, and email delivery. We
					select these providers carefully and bind them by contract to process data only on our
					instructions. Where our website loads web fonts from Google Fonts, a technical connection
					to Google servers is established and your IP address is transmitted; we are evaluating
					self-hosting these fonts. Where data is transferred outside the EEA, we rely on
					appropriate safeguards such as the European Commission's standard contractual clauses.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">6. Security</h2>
				<p>
					We protect personal data with technical and organizational measures appropriate to the
					risk, including encryption in transit (HTTPS/TLS) for the Service and API, access
					controls, and least-privilege practices. No system is perfectly secure; if a data breach
					affects your rights and freedoms, we will notify you and the competent authority as
					required by law.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">7. Your Rights</h2>
				<p>
					Subject to applicable law, you have the right to: access your personal data and receive a
					copy (Art. 15 GDPR); rectify inaccurate data (Art. 16); erase data (Art. 17); restrict
					processing (Art. 18); receive your data in a portable format (Art. 20); object to
					processing based on legitimate interests (Art. 21); and withdraw consent at any time where
					processing is based on consent. You also have the right to lodge a complaint with a data
					protection supervisory authority.
				</p>
				<p>
					To exercise any of these rights, contact
					<a
						href="mailto:contact@asclevor.com"
						class="underline underline-offset-2 transition-opacity hover:opacity-70"
						>contact@asclevor.com</a
					>. We will respond within the timeframes required by law.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">8. Children</h2>
				<p>
					The Service is intended for professionals and organizations. We do not knowingly collect
					personal data from children under the age applicable in your jurisdiction.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">9. Changes to This Policy</h2>
				<p>
					We may update this Privacy Policy as the Service or applicable law evolves. Material
					changes will be announced on this page (and, where appropriate, by notice through the
					Service) before they take effect.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">10. Contact</h2>
				<p>
					Questions about this Privacy Policy or our data practices can be sent to
					<a
						href="mailto:contact@asclevor.com"
						class="underline underline-offset-2 transition-opacity hover:opacity-70"
						>contact@asclevor.com</a
					>. Our legal entity details are listed in the
					<a
						href="/imprint"
						class="underline underline-offset-2 transition-opacity hover:opacity-70">Imprint</a
					>.
				</p>
			</div>
		</article>
	</div>
</main>

<Footer />
