<script>
	import Navbar from "$lib/navbar/navbar.svelte";

	let appName = $state("");
	let websiteURL = $state("");
	let supportEmail = $state("");
	let businessAddress = $state("");

	let generated = $state(false);
	let terms = $state(null);

	function TermsConditionGenerator() {
		if (!appName || !websiteURL || !supportEmail || !businessAddress) {
			alert("Please fill all fields");
			return;
		}

		terms = {
			appName,
			websiteURL,
			supportEmail,
			businessAddress,
			date: new Date().toLocaleDateString()
		};

		generated = true;
	}

</script>

<Navbar />

<div class="min-h-screen bg-gray-100 p-6">
	<h1 class="text-3xl font-bold text-red-600 text-center mb-6">Terms and Conditions</h1>
	<div class="flex justify-center">
		<div class="max-w-6xl bg-white p-6 rounded-xl shadow-lg w-full">
			<div class="grid grid-cols-1 lg:grid-cols-3 text-gray-500 gap-4">
				<label class="">App Name <span class="text-red-600">*</span>
					<input type="text" bind:value={appName} class="rounded bg-gray-100 w-full border-gray-300"/>
				</label>
				<label class="">Website URL <span class="text-red-600">*</span>
					<input type="text" bind:value={websiteURL} class="rounded bg-gray-100 w-full border-gray-300"/>
				</label>
				<label class="">Support Email <span class="text-red-600">*</span>
					<input type="text" bind:value={supportEmail} class="rounded bg-gray-100 w-full border-gray-300"/>
				</label>
				<label class="">Business Address <span class="text-red-600">*</span>
					<input type="text" bind:value={businessAddress} class="rounded w-full border-gray-300 bg-gray-100">
				</label>

				
			</div>
			<button onclick={TermsConditionGenerator} class="bg-red-600 text-white/80 rounded  py-2 px-4 my-4 cursor-pointer">Generate Terms and Conditions</button>
		</div>
	</div>
  
	<div class="my-20 flex justify-center">
	<div class=" max-w-6xl bg-white p-6 rounded-xl shadow-lg w-full">
	{#if generated}
      <section class="tmt-10 prose max-w-none">
        <h2 class="text-lg font-bold">
          Terms and Conditions for {terms.appName}
        </h2>

        <p class="text-gray-500">
        Effective Date: {terms.date}
      </p>

      <p>
        Welcome to {terms.appName}! These terms and conditions outline the rules
        and regulations for the use of {terms.appName}'s Website and Mobile
        Application, located at {terms.website}. By accessing or using our
        services, you agree to comply with these terms.
      </p>

        <h3 class="font-semibold">1. Acceptance of Terms</h3>
      <p>
        By using {terms.appName}'s website, mobile application, or any other
        services, you agree to be bound by these terms.
      </p>

      <h3 class="font-semibold">2. License to Use</h3>
      <p>
        {terms.appName} grants you a limited, non-exclusive, non-transferable, and revocable license to access and use our website and mobile app for personal, non-commercial purposes. You agree not to copy, distribute, modify, or make derivative works of our materials without express written permission.
      </p>

      <h3 class="font-semibold">3. User Obligations</h3>
	  <p>As a user of our services, you agree to the following conditions:</p>
      <ul class="list-disc ml-6 space-y-1">
		<li>You will use the services only for lawful purposes and comply with all applicable laws and regulations.</li>
        <li>You will not use the services to upload, post, or transmit any harmful or illegal content, including but not limited to viruses, malware, or infringing materials.</li>
        <li>You are responsible for maintaining the confidentiality of your account credentials and for all activities under your account.</li>
        <li>You agree not to reverse engineer, decompile, or disassemble any part of our services.</li>
        <li>You will ensure that all the information provided during registration or in connection with the use of our services is accurate, up-to-date, and complete.</li>
      </ul>

      <h3 class="font-semibold">4. Prohibited Activities</h3>
	  <p>You agree not to engage in the following prohibited activities:</p>
      <ul class="list-disc ml-6 space-y-1">
        <li>Attempting to access or tamper with areas of the site or systems that you are not authorized to access.</li>
        <li>Using any automated means, such as robots or scraping tools, to access our services without permission.</li>
        <li>Interfering with or disrupting the integrity or performance of our services.</li>
        <li>Engaging in any activity that violates the intellectual property rights of Loan Calculator or others.</li>
      </ul>

	  <h3 class="font-semibold">5. Payments and Fees</h3>
	  <p>Certain services provided by {terms.appName} may be subject to fees or subscription charges. You agree to pay all applicable fees and taxes in a timely manner. Failure to do so may result in the termination of your access to paid features. All payments are non-refundable unless otherwise specified in writing.</p>

	  <h3 class="font-semibold">6. Termination of Use</h3>
	  <p>We reserve the right to terminate or suspend your access to {terms.appName}'s services, without prior notice, for any reason, including but not limited to breach of these terms or any conduct that we believe is harmful to others or our business interests.</p>

	  <h3 class="font-semibold">7. Intellectual Property Rights</h3>
	  <p>All content, trademarks, logos, and intellectual property displayed on our website and mobile app are the property of {terms.appName} or its licensors. You agree not to use any such content for any commercial purpose without obtaining explicit written permission from us.</p>

	  <h3 class="font-semibold">8. Limitation of Liability</h3>
	  <p>To the fullest extent permitted by law, {terms.appName} is not liable for any direct, indirect, incidental, consequential, or punitive damages arising out of your use or inability to use the website, mobile app, or any other services provided. This includes any damages for loss of profits, data, or other intangible losses.</p>

	  <h3 class="font-semibold">9. Disclaimer of Warranties</h3>
	  <p>The services provided by {terms.appName} are offered "as is" without warranties of any kind, either express or implied. We do not warrant that the services will be error-free, uninterrupted, or free of harmful components. Any material downloaded or otherwise obtained through the use of our services is done at your own risk.</p>

	  <h3 class="font-semibold">10. Governing Law</h3>
	  <p>These terms and conditions are governed by and construed in accordance with the laws of the jurisdiction in which {terms.appName} is based, without regard to conflict of law provisions. You agree that any disputes arising out of or relating to these terms will be resolved exclusively in the competent courts of that jurisdiction.</p>

	  <h3 class="font-semibold">11. Data Privacy</h3>
	  <p>Our use of your personal data is governed by our Privacy Policy. By using our services, you agree that we may collect, use, and share your data in accordance with our privacy practices.</p>

      <h3 class="font-semibold">12. Modifications to the Services</h3>
      <p>
        We reserve the right to modify or discontinue, temporarily or permanently, any part of our services with or without notice. You agree that {terms.appName} shall not be liable for any modifications or discontinuation of our services.
      </p>

      <h3 class="font-semibold">13. Indemnification</h3>
      <p>
        You agree to indemnify, defend, and hold harmless {terms.appName}, its affiliates, and its respective officers, employees, and agents from any claims, liabilities, damages, losses, and expenses, including attorney's fees, arising out of your violation of these terms or misuse of our services.
      </p>

      <h3 class="font-semibold">14. Third-Party Links</h3>
      <p>
        Our services may contain links to third-party websites or services that are not owned or controlled by {terms.appName}. We are not responsible for the content, privacy practices, or availability of these third-party sites. Your use of third-party websites is at your own risk.
      </p>

      <h3 class="font-semibold">15.Mobile Application Use</h3>
      <p>
        When accessing our services via a mobile application, you may be required to grant certain permissions on your device (e.g., access to location, camera, contacts). You can control these permissions in your device settings, but disabling certain features may affect the functionality of the app.
      </p>

      <h3 class="font-semibold">16.Dispute Resolution</h3>
      <p>
        In the event of a dispute, you agree to first attempt to resolve the matter informally by contacting us at {terms.supportEmail} If the dispute cannot be resolved, it will be subject to binding arbitration in the jurisdiction of our choice.
      </p>

      <h3 class="font-semibold">17.Force Majeure</h3>
      <p>
        {terms.appName} will not be liable for any failure or delay in the performance of its obligations due to events beyond its reasonable control, including natural disasters, strikes, acts of terrorism, technical failures, or other unforeseen events.
      </p>

      <h3 class="font-semibold">18.Severability</h3>
      <p>
        These terms are governed by local applicable laws.
      </p>

      <h3 class="font-semibold">19. Entire Agreement</h3>
      <p>
        These terms constitute the entire agreement between you and Loan Calculator regarding the use of our services and supersede any prior agreements or understandings, whether written or oral.
      </p>

      <h3 class="font-semibold">20. Contact Information</h3>
	  <p>If you have any questions or concerns about these Terms and Conditions, please contact us:</p>
      <p>Email: {terms.supportEmail}</p>
      <p>Business Address: {terms.businessAddress}</p>
      </section>
	 
  	{/if}
	</div>
</div>
</div>