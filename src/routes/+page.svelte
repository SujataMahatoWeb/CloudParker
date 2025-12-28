<script lang="ts">
    export let isDark = false;
	import { goto } from "$app/navigation";
	import Navbar from "$lib/navbar/navbar.svelte";


    // 4 buttons
    // function handleGoToNotepad() {
    //     goto("/Notepad")
    // }

    // function handleGoToToDo() {
    //     goto("/ToDo")
    // }

    // function handleGoToWeb2PDF() {
    //     goto("/Web2PDF")
    // }

    // function handleGoToRecorder() {
    //     goto("/Recorder")
    // }

    // 2 buttons
    function handleGoToOpenPocker() {
        goto("/PockerPlanner")
    }

    function handleGoToOpenRetroBoard() {
        goto("/RetroBoard")
    }
    // LOAN EMI CALCULATOR
    function handleGoToHomeLone(){
        goto("/HomeLoan")
    }

    function handleGoToPersonalLoan() {
        goto("/PersonalLoan")
    }

    function handleGoToVehicalLoan() {
        goto("/VehicalLoan")
    }

    // LEGAL PAGE GENERATOR
    function handleGoToPrivacypolicyGenerator() {
        goto("/PrivacypolicyGenerator")
    }

    function handleGoToTermsConditionsGenerator() {
        goto("/TermsConditionsGenerator")
    }

    // QRCode Tools
    function handleGoToQRCodeGenerator() {
        goto("/QRCodeGenerator")
    }

    function handleGoToQRCodeRender() {
        goto("/QRCodeReader")
    }

    function handleGoToReturnRefundPolicyGenerator() {
        goto("/ReturnRefundPolicyGenerator")
    }
    //Calculator Tools
    function handleGoToBMIcalculator() {
        goto("/BMIcalculator")
    }

    function handleGoToVATcalculator() {
        goto("/VATcalculator")
    }

    // ID generator / validator tools
    function handleGoToNanoId(){
        goto("/NanoId")
    }

    function handleGoToMongoId() {
         goto("/MongoId")
    }

    function handleGoToMongovalidator() {
        goto("/Mongovalidator")
    }

    function handleGoToUuidGenerator() {
        goto("/UUIDgenerator")
    }

    function handleGoToUuidValidator() {
        goto("/UUIDvalidator")
    }
