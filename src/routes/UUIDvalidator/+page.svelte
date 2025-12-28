<script>
	import Navbar from "$lib/navbar/navbar.svelte";

    let uuid = "";
    let checkedId = "";
    let isValid = false;
    let hasChecked = false;

    function validateuuid() {
        const regex = /^[0-9a-f]{8}-[0-9a-f]{4}-[1-5][0-9a-f]{3}-[89ab][0-9a-f]{3}-[0-9a-f]{12}$/i;
        isValid = regex.test(uuid.trim());

        checkedId = uuid;
        hasChecked = true;    
    }

    function clearIDs() {
        uuid = "";
        checkedId = "";
        isValid = false;
        hasChecked = false;
    }
</script>
<Navbar />


<div class="my-10">
<h2 class="text-4xl md:text-5xl lg:text-6xl font-bold text-center  mb-6  text-red-600">UUID Validator</h2>

<section class="max-w-5xl lg:max-w-6xl  mx-auto  mt-10 p-6 bg-white rounded-2xl shadow-md gap-4">
        <p class="text-gray-500">Your UUID?</p>
        <input type="text" placeholder="Enter uuid here" bind:value={uuid} class="w-full lg:w-sm  my-2 p-2 border rounded mb-4 focous:outline-none focus:ring-0" />

        {#if hasChecked}
            <div class="rounded items-center justify-center text-center lg:items-start lg:justify-start lg:text-start">
                <p class="text-sm break-all py-2">{checkedId}</p>
                <button
                    class="px-4 m-4 py-2 rounded text-white text-sm"
                    class:bg-green-600={isValid}
                    class:bg-red-600={!isValid}
                >
                {isValid ? "VALID" : "INVALID"}
                </button>
            </div>
        {/if}

        <div class="lg:flex flex-wrap lg:gap-5 items-center">
        <button on:click={validateuuid}
        class="w-full lg:w-30 lg:h-12 bg-red-600 text-white py-2 rounded hover:bg-red-500 transition"
        >
            VALIDATE
        </button>

        <button on:click={clearIDs} class=" my-4 w-full lg:w-20 lg:h-12 bg-red-600 text-white py-2 rounded hover:bg-red-500 transition">CLEAR</button>
        </div>

        <p class="font-semibold text-gray-500">Sample UUID</p>
        <p class="text-gray-400 text-sm"><span>UUID v1:</span>  0a8d8210-7e8c-11ec-a22e-7954f59d589d</p>
        <p class="text-gray-400 text-sm"><span>UUID v4:</span>  d9b4379f-a2c5-4cb7-b6c2-eb52cae48545</p>
</section>
</div>
