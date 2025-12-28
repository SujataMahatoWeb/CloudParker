<script>
	import Navbar from "$lib/navbar/navbar.svelte";

	let appName = $state("");
	let websiteUrl = $state("");
	let supportEmail = $state("");
	let businessAddress = $state("");
	let dpoEmail = $state("");
	let otherDetails = $state("");

	let showPolicy = $state(false);

	function generatePolicy() {
	if (!appName || !websiteUrl || !supportEmail || !businessAddress) {
	alert("Please fill all required fields");
	return;
	}
	showPolicy = true;
	}
</script>
<Navbar />

<div class="min-h-screen bg-gray-100 p-6">
    <h1 class="text-3xl font-bold text-red-600 text-center mb-6">Privacy Policy Generator</h1>
    <div class="flex justify-center">
        <div class=" max-w-6xl bg-white p-6 rounded-xl shadow-lg w-full">
            <div class="grid grid-cols-1 lg:grid-cols-3 text-gray-500 gap-4">
                <label for="" >App Name <span class="text-red-600 font-bold">*</span>
                    <input type="text" bind:value={appName} class="rounded bg-gray-100 w-full border-gray-300">
                </label>
                <label for="">Website URL <span class="text-red-600 font-bold">*</span>
                    <input type="text" bind:value={websiteUrl} class="rounded bg-gray-100 w-full border-gray-300">
                </label>
                <label for="">Support Email<span class="text-red-600 font-bold">*</span>
                    <input type="text" bind:value={supportEmail} class="rounded bg-gray-100 w-full border-gray-300">
                </label>
                <label for="">Business Address <span class="text-red-600 font-bold">*</span>
                    <input bind:value={businessAddress} type="text" class="rounded bg-gray-100 w-full border-gray-300">
                </label>
                <label for="">Data Protection Oficer Email (Optional)
                    <input bind:value={dpoEmail} type="text" class="rounded bg-gray-100 w-full border-gray-300">
                </label>
                <label for="">Other Details (Optional)
                    <input bind:value={otherDetails } type="text"  class="rounded bg-gray-100 w-full border-gray-300">
                </label>

                <button onclick={generatePolicy} class="bg-red-600 text-white/80 font-semibold py-2 px-4 rounded my-4">
                    Generate Privacy Policy
                </button>
            </div>
        </div>
    </div>

	<div class="my-20 flex justify-center">
	<div class=" max-w-6xl bg-white p-6 rounded-xl shadow-lg w-full">
		{#if showPolicy}
			<section class="mt-10 prose max-w-none">
			<h2>Privacy Policy for {appName}</h2>
			<p><strong>Effective Date:</strong> {new Date().toLocaleDateString()}</p>


			<p>
			At <strong>{appName}</strong>, accessible from <strong>{websiteUrl}</strong>, we are committed to safeguarding the privacy of our users. This Privacy Policy outlines how we collect, use, store, and protect personal information. It also provides information about your rights under various data protection laws applicable to your jurisdiction.
			</p>


			<h3>1. Information We Collect</h3>
			<p>We collect and process the following categories of personal data:</p>
			<ul>
				<li>
					<span class="font-bold">Personal Information:</span> You have given us clear permission to process your data for specific purposes.Including your name, email address, phone number, and business address when you register for our services.
				</li>
				<li>
					<span class="font-bold">Usage Data:</span> Data related to how you interact with our services, including IP addresses, device identifiers, browser type, and pages visited.
				</li>
				<li>
					<span class="font-bold">Cookies and Tracking Technologies: </span> We use cookies to store information about your preferences and track your interactions with our services.
				</li>
				<li>
					<span class="font-bold">Financial Information:</span>  Payment details such as credit card numbers, billing addresses, and transaction data where applicable.
				</li>
				<li>
					<span>Communications:</span>Details of communications you have with our customer support or marketing teams.
				</li>
			</ul>

			<h3>2. Legal Basis for Processing Personal Data</h3>
			<p>We rely on the following legal bases to process personal data:</p>
			<ul>
			<li><span>Consent:</span> You have given us clear permission to process your data for specific purposes.</li>
			<li><span>Contractual Necessity:</span> Processing is necessary to fulfill our contractual obligations to you.</li>
			<li><span>Legal Obligations: </span>We may be required to process your data to comply with legal obligations.</li>
			<li><span>Legitimate Interests:</span> Processing is necessary for our legitimate interests, such as improving our services, preventing fraud, and ensuring network security.</li>
			</ul>
			<h3>3.How We Use Your Information</h3>
			<p>We use your personal data for the following purposes:</p>
			<ul>
				<li>
					To provide, operate, and maintain our app and services
				</li>
				<li>
					To improve and personalize your user experience
				</li>
				<li>
					To process payments and transactions
				</li>
				<li>
					To communicate with you for support, promotional purposes, and product updates
				</li>
				<li>
					To detect and prevent fraud, ensure security, and comply with legal obligations
				</li>
			</ul>


			<h3>4. Data  Retention</h3>
			<p>We retain personal data only for as long as necessary for the purposes outlined in this policy, unless otherwise required by law. The retention period varies depending on the type of data collected and the purpose of its use. You may request deletion of your data by contacting us at support@gmail.com.</p>


			<h3>5.Data Sharing</h3>
			<p>We may share your data with the following third parties:</p>
			<ul>
				<li>
					<span>Service Providers: </span>We share personal data with third-party vendors that provide services on our behalf (e.g., cloud storage, analytics, payment processors).
				</li>
				<li>
					<span>Legal Compliance:</span>We may share personal data to comply with laws, regulations, or legal requests.

				</li>
				<li>
					<span>Business Transfers:</span> In the event of a merger, acquisition, or sale of assets, your personal data may be transferred as part of the business transaction.
				</li>
			</ul>


			<h3>6. Data Protection and Security</h3>
			<p>We use industry-standard security measures to protect your personal data, including encryption and secure access controls. However, no method of transmission over the internet or electronic storage is 100% secure, and we cannot guarantee absolute security.</p>
		
			<h3>7. International Data Transfers</h3>
			<li>Your personal data may be transferred to and stored in countries outside of your jurisdiction, including countries with data protection laws that differ from those in your country. We take steps to ensure that your data remains protected in compliance with applicable laws, including through the use of standard contractual clauses.</li>

			<h3>8. Cookies and Tracking Technologies</h3>
			<li>We use cookies and other tracking technologies to improve your experience on our website. You may control the use of cookies through your browser settings, but disabling cookies may affect your ability to use certain features of our services.</li>

			<h3>9. Your Privacy Rights</h3>
			<p>Depending on your location, you may have the following rights regarding your personal data:</p>
			<ul>
				<li><span>Right to Access:</span>You can request a copy of the personal data we hold about you.</li>
				<li><span>Right to Correction: </span>You have the right to request that we correct any inaccuracies in your data.</li>
				<li><span>Right to Deletion:</span>You can request that we delete your personal data in certain circumstances.</li>
				<li><span>Right to Restrict Processing:</span> You may request that we limit how we process your personal data.</li>
				<li><span>Right to Data Portability:</span>You may request to receive your data in a structured, machine-readable format.</li>
				<li><span>Right to Object: </span>You have the right to object to our processing of your data, including for marketing purposes.</li>
			</ul>

			<h3>10. Specific Rights by Region</h3>
			<h3>10.1 GDPR (European Economic Area)</h3>
			<p>If you are located in the EEA, you have the following rights under the General Data Protection Regulation (GDPR):</p>
			<ul>
				<li>The right to access, correct, delete, or restrict your personal data.</li>
				<li>The right to data portability.</li>
				<li>The right to lodge a complaint with a data protection authority.</li>
				<li>The right to withdraw consent at any time.</li>
			</ul>

			<h3>10.2 CCPA (California, USA)</h3>
			<p>Under the California Consumer Privacy Act (CCPA), California residents have the following rights:</p>

			<ul>
				<li>The right to know what personal data we collect and how we use it.</li>
				<li>The right to request the deletion of your personal data.</li>
				<li>The right to opt-out of the sale of your personal data (we do not sell personal data).</li>
				<li>The right to non-discrimination for exercising your rights.</li>
			</ul>

			<h3>10.3 PIPEDA (Canada)</h3>
			<p>Under the Personal Information Protection and Electronic Documents Act (PIPEDA), Canadian residents have the following rights:</p>
			<ul>
				<li>The right to access personal data we collect and process.</li>
				<li>The right to correct inaccurate or incomplete data.</li>
				<li>The right to withdraw consent to data processing.</li>
			</ul>

			<h3>10.4 LGPD (Brazil)</h3>
			<p>Under the Brazilian General Data Protection Law (LGPD), Brazilian residents have the following rights:</p>
			<ul>
				<li>The right to confirm whether we process personal data.</li>
				<li>The right to access, correct, and delete personal data.</li>
				<li>The right to data portability.</li>
				<li>The right to withdraw consent at any time.</li>
			</ul>

			<h3>11. Data Breach Notification</h3>
			<p>In the event of a data breach, we will notify affected users and authorities in compliance with applicable laws. You will be informed via email or through a prominent notice on our website.</p>

			<h3>12. Changes to This Privacy Policy</h3>
			<p>We may update this Privacy Policy from time to time. We will notify you of any significant changes by updating the "Effective Date" and posting a notice on our website. Please review this policy periodically to stay informed about how we are protecting your information.</p>

			<h3>13. Contact Us</h3>
			<p>If you have any questions or concerns about this Privacy Policy, please contact us:</p>
			{#if dpoEmail}
			<p>Email: {dpoEmail}</p>
			<p>Business Address: {businessAddress}</p>
			{/if}


			{#if otherDetails}
			<h3>Additional Information</h3>
			<p>{otherDetails}</p>
			{/if}
			</section>
			{/if}
		</div>
	</div>
</div>