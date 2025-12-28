<script>
	import Navbar from "$lib/navbar/navbar.svelte";

    let count = 1;
    let ids = [];
    let copiedMessage = "";
    let lastCounter = Math.floor(Math.random() * 0xffffff);

    const hexPad = (num, n) => num.toString(16).padStart(n, "0");

    function generateObjectId() {
        const ts = Math.floor(Date.now() / 1000);
        const tsHex = hexPad(ts, 8);

        let randBytes = new Uint8Array(5);  
        crypto.getRandomValues(randBytes);
        const randHex = Array.from(randBytes).map(b => hexPad(b, 2)).join("");

        lastCounter = (lastCounter + 1) & 0xffffff;
        const counterHex = hexPad(lastCounter, 6);

        return (tsHex + randHex + counterHex).toLowerCase();
    }

    function generateMany() {
        ids = [];
        const n = Math.max(1, Math.min(1000, parseInt(count) || 1));
        for (let i = 0; i < n; i++) ids.push(generateObjectId());
    }

    async function copyToClipboard(text) {
        await navigator.clipboard.writeText(text);
        copiedMessage = "Copied!";
        setTimeout(() => (copiedMessage = ""), 1500);
    }

    ids = [generateObjectId()];
</script>

<Navbar />

<div class="min-h-screen bg-gray-100 p-16">
<h2 class="text-4xl lg:text-6xl font-bold text-center  mb-6  text-red-600">Mongo ObjectId Generator</h2>

<section class="max-w-6xl mx-auto grid grid-cols-1 lg:grid-cols-2 mt-10 p-6 bg-white rounded-2xl shadow-md gap-4">

    <div>
        <p class="text-sm text-gray-600 mb-2">How many Mongo ObjectId required?</p>

        <input 
            type="number" 
            bind:value={count} 
            min="1" 
            max="1000" 
            class="w-full p-2 mb-4 border rounded-md"
        />

        <button 
            class="px-4 py-2 rounded-md bg-red-600 text-white hover:bg-red-700"
            on:click={generateMany}
        >
            Generate
        </button>

        <button 
            class="px-4 py-2 ml-2 rounded-md bg-red-600 text-white hover:bg-red-700"
            on:click={() => (ids = [])}
        >
            Clear
        </button>

        {#if copiedMessage}
            <p class="text-green-600 mt-2">{copiedMessage}</p>
        {/if}
    </div>

    <!-- Right -->
    <div class="space-y-2">
        {#each ids as id}
            <div class="flex justify-between items-center p-3 border-b">
                <div class="font-mono text-sm break-all">{id}</div>
                <button 
                class="p-2 rounded-md  cursor-pointer"
                on:click={() => copyToClipboard(id)}
                title="Copy ID"
            >
                <svg 
                    class="w-5 h-5 text-gray-700" 
                    fill="currentColor" 
                    viewBox="0 0 24 24"
                >
                    <path d="M19 21H8V7h11v14m0-16H8a2 2 0 0 0-2 2v14a2 
                    2 0 0 0 2 2h11a2 2 0 0 0 2-2V7a2 2 0 0 0-2-2m-3-4H4a2 
                    2 0 0 0-2 2v14h2V3h12V1Z" />
                </svg>
            </button>
            </div>
        {/each}
    </div>

</section>
</div>
