<script>
	import Navbar from "$lib/navbar/navbar.svelte";

    let weight = "";
    let height = "";
    let bmi = "";
    let status = "";

    $: if (weight && height) {
		const h = height / 100;
		const result = weight / (h * h);

		bmi = result.toFixed(1);

		if (result < 18.5) status = "Underweight";
		else if (result < 24.9) status = "Normal";
		else if (result < 29.9) status = "Overweight";
		else status = "Obese";
	} else {
		bmi = "";
		status = "";
	}

	function clearAll() {
		weight = "";
		height = "";
		bmi = "";
		status = "";
	}

</script>

<Navbar />
<section class="max-w-6xl mx-auto">
    <div class=" p-6">
        <h1 class="text-4xl lg:text-6xl my-6 lg:my-10 font-bold text-center text-red-600">Body Mass Index (BMI) Calculator</h1>
        <p class="text-black/60 text-center">
        Quickly calculate your Body Mass Index (BMI) to track your health and fitness goals!
        </p>
    </div>
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-6"> 
        <div class="my-4 mx-3">
            <div class="my-3"> 
                <p class="py-2">Body weight (Kg) ?</p>
                <input type="number" bind:value={weight} class="w-full rounded border-gray-300 shadow-purple-400 shadow-2xl">
            </div>
            <div class="my-3">
                <p class="py-2">Body height (cm)?</p>
                <input type="number" bind:value={height} class="w-full rounded border-gray-300 shadow-purple-400 shadow-2xl">
            </div>
            <div class="my-3">
                <p class="py-2">Body Mass Index (BMI)</p>
                <input type="number" value={bmi} class="w-full rounded border-gray-300 shadow-purple-400 shadow-2xl">
            </div>

            <button class="bg-red-600 hover:bg-red-500 text-white uppercase py-2 px-3 rounded my-4" on:click={calculateBMI}>Calculator</button>

            <button class="bg-gray-200 hover:bg-gray-300 uppercase py-2 px-3 rounded mx-4" on:click={clearAll}>Clear</button>
        </div>
        <div
			class="bg-red-600 text-white flex flex-col items-center justify-center rounded-lg text-center h-56 lg:my-16 mx-3"
		>
			<p class="text-xl">Body Mass Index</p>
			<p class="text-lg">BMI</p>
			<p class="mt-2">
				{bmi || " "}
			</p>
			
		</div>
    </div>
</section>