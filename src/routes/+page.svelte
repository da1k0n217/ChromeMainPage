<script lang="ts">

    import {fade} from "svelte/transition";

    let Gsearchquery = '';
    let Xsearchquery = '';
    let Asearchquery = '';

    function Gsearch(event: SubmitEvent) {

        event.preventDefault();
        if(defsearchquery.trim() !== ''){

            window.location.href = `https://www.google.com/search?q=${encodeURIComponent(defsearchquery)}`;

            defsearchquery = '';
        }

    }
    function Xsearch(event: SubmitEvent) {

        event.preventDefault();
        if(defsearchquery.trim() !== ''){

            window.location.href = `https://x.com/search?q=${encodeURIComponent(defsearchquery)}&src=typed_query`;

            defsearchquery = '';

        }

    }
    function Asearch(event: SubmitEvent) {

        event.preventDefault();
        if(defsearchquery.trim() !== ''){

            window.location.href = `https://www.amazon.co.jp/s?k=${encodeURIComponent(defsearchquery)}`;

            defsearchquery = '';
        }

    }

    
    const brands: string[] = ['google', 'twitter', 'amazon'];
    let index = 0;
    let icon = brands[0];
    let name = 'Google';

    function changebrand() {

        index++

        if (index >= brands.length) {

            index = 0;

        }

        icon = brands[index];

        if (icon === 'google') {
            def = Gsearch;
            defsearchquery = Gsearchquery;
            name = 'Google';
        } else if (icon === 'twitter') {
            def = Xsearch;
            defsearchquery = Xsearchquery;
            name = 'X';
        } else if (icon === 'amazon') {
            def = Asearch;
            defsearchquery = Asearchquery;
            name = 'Amazon';
        }

    }


    import { onMount } from 'svelte';

    let show = false;

    let def = Gsearch;
    let defsearchquery = Gsearchquery;

    onMount(() => { show = true; });


</script>

<title>スマート検索タブ</title>

{#if show}
<main class="bg-gray-600 h-dvh flex flex-col justify-center p-10" transition:fade="{{delay: 250}}">

    <div class="bg-gray-500 backdrop-blur-md p-7 rounded-2xl">

        <div class="flex justify-center gap-2">

            <img src="./images/icon.png" alt="Logo" class="mt-4"/>
            <h1 class=" text-white text-4xl font-extralight pt-11">Smart Search</h1>

        </div>

        <div class="flex justify-center p-20 w-full gap-2">

            <div onclick={() => {changebrand()}}>

                <img src={`./images/${icon}.png`} alt="Search Icon" class="m-auto my-2 cursor-pointer hover:brightness-60 transition"/>
            
            </div>

            <form onsubmit={def}>

                <input type='text' bind:value={defsearchquery} placeholder="{name}で検索" class="search-input rounded-full w-144 border-2 drop-shadow-lg border-gray-300  focus:border-blue-500
                focus:ring-1 focus:ring-blue-500 hover:bg-gray-200 transition"/>

            </form>

        </div>

    </div>

    <div class="mt-20">

        <div class="mx-70 flex justify-center border-t-1 border-gray-400 gap-30">

            <div class="mt-20 rounded-xl w-20 h-20 bg-gray-500 hover:bg-gray-400 cursor-pointer flex items-center justify-center transition">

                <a href="https://gmail.com">
                    <img src="./images/gmail.png" alt="Gmail" class="w-10 h-10"/>
                </a>

            </div>

            <div class="mt-20 rounded-xl w-20 h-20 bg-gray-500 hover:bg-gray-400 cursor-pointer flex items-center justify-center transition">

                <a href="https://x.com">
                    <img src="./images/X.png" alt="X" class="w-8 h-8"/>
                </a>

            </div>

            <div class="mt-20 rounded-xl w-20 h-20 bg-gray-500 hover:bg-gray-400 cursor-pointer flex items-center justify-center transition">

                <a href="https://www.amazon.co.jp/">
                    <img src="./images/amazon2.png" alt="Amazon" class="w-10 h-10"/>
                </a>

            </div>

            <div class="mt-20 rounded-xl w-20 h-20 bg-gray-500 hover:bg-gray-400 cursor-pointer flex items-center justify-center transition">

                <a href="https://chatgpt.com/">
                    <img src="./images/chatgpt.png" alt="ChatGPT" class="w-10 h-10"/>
                </a>

            </div>

        </div>

    </div>

</main>
{/if}