</script>
        <Navbar />
    
    <div>
    <div class="items-center justify-center text-center py-12">
        <h1 class="uppercase text-3xl lg:text-5xl font-bold text-red-600">Cloudparker</h1>
        <p class={`text-lg lg:text-xl py-4 transition-colors ${isDark ? 'text-gray-300' : 'text-gray-500'}`}>
            A diverse array of general-purpose tools
        </p>
    </div>

    

    <div class="flex justify-center mx-6">
        <div class="relative w-full max-w-2xl">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                stroke="gray" class="w-4 h-4 absolute left-3 top-1/2 -translate-y-1/2 pointer-events-none">
                <path stroke-linecap="round" stroke-linejoin="round"
                    d="m21 21-4.35-4.35m0 0A7.5 7.5 0 1 0 4.5 4.5a7.5 7.5 0 0 0 12.15 12.15Z" />
            </svg>

            <input type="text" placeholder="Search..."
                class={`pl-10 pr-4 py-3  w-full rounded-lg outline-none border-transparent transition
                    ${isDark ? 'bg-gray-700 text-white placeholder-gray-400 shadow-2xl' : 'bg-gray-100 text-gray-700 placeholder-gray-500 shadow-xl'}`} />
        </div>
    </div>

    </div>

    <!-- 4 buttons -->
    <!-- <div class=" max-w-6xl mx-auto mt-26 grid grid-cols-2 lg:grid-cols-4 gap-4">
        <button on:click={handleGoToNotepad} class="shadow-lg py-6 px-4 mx-4 border border-gray-100 rounded flex justify-between cursor-pointer">
            <div class="flex gap-2">
            <img src="notepad-192.png" class="h-10" alt="">
            <h1 class="font-bold mt-2">Notepad</h1>
            </div>
            
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="h-6 mt-2"><title>invoice-import-outline</title><path d="M18 20L21 22V3H3V9H5V5H19V18.26L18 17.6L15 19.6L12 17.6L9 19.6L6 17.6L5 18.26V15H3V22L6 20L9 22L12 20L15 22L18 20M11.5 17L10.08 15.58L12.67 13H3V11H12.67L10.08 8.41L11.5 7L16.5 12L11.5 17Z" /></svg>
        </button>
        <button on:click={handleGoToToDo} class="shadow-lg py-6 px-4 mx-4 border border-gray-100 rounded flex justify-between cursor-pointer">
            <div class="flex gap-2">
            <img src="todo-192.png" class="h-10" alt="">
            <h1 class="font-bold mt-2">ToDo</h1>
            </div>
            
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="h-6 mt-2"><title>invoice-import-outline</title><path d="M18 20L21 22V3H3V9H5V5H19V18.26L18 17.6L15 19.6L12 17.6L9 19.6L6 17.6L5 18.26V15H3V22L6 20L9 22L12 20L15 22L18 20M11.5 17L10.08 15.58L12.67 13H3V11H12.67L10.08 8.41L11.5 7L16.5 12L11.5 17Z" /></svg>
        </button>
        <button on:click={handleGoToWeb2PDF} class="shadow-lg py-6 px-4 mx-4 border border-gray-100 rounded flex justify-between cursor-pointer">
            <div class="flex gap-2">
            <img src="web2pdf-192.png" class="h-10" alt="">
            <h1 class="font-bold mt-2">Web2PDF</h1>
            </div>
            
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="h-6 mt-2"><title>invoice-import-outline</title><path d="M18 20L21 22V3H3V9H5V5H19V18.26L18 17.6L15 19.6L12 17.6L9 19.6L6 17.6L5 18.26V15H3V22L6 20L9 22L12 20L15 22L18 20M11.5 17L10.08 15.58L12.67 13H3V11H12.67L10.08 8.41L11.5 7L16.5 12L11.5 17Z" /></svg>
        </button>
        <button on:click={handleGoToRecorder} class="shadow-lg py-6 px-4 mx-4 border border-gray-100 rounded flex justify-between cursor-pointer">
            <div class="flex gap-2">
            <img src="screen-192.png" class="h-10" alt="">
            <h1 class="font-bold mt-2">Recorder</h1>
            </div>
            
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="h-6 mt-2"><title>invoice-import-outline</title><path d="M18 20L21 22V3H3V9H5V5H19V18.26L18 17.6L15 19.6L12 17.6L9 19.6L6 17.6L5 18.26V15H3V22L6 20L9 22L12 20L15 22L18 20M11.5 17L10.08 15.58L12.67 13H3V11H12.67L10.08 8.41L11.5 7L16.5 12L11.5 17Z" /></svg>
        </button>
    </div> -->

    <!-- 2 button -->
    <div class=" max-w-6xl mx-auto mt-26 grid grid-cols-1 lg:grid-cols-2 gap-10 lg:gap-0">
        <div class="shadow-lg py-20 px-6 mx-4 border border-gray-100 rounded">
            <img src="poker-192.png" class="h-10" alt="">
            <h1 class="font-bold py-6 text-xl">Pocker Planner</h1>
            <p class="text-gray-500 pb-6">A collaborative tool for agile teams to estimate effort and reach consensus on tasks using interactive, game-like cards.</p>
            <button on:click={handleGoToOpenPocker} class="py-2 px-6 rounded bg-gray-200 flex gap-3">
                Open Pocker
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="h-4 mt-1"><title>invoice-import-outline</title><path d="M18 20L21 22V3H3V9H5V5H19V18.26L18 17.6L15 19.6L12 17.6L9 19.6L6 17.6L5 18.26V15H3V22L6 20L9 22L12 20L15 22L18 20M11.5 17L10.08 15.58L12.67 13H3V11H12.67L10.08 8.41L11.5 7L16.5 12L11.5 17Z" /></svg>
            </button>
        </div>
        <div class="shadow-lg py-20 px-6 mx-4 border border-gray-100 rounded">
            <img src="retro-192.png" class="h-10" alt="">
            <h1 class="font-bold py-6 text-xl">Retro Board</h1>
            <p class="text-gray-500 pb-6">A digital tool designed to facilitate team retrospectives, primarily in Agile and Scrum project management methodologies.</p>
            <button on:click={handleGoToOpenRetroBoard} class="py-2 px-6 rounded bg-gray-200 flex gap-3">
                Open Retro Board
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="h-4 mt-1"><title>invoice-import-outline</title><path d="M18 20L21 22V3H3V9H5V5H19V18.26L18 17.6L15 19.6L12 17.6L9 19.6L6 17.6L5 18.26V15H3V22L6 20L9 22L12 20L15 22L18 20M11.5 17L10.08 15.58L12.67 13H3V11H12.67L10.08 8.41L11.5 7L16.5 12L11.5 17Z" /></svg>
            </button>
        </div>
    </div>

