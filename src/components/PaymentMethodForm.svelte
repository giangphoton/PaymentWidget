<script>
    let fields = { cardholdername: '', answerA: '', answerB: '' };
    let errors = { cardholdername: '', answerA: '', answerB: '' };
    let valid = false;

    const submitHandler = () => {

    };
</script>

<svelte:head>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</svelte:head>

<h3>Fill Out The Payment Form</h3>

<form on:submit|preventDefault={submitHandler}>
    <div class="form-field">
        <label for="cardholdername">Cardholder Name: </label>
        <input type="text" id="cardholdername" bind:value={fields.cardholdername}>
        <div class="error">{ errors.cardholdername }</div>
    </div>
</form>