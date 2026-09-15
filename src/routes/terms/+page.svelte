<script>
	import Navbar from '$lib/components/Navbar.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import LegalNav from '$lib/components/legal/LegalNav.svelte';
	import Seo from '$lib/components/Seo.svelte';
</script>

<Seo
	title="Terms of Service · Asclevor"
	description="The terms governing your access to and use of the Asclevor clinical knowledge platform, its API, and related services."
	path="/terms"
/>

<Navbar />

<main class="mx-auto w-full max-w-[1300px] px-4 pt-[140px] pb-[160px] xl:px-0">
	<div class="grid gap-12 lg:grid-cols-[200px_1fr] lg:gap-16">
		<LegalNav active="/terms" />

		<article class="max-w-[680px]">
			<h1 class="text-[40px] leading-[1.1] tracking-[-0.02em] text-ink sm:text-[48px]">
				Terms of Service
			</h1>
			<p class="mt-3 text-[17px] text-soft">Last updated September 15, 2026</p>

			<div class="mt-12 space-y-6 text-[17px] leading-[1.65] text-ink">
				<p>
					Welcome, and thank you for your interest in Asclevor ("<strong>Asclevor</strong>," "<strong
						>we</strong
					>," "<strong>us</strong>," or "<strong>our</strong>"). These Terms of Service ("<strong
						>Terms</strong
					>") govern your access to and use of the Asclevor platform, including the clinical
					knowledge base, the Asclevor API, the website
					<a
						href="https://www.asclevor.com"
						class="underline underline-offset-2 transition-opacity hover:opacity-70"
						>www.asclevor.com</a
					>, and related documentation and tools made available by us (collectively, the "<strong
						>Service</strong
					>").
				</p>
				<p>
					By accessing or using the Service, you agree to be bound by these Terms and our
					<a
						href="/privacy"
						class="underline underline-offset-2 transition-opacity hover:opacity-70"
						>Privacy Policy</a
					>. If you use the Service on behalf of a company or organization, you represent that you
					have the legal authority to bind that entity to these Terms. If you have entered into a
					separate written agreement with us (for example, an Enterprise agreement), that agreement
					controls in the event of a conflict with these Terms.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">1. Description of the Service</h2>
				<p>
					<strong>1.1. Provision of Access.</strong> Asclevor provides a knowledge base for medical infrastructure:
					semantic search over a corpus of real-world clinical cases and their associated medical literature,
					accessible via API, web application, and Model Context Protocol (MCP). Subject to your compliance
					with these Terms, we grant you a limited, non-exclusive, non-transferable, revocable right to
					access and use the Service for your internal business or research purposes.
				</p>
				<p>
					<strong>1.2. Plans and Limits.</strong> The Service is offered under the plans described
					on our
					<a
						href="/pricing"
						class="underline underline-offset-2 transition-opacity hover:opacity-70">pricing page</a
					>, including a Free plan, paid Developer and Pro plans, and custom Enterprise
					arrangements. Plan limits (such as monthly requests and rate limits) apply as described at
					the time of purchase or, for the Free plan, as published on our website. We may update
					plan features and limits from time to time.
				</p>
				<p>
					<strong>1.3. API Keys.</strong> Paid plans include one or more API keys. Keys are personal to
					your account; you must keep them confidential, use them only in accordance with the documentation,
					and promptly notify us of any unauthorized use. We may suspend or throttle usage that exceeds
					plan limits or threatens the stability of the Service.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">2. Medical Disclaimer</h2>
				<p>
					<strong>2.1. Not Medical Advice.</strong> The Service provides access to medical case data and
					retrieval infrastructure. It is not a medical device, not a diagnostic system, and does not
					provide medical advice. Outputs are informational only and must not be used as a substitute
					for professional medical judgment, diagnosis, or treatment.
				</p>
				<p>
					<strong>2.2. Your Responsibility.</strong> You are solely responsible for how you use the Service
					and any outputs derived from it, including compliance with the professional, legal, and regulatory
					requirements applicable to your use case and jurisdiction. Do not rely on the Service as the
					sole basis for any clinical decision.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">3. Acceptable Use</h2>
				<p>
					<strong>3.1. Restrictions.</strong> You agree not to: (a) use the Service in violation of applicable
					law or the rights of any person; (b) present Service outputs as medical advice; (c) circumvent
					or attempt to circumvent plan limits, rate limits, or access controls; (d) scrape, resell, or
					redistribute substantial portions of the underlying case corpus except as expressly permitted
					by your plan; (e) interfere with or disrupt the Service or other users; or (f) use the Service
					to develop a competing clinical knowledge base or retrieval service.
				</p>
				<p>
					<strong>3.2. Suspension.</strong> We may suspend or terminate access to the Service if you violate
					these Terms, if required by law, or to protect the Service, our users, or third parties from
					harm.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">4. Your Content</h2>
				<p>
					<strong>4.1. Inputs and Outputs.</strong> You may submit queries and other inputs to the
					Service ("<strong>Inputs</strong>") and receive case matches, text, and other outputs ("<strong
						>Outputs</strong
					>"). As between you and us, you own your Inputs and we claim no ownership over your
					Outputs. You are responsible for ensuring that you have all rights and permissions
					necessary to submit your Inputs.
				</p>
				<p>
					<strong>4.2. Use of Content.</strong> We may use Inputs and usage data to provide, maintain,
					and secure the Service, to comply with law, and to enforce our terms. We will not use your Inputs
					to train machine-learning models unless you have explicitly opted in.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">5. Fees and Payment</h2>
				<p>
					<strong>5.1. Fees.</strong> Paid plans are billed in advance on a monthly or yearly basis as
					selected at checkout or as set out in an order form. Fees are non-refundable except as required
					by law or as expressly stated otherwise. We do not charge automatic overage fees; requests pause
					when a plan's monthly quota is exhausted.
				</p>
				<p>
					<strong>5.2. Changes and Renewal.</strong> Subscriptions renew automatically until cancelled.
					You can change or cancel your plan at any time; changes take effect as described on the pricing
					page or in your order form. We may change prices for upcoming billing periods with reasonable
					prior notice.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">6. Term and Termination</h2>
				<p>
					<strong>6.1. Termination.</strong> These Terms apply for as long as you use the Service. You
					may stop using the Service and cancel subscriptions at any time. We may terminate or suspend
					your access with notice if you materially breach these Terms and fail to cure the breach where
					curable, or immediately in cases of unlawful use or security threats.
				</p>
				<p>
					<strong>6.2. Effect of Termination.</strong> Upon termination, your right to use the Service
					ends and your API keys stop working. Sections that by their nature should survive termination
					(including ownership, disclaimers, limitation of liability, and governing law) will survive.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">7. Disclaimers</h2>
				<p>
					<strong>7.1. As Is.</strong> Except as expressly stated, the Service is provided "as is" and
					"as available" without warranties of any kind, whether express, implied, or statutory, including
					warranties of merchantability, fitness for a particular purpose, and non-infringement. We do
					not warrant that the Service will be uninterrupted, error-free, or that outputs will be accurate
					or complete. While we aim to source and index cases carefully, the underlying case data may
					contain inaccuracies.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">8. Limitation of Liability</h2>
				<p>
					<strong>8.1. Exclusion of Certain Damages.</strong> To the maximum extent permitted by law,
					neither party will be liable for indirect, incidental, special, consequential, or punitive damages,
					or for lost profits, revenues, or data, arising out of or relating to the Service.
				</p>
				<p>
					<strong>8.2. Liability Cap.</strong> To the maximum extent permitted by law, each party's aggregate
					liability arising out of or relating to the Service is limited to the amount you paid us in
					the twelve (12) months preceding the event giving rise to the claim (or, for Free-plan use,
					EUR 100). Nothing in these Terms limits liability for intent or gross negligence, for personal
					injury, or where liability cannot be limited under applicable law.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">9. Indemnification</h2>
				<p>
					<strong>9.1. By You.</strong> You will defend and indemnify us against third-party claims arising
					from your use of the Service in violation of these Terms or applicable law, including any claim
					that your Inputs infringe or misappropriate the rights of a third party.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">10. Changes to the Service and Terms</h2>
				<p>
					<strong>10.1. Modifications.</strong> We may modify the Service and these Terms. If a change
					is materially adverse to you, we will provide reasonable advance notice (for example, by email
					or through the Service). Continued use of the Service after the effective date of a change constitutes
					acceptance of the updated Terms. The current version is always available on this page.
				</p>

				<h2 class="pt-4 text-[17px] font-bold">11. General</h2>
				<p>
					<strong>11.1. Governing Law and Venue.</strong> These Terms are governed by the laws of
					the jurisdiction in which Asclevor's legal entity is registered (see the
					<a
						href="/imprint"
						class="underline underline-offset-2 transition-opacity hover:opacity-70">Imprint</a
					>), without regard to conflict-of-law rules. Mandatory consumer-protection rights in your
					country of residence remain unaffected.
				</p>
				<p>
					<strong>11.2. Entire Agreement; Severability.</strong> These Terms, together with the Privacy
					Policy and any order form, constitute the entire agreement between you and us regarding the
					Service. If any provision is found unenforceable, the remainder of the Terms will remain in
					full force.
				</p>
				<p>
					<strong>11.3. Contact.</strong> Questions about these Terms can be sent to
					<a
						href="mailto:contact@asclevor.com"
						class="underline underline-offset-2 transition-opacity hover:opacity-70"
						>contact@asclevor.com</a
					>.
				</p>
			</div>
		</article>
	</div>
</main>

<Footer />
