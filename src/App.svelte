<script>
	import CountrySelector from './components/CountrySelector.svelte';
	import PaymentMethodSelector from './components/PaymentMethodSelector.svelte';
	import PaymentMethodForm from './components/PaymentMethodForm.svelte';
</script>

<!-- <svelte:head>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</svelte:head> -->

<main>
	<CountrySelector></CountrySelector>
	<PaymentMethodSelector></PaymentMethodSelector>
	<PaymentMethodForm></PaymentMethodForm>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>