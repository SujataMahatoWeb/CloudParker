<script>
	import Navbar from "$lib/navbar/navbar.svelte";
	import QRCode from "qrcode";

    const qrTypes = {
        url: {
            label: "URL",
            title: "Enter your website URL here",
            placeholder: "",
            format: value => value
        },

        text: {
            label: "Text",
            title: "Enter your text here",
            placeholder: "Write something...",
            format: value => value
        },

        phone: {
            label: "Phone",
            title: "Enter your phone number here to make a call",
            placeholder: "+91",
            format: value => `tel:${value}`
        },

        email: {
            label: "Email",
            title: "Enter Your EMAIL details here",
            placeholder: "",
            format: value => `mailto:${value}`
        },

        sms: {
            label: "SMS",
            title: "Enter your SMS details here",
            placeholder: "",
            format: value => `smsto:${value};`
        },

        wifi: {
            label: "WiFi",
            title: "Enter your WIFI details here",
            placeholder: "SSID:PASSWORD",
            format: value => `WIFI:T:WPA;S:${value};`
        },

        event: {
            label: "Event",
            title: "Enter your WIFI details here",
            placeholder: "Event name",
            format: value => value
        },

        contact: {
            label: "Contact",
            title: "Enter your contact details here",
            placeholder: "John Doe, +91...",
            format: value => value
        }
    };

    let selectedType = $state("url");
    let inputValue = $state("");
    let qrDataUrl = $state("");

    $effect(() => {
        if (!inputValue) {
            qrDataUrl = "";
            return;
        }

        const formattedValue = qrTypes[selectedType].format(inputValue);

        QRCode.toDataURL(formattedValue, { width: 220 })
            .then(url => qrDataUrl = url)
            .catch(console.error);
            
    });

    function clearInput() {
        inputValue = "";
    }

    function downloadedQR() {
        const link = document.createElement("a");
        link.href = qrDataUrl;
        link.download = "qrcode.png";
        link.click();
    }
</script>
<Navbar />

<div class="bg-gray-50 min-h-screen">
    <h1 class="text-center py-20 text-4xl lg:text-5xl font-bold text-red-600">QRCode generator</h1>
    <div class="flex justify-center">
        <div class=" max-w-7xl bg-white p-6 rounded-xl shadow-lg w-full">
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-4">
                <div class="border-2 border-red-600 rounded">
                    <h3 class="font-bold mb-3 ">Options</h3>
                    {#each Object.entries(qrTypes) as [key, type]}
                        <button class="block w-full text-left px-3 py-2 mb-2 rounded {selectedType === key ? 'bg-red-600 text-white' : 'hover:bg-gray-100'}"
                        on:click={() => {
                            selectedType = key;
                            inputValue = "";
                        }}
                        >
                            {type.label}
                        </button>
                    {/each}
                </div>
                <div class="border-2 border-red-600 rounded p-4">
                    <p class="mb-2 font-semibold">
                        {qrTypes[selectedType].title}
                    </p>
                    <input type="text" class="w-full border p-2 rounded" placeholder={qrTypes[selectedType].placeholder} bind:value={inputValue} />

                    <p class="text-sm mt-2 text-gray-500">
                        (Your QR Code will be generated automatically)
                    </p>

                    <button class="mt-4 bg-gray-200 px-4 py-2 rounded"
                    on:click={clearInput}
                    >
                        Clear
                    </button>
                </div>

                <div class="border-2 border-red-600 rounded p-4 flex flex-col items-center">
					<p class="font-semibold mb-2">QR Code Preview</p>

					{#if qrDataUrl}
						<img src={qrDataUrl} alt="QR Code" class="mb-4" />
						<button
							class="bg-red-600 text-white px-4 py-2 rounded"
							on:click={downloadedQR}
						>
							Download
						</button>
					{:else}
						<p class="text-gray-400 text-center mt-10">No QR code yet</p>
					{/if}
				</div>
            </div>
        </div>
    </div>
</div>