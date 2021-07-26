<script>
  let height = null;
  let weight = null;
  $: bmi = Math.round((weight / height / height) * 10000);
</script>

<main>
  <h1>BMI CALCULATOR</h1>

  <div class="calculator">
    <label>
      <input
        type="number"
        bind:value={height}
        min="120"
        max="230"
        tabindex="0"
				placeholder="170"
      />
      cm
      <input
        type="range"
        bind:value={height}
        min="120"
        max="230"
        tabindex="-1"
      />
    </label>

    <label>
      <input
        type="number"
        bind:value={weight}
        min="30"
        max="200"
        tabindex="0"
				placeholder="70"
      />
      kg
      <input
        type="range"
        bind:value={weight}
        min="30"
        max="200"
        tabindex="-1"
      />
    </label>

    {#if bmi}
      <p>Your BMI is <strong>{bmi}</strong></p>

      {#if bmi <= 18.5}
        <p class="underweight">You are underweight</p>
      {/if}

      {#if bmi > 18.5 && bmi <= 25}
        <p class="normal">You are normal weight</p>
      {/if}

      {#if bmi > 25 && bmi <= 30}
        <p class="overweight">You are overweight</p>
      {/if}

      {#if bmi > 30 && bmi <= 35}
        <p class="obese">You are obese</p>
      {/if}

      {#if bmi > 35}
        <p class="morbidly-obese">You are morbidly obese</p>
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
    width: 150px;
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
