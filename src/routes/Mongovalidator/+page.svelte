<script>
	import Navbar from "$lib/navbar/navbar.svelte";

    let objectId = "";
    let checkedId = "";
    let isValid = false;
    let hasChecked = false;

    function validateObjectId() {
        const regex = /^[a-fA-F0-9]{24}$/;
        isValid = regex.test(objectId);

        checkedId = objectId;
        hasChecked = true;    
    }

    function clearIDs() {
        objectId = "";
        checkedId = "";
        isValid = false;
        hasChecked = false;
    }
</script>
<Navbar />


<div class="my-10">
<h2 class="text-4xl md:text-5xl lg:text-6xl font-bold text-center  mb-6  text-red-600">Mongo ObjectId Validator</h2>

<section class="max-w-5xl lg:max-w-6xl  mx-auto  mt-10 p-6 bg-white rounded-2xl shadow-md gap-4">
        <p class="text-gray-500">Your Mongo ObjectId?</p>
        <input type="text" placeholder="Enter Mongo ObjectId here" bind:value={objectId} class="w-full lg:w-sm  my-2 p-2 border rounded mb-4 focous:outline-none focus:ring-0" />

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
        <button on:click={validateObjectId}
        class="w-full lg:w-30 lg:h-12 bg-red-600 text-white py-2 rounded hover:bg-red-500 transition"
        >
            VALIDATE
        </button>

        <button on:click={clearIDs} class=" my-4 w-full lg:w-20 lg:h-12 bg-red-600 text-white py-2 rounded hover:bg-red-500 transition">CLEAR</button>
        </div>

        <p class="font-semibold text-gray-500">Sample Mongo ObjectId</p>
        <p class="text-gray-400 text-sm">61f1181a5ea5b25a66e2b690</p>
</section>
</div>
