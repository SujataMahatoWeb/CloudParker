<script>
	import Navbar from "$lib/navbar/navbar.svelte";

	let appName = $state('');
	let websiteUrl = $state('');
	let supportEmail = $state('');
	let business = $state('');

	let showPolicy = $state(false);

	function refundPolicy() {
		if (!appName || !websiteUrl || !supportEmail || !business) {
			alert("please fill all required fields");
			return;
		}
		showPolicy = true;
	}
</script>

<Navbar />

<div class="min-h-screen bg-gray-100 p-6">
	<h1 class="text-3xl font-bold text-red-600 text-center mb-6">Return and Refund Policy Generator</h1>
	<div  class="flex justify-center">
		<div class="max-w-6xl bg-white p-6 rounded-xl shadow-lg w-full">
			<div class="grid grid-cols-1 lg:grid-cols-3 text-gray-500 gap-4">
				<label for="">App Name <span class="text-red-600 font-bold">*</span>
					<input type="text" bind:value={appName} class="rounded bg-gray-100 w-full border-gray-300" />
				</label>

				<label for="">Website URL <span class="text-red-600 font-bold">*</span>
					<input type="text" bind:value={websiteUrl} class="rounded bg-gray-100 w-full border-gray-300" />
				</label>

				<label for="">Support Email<span class="text-red-600 font-bold">*</span>
					<input type="text" bind:value={supportEmail} class="rounded bg-gray-100 w-full border-gray-300" />
				</label>

				<label for="">Business Address<span class="text-red-600 font-bold">*</span>
					<input type="text" bind:value={business} class="rounded bg-gray-100 w-full border-gray-300" />
				</label>
			</div>

			<button onclick={refundPolicy} class="bg-red-600 text-white/80 font-semibold py-2 px-4 rounded my-4">
				Generate Return and Refund Policy
			</button>
		</div>
	</div>

	<div class="my-20 flex justify-center">
		<div class="max-w-6xl bg-white p-6 rounded-xl shodow-lg w-full">
			{#if showPolicy}
				<section class="mt-10 prose max-w-none">
					<h2>Return and Refund Policy for {appName}</h2>
					<p><strong>Effective Date:</strong> {new Date().toLocaleDateString()}</p>

					<p>
					Thank you for shopping at{appName}. We strive to ensure that you are happy with your purchase, but if for any reason you are not satisfied, this Return and Refund Policy will guide you through the process. Please note that this policy applies only to purchases made directly from {appName}. If you have purchased from a third-party retailer, their return policy will apply.
					</p>

					<h3>1. Return Eligibility</h3>
					<p>Returns are applicable within X days (customize the timeframe) from the date of delivery. To qualify for a return, the following conditions must be met:</p>
					<ul>
						<li>
							The item must be unused, in its original condition, and in its original packaging.
						</li>
						<li>
							You must provide a valid proof of purchase (receipt or order number).
						</li>
						<li>
							Returns for certain items, such as perishable goods, personal care items, or custom-made products, are not accepted unless they are damaged or defective upon receipt.
						</li>
						<li>
							All returns must comply with the specific product's return policy if mentioned on the product page. Please ensure you review the return policy for each product before purchasing.
						</li>
					</ul>

					<h3>2.Product-Specific Return and Refund Policies</h3>
					<p>Certain products or services may have different return and refund policies depending on their nature. These specific policies will be displayed on the respective product or service pages. Please make sure to read the terms for each product carefully before purchasing. By completing the purchase, you agree to the terms specific to that product or service.</p>
				
					<h3>3.Refunds</h3>
					<p>Once we receive your returned item, we will inspect it and notify you via email. The refund will be processed after approval, and the funds will be credited to your original method of payment within a certain number of days, depending on your card issuer or payment provider’s policies.</p>
					<ul>
						<li>
							Refunds may take additional time due to technical or payment processing delays beyond our control. Please allow some extra time before contacting customer support.
						</li>
						<li>
							If your item was purchased during a promotional sale, the refund will be based on the discounted price.
						</li>
						<li>
							In cases where a partial refund is granted, we will explain the reason behind the decision.
						</li>
					</ul>

					<h3>4.Shipping and Handling Fees</h3>
					<p>Return shipping costs are the responsibility of the customer unless the item is defective or we shipped the wrong product. Shipping costs are non-refundable except in cases where a product is deemed defective or damaged. If you are returning items, please ensure you use a trackable shipping service or purchase shipping insurance. We are not responsible for lost or undelivered return packages.</p>

					<h3>5. Late or Missing Refunds</h3>
					<p>If you have not received your refund within the expected time frame, please follow these steps:</p>
					<ul>
						<li>First, check your bank or payment account for any pending transactions.</li>
						<li>Next, contact your credit card company or payment provider, as there may be processing delays before the refund is officially posted.</li>

						<li>If you have completed the steps above and still have not received your refund, please contact us at support@gmail.com. We will assist you in resolving the issue as soon as possible.</li>
					</ul>

					<h3>6. Non-Returnable and Non-Refundable Items</h3>
					<p>Certain products and services are non-returnable and non-refundable. These include, but are not limited to:</p>
					<ul>
						<li>
							Gift cards and vouchers
						</li>
						<li>
							Downloadable digital products such as eBooks, software, and licenses
						</li>
						<li>
							Personalized items and custom-made products
						</li>
						<li>
							Health and personal care items that have been opened or used
						</li>
						<li>
							Clearance or final sale items
						</li>
					</ul>
					<p>Please review product descriptions carefully before making a purchase to determine if the product is eligible for return or refund.</p>

					<h3>7. Exchanges</h3>
					<p>If you wish to exchange an item for a different size, color, or model, please contact us at {supportEmail} Exchanges are only permitted for the same product type and must adhere to the same return eligibility conditions mentioned above.</p>
					<ul>
						<li>If the item is out of stock or unavailable, you may opt for a refund or store credit in place of an exchange.</li>
						<li>Shipping times for exchanged items may vary depending on your location.</li>
					</ul>

					<h3>8. Delays in Returns and Refunds</h3>
					<p>There may be instances where the processing of returns or refunds takes longer than expected due to technical reasons or payment gateway issues. We appreciate your patience and recommend reaching out to our support team at {supportEmail} if you experience significant delays.</p>

					<h3>9. Cancellations</h3>
					<p>Order cancellations are allowed within a certain window of time after the order is placed (e.g., within 24 hours). After this period, the order will be processed and shipped, and the return and refund policy will apply. Some services or products may have non-cancellable terms, which will be indicated on the product or service page.</p>

					<h3>10. Contact Us</h3>
					<p>If you have any questions regarding this Return and Refund Policy, or if you need assistance with a return or refund, please contact our customer support team at {supportEmail}</p>
				</section>
			{/if}
		</div>
	</div>
</div>