<section>
    <div class=" max-w-7xl mx-auto mt-26 grid grid-cols-1 lg:grid-cols-2 gap-4">
        <div class="mx-6 my-18 lg:my-0">
            <h1 class="lg:text-3xl text-2xl py-4 font-bold text-red-600">LOAN EMI CALCULATOR</h1>
            <p class="text-gray-500 text-justify font-medium">Use our Loan EMI Calculator to instantly calculate EMIs for home, personal, and vehicle loans. Enter loan amount, interest rate, and tenure to get accurate monthly EMI payments.</p>
        </div>

         <div>
        <div class="flex items-center justify-center  gap-6">
            <button on:click={handleGoToHomeLone} class="bg-gray-300 w-full flex mx-6  py-2 justify-center text-center items-center font-semibold rounded text-black/60 my-3 gap-2">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="h-8  w-8" fill="currentcolor"><title>home-account</title><path d="M12,3L2,12H5V20H19V12H22L12,3M12,8.75A2.25,2.25 0 0,1 14.25,11A2.25,2.25 0 0,1 12,13.25A2.25,2.25 0 0,1 9.75,11A2.25,2.25 0 0,1 12,8.75M12,15C13.5,15 16.5,15.75 16.5,17.25V18H7.5V17.25C7.5,15.75 10.5,15 12,15Z" /></svg>
                Home Loan EMI Calculator
            </button>
        </div>
        <div class="flex items-center justify-center gap-6">
            <button on:click={handleGoToPersonalLoan} class="bg-gray-300 flex w-full mx-6 py-2 text-center justify-center items-center font-semibold rounded text-black/60 mb-3 gap-2">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="h-8 w-8" fill="currentcolor"><title>account</title><path d="M12,4A4,4 0 0,1 16,8A4,4 0 0,1 12,12A4,4 0 0,1 8,8A4,4 0 0,1 12,4M12,14C16.42,14 20,15.79 20,18V20H4V18C4,15.79 7.58,14 12,14Z" /></svg>
                Personal Loan EMI Calculator
            </button>
        </div>
        <div class="flex items-center justify-center gap-6">
            <button on:click={handleGoToVehicalLoan} class="bg-gray-300 flex w-full mx-6 py-2 text-center justify-center items-center font-semibold rounded text-black/60 mb-3 gap-2">
                 <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="h-8 w-8" fill="currentcolor"><title>car-estate</title><path d="M3,6H16L19,10H21C22.11,10 23,10.89 23,12V15H21A3,3 0 0,1 18,18A3,3 0 0,1 15,15H9A3,3 0 0,1 6,18A3,3 0 0,1 3,15H1V8C1,6.89 1.89,6 3,6M2.5,7.5V10H10.5V7.5H2.5M12,7.5V10H17.14L15.25,7.5H12M6,13.5A1.5,1.5 0 0,0 4.5,15A1.5,1.5 0 0,0 6,16.5A1.5,1.5 0 0,0 7.5,15A1.5,1.5 0 0,0 6,13.5M18,13.5A1.5,1.5 0 0,0 16.5,15A1.5,1.5 0 0,0 18,16.5A1.5,1.5 0 0,0 19.5,15A1.5,1.5 0 0,0 18,13.5Z" /></svg>
                Vehical Loan EMI Calculator
            </button>
        </div>
        </div> 
    </div>
</section>

