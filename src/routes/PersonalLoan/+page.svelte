<script>
	import Navbar from "$lib/navbar/navbar.svelte";

    let loanAmount = 100000;
    let annualInterest = 10;
    let loanTenure = 12;
    let startDate = new Date().toISOString().split("T")[0]; 

    let emi = 0;
    let totalInterest = 0;
    let totalPrincipal = 0;

    function formatINR(num) {
        return num
            .toLocaleString("en-IN", {
                minimumFractionDigits: 2,
                maximumFractionDigits: 2
            });
    }

    function calculatorEMI() {
        let p = loanAmount;
        let r = annualInterest / 12 /100;
        let n  = loanTenure * 12;
        
        emi = p * r * Math.pow(1 + r, n) / (Math.pow(1 + r, n) - 1);
        emi = parseFloat(emi.toFixed(2));

        totalPrincipal = p;
        totalInterest = parseFloat((emi * n - p).toFixed(2));
    }

    function inWords(num) {
        num = parseInt(num);
        if (num === 0) return "Zero";
        const a = [
            '', 'One', 'Two', 'Three', 'Four', 'Five', 'Six', 'Seven', 'Eight', 'Nine', 'Ten',
            'Eleven', 'Twelve', 'Thirteen', 'Fourteen', 'Fifteen', 'Sixteen', 'Seventeen',
            'Eighteen', 'Nineteen'
        ];
        const b = [
            '', '', 'Twenty', 'Thirty', 'Forty', 'Fifty', 'Sixty', 'Seventy', 'Eighty', 'Ninety'
        ];
        function twoDigit(n) {
        if (n < 20) return a[n];
        return b[Math.floor(n / 10)] + (n % 10 ? " " + a[n % 10] : "");
    }

        function threeDigit(n) {
        let hundred = Math.floor(n / 100);
        let rest = n % 100;
        return (hundred ? a[hundred] + " Hundred" + (rest ? " " : "") : "") +
               (rest ? twoDigit(rest) : "");
    }

    if (num.toString().length > 9) return "Overflow";

    let crore = Math.floor(num / 10000000);
    let lakh = Math.floor((num % 10000000) / 100000);
    let thousand = Math.floor((num % 100000) / 1000);
    let hundredAndBelow = num % 1000;

    let str = "";
    
    if (crore) str += twoDigit(crore) + " Crore ";
    if (lakh) str += twoDigit(lakh) + " Lakh ";
    if (thousand) str += twoDigit(thousand) + " Thousand ";
    if (hundredAndBelow) str += threeDigit(hundredAndBelow);

        return str.trim();
    }


</script>

<Navbar />


<div class="min-h-screen bg-gray-100 p-6">
    <h1 class="text-3xl font-bold text-red-600 text-center mb-6">
        Personal Loan EMI Calculator
    </h1>
    <div class="flex justify-center">
    <div class=" max-w-6xl bg-white p-6 rounded-xl shadow-lg w-full">
        <div>
            <!-- <div class="grid grid-cols-1 lg:grid-cols-2 gap-10"> -->
                <div class="">
                    <label class="block font-semibold w-full ">Loan Amount</label>
                        <input type="range" bind:value={loanAmount} min="100000" max="100000000" class="w-full"/>
                            <input type="number" bind:value={loanAmount} min="100000" max="100000000" step="100000" class=" p-3 border rounded-lg my-4  lg:w-80 w-full" />
                    <p class="text-sm text-gray-500">{inWords(loanAmount)}</p>

                    <label class="block font-semibold">Annual Interest Rate (%)</label>
                        <input type="range" bind:value={annualInterest} min="1" max="20" step="0.1" class="w-full"/>
                        <input type="number" bind:value={annualInterest} min="1" max="20" step="0.1" class=" p-3 border rounded-lg my-4  lg:w-80 w-full" />

                    <label class="block font-semibold">Loan Tenure (Years)</label>
                        <input type="range" bind:value={loanTenure} min="1" max="30" step="1" class="w-full" />
                        <input type="number" bind:value={loanTenure} min="1" max="30" step="1" class="p-3 border rounded-lg my-4  lg:w-80 w-full"/>

                    <label class="block font-semibold">Loan Start Date </label>
                    <input type="date" bind:value={startDate} class="lg:w-80 w-full p-3 border rounded-lg mb-4 lg:ml-194 " />
                
                </div>

                <div>
                    
                <button on:click={calculatorEMI}
                    class="bg-red-600 lg:w-80 w-full lg:ml-194  text-white py-3 lg:mx-50 rounded-lg font-semibold hover:bg-red-700">
                    Calculate EMI
                </button>
                    
                    <div class="mt-6 space-y-2 p-4 lg:ml-176">
                        <p class="text-xl font-semibold text-gray-400">
                            Your Monthly EMI: ₹ <span class="text-gray-500 text-2xl px-5 text-right inline-block">{formatINR(emi)}</span>
                        </p>

                        <p class="text-lg font-semibold text-gray-400 py-2">
                            Total Interest Paid: ₹ <span class="text-gray-600 px-5 text-lg text-right inline-block">{formatINR(totalInterest)}</span>
                        </p>

                        <p class="text-lg font-semibold text-gray-400">
                            Total Principal Paid: ₹ <span class="text-gray-600 px-5 text-right inline-block">{formatINR(totalPrincipal)}</span>
                        </p>
                    </div>
                </div>
            <!-- </div> -->
        </div>

    </div>
    </div>
</div>
<style>
    input[type="range"] {
        -webkit-appearance: none;
        appearance: none;
        width: 70%;
        height: 8px;
        background: rgb(216, 214, 214); 
        border-radius: 5px;
        outline: none;
        cursor: pointer;
    }

    input[type="range"]::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    background: rgb(229, 12, 12);     /* thumb colour only */
    width: 18px;
    height: 18px;
    border-radius: 50%;
    cursor: pointer;
    }

    @media(max-width: 640px) {
        input[type="range"]{
            width: 100%;
            height: 6px;
        }
        input[type="range"]::-webkit-slider-thumb {
            width: 14px;
            height: 14px;
        }
    }
</style>