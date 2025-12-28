<script>
    export let isDark = false;

    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    function toggleLight() {
        console.log('Navbar: dispatching light');
        dispatch("light");
    }

    function toggleDark() {
        console.log('Navbar: dispatching dark');
        dispatch("dark");
    }
</script>

<div class={`flex justify-between items-center px-4 py-4 sticky top-0 transition-colors duration-200
    ${isDark ? 'bg-gray-900 text-white shadow-2xl' : 'bg-white text-black shadow'}`}>
    <div class="flex items-center space-x-2">
        <img src="icon-192.png" class="h-8 w-8" alt="logo" />
        <h1 class="uppercase text-lg font-bold">Cloudparker</h1>
    </div>

    <div class="flex items-center space-x-4">
        {#if isDark}
            <!-- sun icon -->
            <svg on:click={toggleLight} xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="h-6 w-6 text-white"  fill="currentcolor"><title>white-balance-sunny</title><path d="M3.55 19.09L4.96 20.5L6.76 18.71L5.34 17.29M12 6C8.69 6 6 8.69 6 12S8.69 18 12 18 18 15.31 18 12C18 8.68 15.31 6 12 6M20 13H23V11H20M17.24 18.71L19.04 20.5L20.45 19.09L18.66 17.29M20.45 5L19.04 3.6L17.24 5.39L18.66 6.81M13 1H11V4H13M6.76 5.39L4.96 3.6L3.55 5L5.34 6.81L6.76 5.39M1 13H4V11H1M13 20H11V23H13" /></svg>
        {:else}
            <!-- moon icon -->
            <svg on:click={toggleDark} xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"
                class="h-6 w-6 cursor-pointer" fill="currentColor" aria-hidden="true">
                <path d="M2 12A10 10 0 0 0 15 21.54A10 10 0 0 1 15 2.46A10 10 0 0 0 2 12Z" />
            </svg>
        {/if}
    </div>
</div>