<!-- LEGAL PAGE GENERATOR -->
 <section>
    <div class=" max-w-7xl mx-auto mt-26 grid grid-cols-1 lg:grid-cols-2 gap-4">
        <div class="order-2 lg:order-1 lg:my-8">
        <div class="flex items-center justify-center gap-6">
            <button on:click={handleGoToPrivacypolicyGenerator} class="bg-gray-300 flex w-full mx-6 py-2 text-center justify-center items-center font-semibold rounded text-black/60 mb-3 gap-2">
                Privacy Policy Generator
            </button>
        </div>
        <div class="flex items-center justify-center gap-6">
            <button on:click={handleGoToTermsConditionsGenerator} class="bg-gray-300 flex w-full mx-6 py-2 text-center justify-center items-center font-semibold text-black/60 mb-3 gap-2">
                Terms Conditions Generator
            </button>
        </div>
        <div class="flex items-center justify-center gap-6">
            <button on:click={handleGoToReturnRefundPolicyGenerator} class="bg-gray-300 flex w-full mx-6 py-2 text-center justify-center items-center font-semibold text-black/60 mb-3 gap-2">
                Return Refund Policy Generator
            </button>
        </div>
        </div>
        <div class="mx-6 my-18 lg:my-0 order-1 lg:order-2">
            <h1 class="lg:text-3xl text-2xl py-4 font-bold text-red-600 uppercase">LEGAL PAGE GENERATOR</h1>
            <p class="text-gray-500 text-justify font-medium">Our free generators for Privacy Policy, Terms and Conditions, and Return and Refund Policy help you quickly create professional and customizable legal documents tailored to your website, app, or e-commerce store. Designed to comply with global regulations like GDPR, CCPA, and LGPD, these tools ensure your business is protected legally while offering transparency to your users. Each generator is simple to use and provides comprehensive policies covering essential areas like data protection, user obligations, and customer returns, building trust with your audience and minimizing legal risks.</p>
        </div>
    </div>
 </section>

 <!-- QRCode Tools -->
 <section>
    <div class="max-w-7xl mx-auto mt-26 grid grid-cols-1 lg:grid-cols-2 gap-4">
        <div class="mx-6 my-18 lg:my-0">
            <h1 class="lg:text-3xl text-2xl py-4 font-bold text-red-600 uppercase">QRCode Tools</h1>
            <p class="text-gray-500 text-justify font-medium">Use our QR Code Tools to effortlessly generate and read QR codes. Access the QR Code Generator to create custom QR codes and the QR Code Reader to decode QR codes instantly. Simplify your QR code tasks with ease!</p>
        </div>
        <div>
            <div class="flex items-center justify-center gap-6">
                <button on:click={handleGoToQRCodeGenerator} class="bg-gray-300 flex w-full mx-6 py-2 text-center justify-center items-center font-semibold rounded text-black/60 mb-3 gap-2">
                    QR Code Generator
                </button>
            </div>
            <div class="flex items-center justify-center gap-6">
                <button on:click={handleGoToQRCodeRender} class="bg-gray-300 flex w-full mx-6 py-2 text-center justify-center items-center font-semibold rounded text-black/60 mb-3 gap-2">
                    QR Code Reader
                </button>
            </div>
        </div>
    </div>
 </section>

<!-- Calculator Tools  -->
 <section>
    <div class="max-w-7xl mx-auto mt-26 grid grid-cols-1 lg:grid-cols-2 gap-4">
        <div class="mx-6 my-18 lg:my-0">
            <h1 class="lg:text-3xl text-2xl py-4 font-bold text-red-600 uppercase">Calculator Tools</h1>
            <p class="text-gray-500 text-justify font-medium">Make quick and accurate calculations with our Calculator Tools. Check your health with the BMI Calculator and compute taxes effortlessly with the VAT Calculator. Simplify your calculations today!</p>
        </div>
        <div>
            <div class="flex items-center justify-center gap-6">
                <button on:click={handleGoToBMIcalculator} class="bg-gray-300 flex w-full mx-6 py-2 text-center justify-center items-center font-semibold rounded text-black/60 mb-3 gap-2">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="w-8 h-8" fill="currentcolor"><title>calculator-variant</title><path d="M19 3H5C3.9 3 3 3.9 3 5V19C3 20.1 3.9 21 5 21H19C20.1 21 21 20.1 21 19V5C21 3.9 20.1 3 19 3M13 7.1L14.1 6L15.5 7.4L16.9 6L18 7.1L16.6 8.5L18 9.9L16.9 11L15.5 9.6L14.1 11L13 9.9L14.4 8.5L13 7.1M6.2 7.7H11.2V9.2H6.2V7.7M11.5 16H9.5V18H8V16H6V14.5H8V12.5H9.5V14.5H11.5V16M18 17.2H13V15.7H18V17.2M18 14.8H13V13.3H18V14.8Z" /></svg>
                    BMI Calculator
                </button>
            </div>
            <div class="flex items-center justify-center gap-6">
                <button on:click={handleGoToVATcalculator} class="bg-gray-300 flex w-full mx-6 py-2 text-center justify-center items-center font-semibold rounded text-black/60 mb-3 gap-2">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="w-8 h-8" fill="currentcolor"><title>calculator</title><path d="M7,2H17A2,2 0 0,1 19,4V20A2,2 0 0,1 17,22H7A2,2 0 0,1 5,20V4A2,2 0 0,1 7,2M7,4V8H17V4H7M7,10V12H9V10H7M11,10V12H13V10H11M15,10V12H17V10H15M7,14V16H9V14H7M11,14V16H13V14H11M15,14V16H17V14H15M7,18V20H9V18H7M11,18V20H13V18H11M15,18V20H17V18H15Z" /></svg>
                    VAT Calculator
                </button>
            </div>
        </div>
    </div>
 </section>


