<script lang="ts">
    import { onMount } from "svelte";
	import Navbar from "$lib/navbar/navbar.svelte";

    let count: number = 1;
    let ids: string[] = [];
    let copiedMessage: string = "";
    

    function generateUUId(): string {
        if (typeof crypto !== "undefined" && "randomUUID" in crypto) {
            return crypto.randomUUID();
        }
        return "xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx".replace(/[xy]/g, c => {
            const r = (Math.random() * 16) | 0;
            const v = c === "x" ? r : (r & 0x3) | 0x8;
            return v.toString(16);
        })
    }

    function generateMany() {
        ids = [];
        const n = Math.max(1, Math.min(1000, Math.floor(Number(count) || 1)));

        for (let i = 0; i < n; i++) {
            ids.push(generateUUId())
            
        }
    }

    async function copyToClipboard(text : string) {
        try{
            if (navigator.clipboard && navigator.clipboard.writeText) {
                await navigator.clipboard.writeText(text);
                copiedMessage = "Copied!";
            }else{
                const ta = document.createElement("textarea");
                ta.value = text;
                ta.style.position = "fixed";
                ta.style.opacity = "0";
                document.body.appendChild(ta);
                ta.select();
                document.execCommand("copy");
                ta.remove();
                copiedMessage = "copied!";
            }
        }catch(err){
            console.error("Copy failed:", err);
            copiedMessage = "Copy failed";
        }finally{
            setTimeout(() => (copiedMessage = ""), 1500);
        }
    }

    function downloadIds() {
        if (ids.length === 0) return;
        const blob = new Blob([ids.join("\n")], {type: "text/plain" });
        const url = URL.createObjectURL(blob);
        const a = document.createElement("a");
        a.href = url;
        a.download = `uuids-${new Date().toISOString()}.txt`;
        document.body.appendChild(a);
        a.click();
        a.remove();
        URL.revokeObjectURL(url);
    }

    onMount(() => {
        ids = [generateUUId()];
    });
</script>

<Navbar />

<div class="min-h-screen bg-gray-100 p-16">
<h2 class="text-4xl lg:text-6xl font-bold text-center  mb-6  text-red-600">UUID Generator</h2>

<section class="max-w-6xl mx-auto grid grid-cols-1 lg:grid-cols-2 mt-10 p-6 bg-white rounded-2xl shadow-md gap-4">

    <div>
        <p class="text-sm text-gray-600 mb-2">How many UUID required?</p>

        <input 
            type="number" 
            bind:value={count} 
            min="1" 
            max="1000" 
            class="w-full p-2 mb-8 border rounded-md"
        />

        <div class="">
        <button 
            class="w-full lg:w-30 py-2 rounded-md bg-red-600 text-white hover:bg-red-700"
            on:click={generateMany}
        >
            GENERATE
        </button>

        <button 
            class="py-2 w-full lg:w-30 lg:ml-2 my-4 rounded-md bg-red-600 text-white hover:bg-red-700"
            on:click={() => (ids = [])}
        >
            CLEAR
        </button>
        </div>

        {#if copiedMessage}
            <p class="text-green-600 mt-2">{copiedMessage}</p>
        {/if}
    </div>

    <!-- Right -->
    <div class="space-y-2">
        <h1 class="mx-4 font-bold text-gray-500">Output: UUIDs (v4)</h1>
        <button class="mx-4 bg-red-600 py-1 px-2 text-white rounded" on:click={downloadIds} disabled={ids.length === 0}>Download</button>
        {#each ids as id}
            <div class="flex justify-between items-center p-3">
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


