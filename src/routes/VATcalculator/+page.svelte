<script>
	import Navbar from "$lib/navbar/navbar.svelte";

    let vat = "";
    let net = "";
    let tax = "";
    let gross = "";

    $: if (vat && net) {
        tax = ((net * vat) / 100).toFixed(2);
        gross = (Number(net) + Number(tax)).toFixed(2);
    }else{
        tax = "";
        gross = "";
    }

    function clearAll() {
        vat = "";
        net = "";
        tax = "";
        gross = "";
    }

</script>
<Navbar />
<section class="max-w-6xl mx-auto">
    <div class=" p-6">
        <h1 class="text-4xl lg:text-6xl my-6 lg:my-10 font-bold text-center text-red-600">VAT Calculator</h1>
        <p class="text-black/60 text-center">
        Effortlessly calculate VAT for your purchases or invoices with our easy-to-use VAT Calculator!
        </p>
    </div>

    <div class="grid grid-cols-1 lg:grid-cols-2 gap-6"> 
        <div class="my-4 mx-3">
            <div class="my-3">
                <p class="py-2">VAT (%) ?</p>
                <input type="number" bind:value={vat} class="w-full rounded border-gray-300 shadow-purple-400 shadow-2xl">
            </div> 
            <div class="my-3">
                <p class="py-2">Net Amount?</p>
                <input type="number" bind:value={net}  class="w-full rounded border-gray-300 shadow-purple-400 shadow-2xl">
            </div> 
            <div class="my-3">
                <p class="py-2">Gross Amount?</p>
                <input type="number" bind:value={gross}  class="w-full rounded border-gray-300 shadow-purple-400 shadow-2xl">
            </div> 
            <div class="my-3">
                <p class="py-2">TAX Amount?</p>
                <input type="number" bind:value={tax}  class="w-full rounded border-gray-300 shadow-purple-400 shadow-2xl">
            </div> 
            <button class="bg-gray-200 hover:bg-gray-300 uppercase py-2 px-3 rounded" on:click={clearAll}>Clear</button>
        </div>
        <div
			class="bg-red-600 text-white/70 flex flex-col items-center justify-center rounded-lg text-center h-86 lg:my-16 mx-3"
		>
			<p class="text-xl font-bold">VAT Calculator</p>
			<p class="text-lg font-bold">TAX</p>
			<p class="mt-2">
				{tax || ""}
			</p>
			
			
		</div>
    </div>
</section>