<!-- ID generator / validator tools -->
<section>
    <div class=" max-w-7xl mx-auto mt-26 grid grid-cols-1 lg:grid-cols-2 gap-4">
        <div class="order-2 lg:order-1">
        <div class="flex items-center justify-center  gap-6">
            <button on:click={handleGoToNanoId} class="bg-gray-300 w-full flex mx-6  py-2 justify-center text-center items-center font-semibold rounded text-black/60 my-3 gap-2">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="h-8 w-8" fill="currentcolor"><title>identifier</title><path d="M10 7V9H9V15H10V17H6V15H7V9H6V7H10M16 7C17.11 7 18 7.9 18 9V15C18 16.11 17.11 17 16 17H12V7M16 9H14V15H16V9Z" /></svg>
                Nano Id Generator
            </button>
        </div>
        <div class="flex items-center justify-center gap-6">
            <button on:click={handleGoToMongoId} class="bg-gray-300 flex w-full mx-6 py-2 text-center justify-center items-center font-semibold rounded text-black/60 mb-3 gap-2">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="h-8 w-8" fill="currentcolor"><title>identifier</title><path d="M10 7V9H9V15H10V17H6V15H7V9H6V7H10M16 7C17.11 7 18 7.9 18 9V15C18 16.11 17.11 17 16 17H12V7M16 9H14V15H16V9Z" /></svg>
                Mongo Object Id Generator
            </button>
        </div>
        <div class="flex items-center justify-center gap-6">
            <button on:click={handleGoToMongovalidator} class="bg-gray-300 flex w-full mx-6 py-2 text-center justify-center items-center font-semibold rounded text-black/60 mb-3 gap-2">
                 <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="w-8 h-8" fill="currentcolor"><title>check-decagram</title><path d="M23,12L20.56,9.22L20.9,5.54L17.29,4.72L15.4,1.54L12,3L8.6,1.54L6.71,4.72L3.1,5.53L3.44,9.21L1,12L3.44,14.78L3.1,18.47L6.71,19.29L8.6,22.47L12,21L15.4,22.46L17.29,19.28L20.9,18.46L20.56,14.78L23,12M10,17L6,13L7.41,11.59L10,14.17L16.59,7.58L18,9L10,17Z" /></svg>
                Mongo Object Id Validator
            </button>
        </div>
        <div class="flex items-center justify-center gap-6">
            <button on:click={handleGoToUuidGenerator} class="bg-gray-300 flex w-full mx-6 py-2 text-center justify-center items-center font-semibold rounded text-black/60 mb-3 gap-2">
                 <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="h-8 w-8" fill="currentcolor"><title>identifier</title><path d="M10 7V9H9V15H10V17H6V15H7V9H6V7H10M16 7C17.11 7 18 7.9 18 9V15C18 16.11 17.11 17 16 17H12V7M16 9H14V15H16V9Z" /></svg>
                UUID Generator
            </button>
        </div>
        <div class="flex items-center justify-center gap-6">
            <button on:click={handleGoToUuidValidator} class="bg-gray-300 flex w-full mx-6 py-2 text-center justify-center items-center font-semibold rounded text-black/60 mb-3 gap-2">
                 <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="w-8 h-8" fill="currentcolor"><title>check-decagram</title><path d="M23,12L20.56,9.22L20.9,5.54L17.29,4.72L15.4,1.54L12,3L8.6,1.54L6.71,4.72L3.1,5.53L3.44,9.21L1,12L3.44,14.78L3.1,18.47L6.71,19.29L8.6,22.47L12,21L15.4,22.46L17.29,19.28L20.9,18.46L20.56,14.78L23,12M10,17L6,13L7.41,11.59L10,14.17L16.59,7.58L18,9L10,17Z" /></svg>
                UUID Validator
            </button>
        </div>
        </div> 

        <div class="mx-6 my-18 lg:my-0 order-1 lg:order-2">
            <h1 class="lg:text-3xl text-2xl py-4 font-bold text-red-600 uppercase">ID Generator / validator tools</h1>
            <p class="text-gray-500 text-justify font-medium">Effortlessly generate and validate IDs with our ID Generator/Validator Tools. Create unique IDs using the Nano ID Generator, Mongo Object ID Generator, and UUID Generator. Verify their accuracy with the Mongo Object ID Validator and UUID Validator. Simplify ID management with ease!</p>
        </div>
    </div>
</section>

