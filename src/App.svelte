<script>
  import ContactCard from "./ContactCard.svelte";

  let name = "Max";
  let title = "";
  let description = "";
  let image = "";
  let age = 30;

  $: uppercaseName = name.toUpperCase();

  $: console.log(name);

  $: if (name === "Maximiline") {
    console.log("It run");
    age = 31;
  }

  function incrementAge() {
    age += 1;
  }

  function changeName() {
    name = "Maximiline";
  }

  function nameInput(event) {
    const enteredValue = event.target.value;
    name = enteredValue;
  }
</script>

<h1>Hello {uppercaseName}, my age {age}</h1>
<button on:click={incrementAge}>Add age</button>
<!-- <button on:click={changeName}>Change name</button> -->
<!-- <input type="text" value={name} on:input={nameInput} /> -->
<input type="text" bind:value={name} />
<input type="text" bind:value={title} />
<input type="text" bind:value={image} />
<textarea rows="3" bind:value={description} />

<ContactCard userName={name} jobTitle={title} {description} userImage={image} />

<style>
  h1 {
    color: purple;
  }
</style>
