<script>
  import CustomInput from "./CustomInput.svelte";
  import Toggle from "./Toggle.svelte";

  let val = "Max";
  let price = 0;
  let selectedOption = 1;
  let agreed;
  // let favColor = "red";
  let favColor = ["red"];

  $: console.log(val);
  $: console.log(selectedOption);
  $: console.log(price);
  $: console.log(agreed);
  $: console.log(favColor);

  function setValue(event) {
    val = event.target.value;
  }
</script>

<!-- <input type="text" value={val} on:input={setValue} /> -->
<!-- <input type="text" bind:value={val} /> -->

<CustomInput bind:val />

<Toggle bind:chosenOption={selectedOption} />

<input type="number" bind:value={price} />

<label
  >Agree to terms?
  <input type="checkbox" bind:checked={agreed} />
</label>

<h1>Color</h1>
<label>
  <input type="checkbox" value="red" name="color" bind:group={favColor} />
  Red
</label>

<label>
  <input type="checkbox" value="green" name="color" bind:group={favColor} />
  green
</label>

<label>
  <input type="checkbox" value="blue" name="color" bind:group={favColor} />
  blue
</label>
