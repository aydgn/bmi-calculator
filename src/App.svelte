<script>
	let height = null;
	let weight = null;
	$: bmi = Math.round((weight / height / height) * 10000);
</script>

<main>
	<h1>BMI CALCULATOR</h1>

	<div class="calculator">
		<fieldset>
			<legend>Your <b>height</b> in <b>cm</b> format</legend>
			<input
				type="number"
				bind:value={height}
				min="120"
				max="230"
				tabindex="0"
				placeholder="170"
			/>
			<input
				type="range"
				bind:value={height}
				min="120"
				max="230"
				tabindex="-1"
			/>
		</fieldset>

    <fieldset>
			<legend>Your <b>width</b> in <b>cm</b> format</legend>
			<input
				type="number"
				bind:value={weight}
				min="30"
				max="200"
				tabindex="0"
				placeholder="70"
			/>
			<input
				type="range"
				bind:value={weight}
				min="30"
				max="200"
				tabindex="-1"
			/>
		</fieldset>


		{#if bmi}
			<h2>Your BMI is <u>{bmi}</u></h2>

			{#if bmi <= 18.5}
				<h3 class="underweight">You are underweight</h3>
			{/if}

			{#if bmi > 18.5 && bmi <= 25}
				<h3 class="normal">You are normal weight</h3>
			{/if}

			{#if bmi > 25 && bmi <= 30}
				<h3 class="overweight">You are overweight</h3>
			{/if}

			{#if bmi > 30 && bmi <= 35}
				<h3 class="obese">You are obese</h3>
			{/if}

			{#if bmi > 35}
				<h3 class="morbidly-obese">You are morbidly obese</h3>
			{/if}
		{/if}
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	.calculator {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	input[type="number"] {
		font-size: 32px;
		width: 100px;
	}

  
	.underweight {
		color: #87b1d9;
	}

	.normal {
		color: #3dd365;
	}

	.overweight {
		color: #eee133;
	}

	.obese {
		color: #fd802e;
		font-weight: bold;
	}

	.morbidly-obese {
		color: #ff0000;
		font-weight: 900;
	}
</style>
