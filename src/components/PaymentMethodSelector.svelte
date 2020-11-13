<script>
    import { PROJECT_KEY } from '../stores/api';
    import { onMount, onDestroy } from 'svelte';
    import { CountryCode } from '../stores/CountryCode';

    let methods = [];
    let error;

    const loadMethods = async () => {
        const url = `https://api.paymentwall.com/api/payment-systems/?key=${$PROJECT_KEY}&country_code=${$CountryCode}`;
        const res = await fetch(url);
        methods = await res.json();

        if (!methods) {
            error = "No payment methods exist in this country! Please choose other country";
        } else {
            error = '';
        }
    }

    onMount(async () => {
        await loadMethods();
    });

    const unsub = CountryCode.subscribe(async (code) => {
        await loadMethods();
    });

    onDestroy(() => {
        // unsub from store
        console.log('component destroyed');
        unsub();
    });
</script>

<h3>Choose Your Payment Method</h3>
<p>{$CountryCode}</p>

{#if methods.length > 0}
    <div class="methods">
        {#each methods as method}
            <figure>
                <img src={method.img_url} alt={method.name}>
                <figcaption>{method.name}</figcaption>
            </figure>
        {/each}
    </div>
{:else}
    <div class="error">{ error }</div>
{/if}

<style>
    .methods {
        display: grid;
        grid-template-columns: repeat(6, 1fr);
        gap: 20px;
    }
</style>