<script>
  import { writable } from "svelte/store";
  import { tweened } from "svelte/motion";
  import { cubicIn } from "svelte/easing";
  import { fade, fly, slide, scale } from "svelte/transition";
  import { flip } from "svelte/animate";

  import Spring from "./Spring.svelte";
  import { bind } from "svelte/internal";

  let boxInput;
  let showParagraph = false;
  const progress = tweened(0, {
    delay: 0,
    duration: 700,
    easing: cubicIn,
    // interpolate: () => {}
  });

  setTimeout(() => {
    progress.set(0.5);
  }, 1500);

  let boxes = [];

  function addBox() {
    boxes = [boxInput.value, ...boxes];
  }

  function discard(value) {
    boxes = boxes.filter((el) => el !== value);
  }
</script>

<!-- <progress value={$progress} /> -->
<!-- <Spring /> -->

<button
  on:click={() => {
    showParagraph = !showParagraph;
  }}
>
  Toggle
</button>
{#if showParagraph}
  <p in:fade out:fly={{ x: 300 }}>Can you see me?</p>
{/if}
<hr />
<input type="text" bind:this={boxInput} />
<button on:click={addBox}>Add</button>
{#if showParagraph}
  {#each boxes as box}
    <div
      transition:fly|local={{ x: 0, y: 300 }}
      on:click={discard.bind(this, box)}
      on:introstart={() => console.log("Adding the element start")}
      on:introend={() => console.log("Adding the element end")}
      on:outtrostart={() => console.log("Removing the element start")}
      on:outtroend={() => console.log("Removing the element end")}
      animate:flip={{ duration: 300 }}
    >
      {box}
    </div>
  {/each}
{/if}

<style>
  div {
    width: 10rem;
    height: 10rem;
    margin: 1rem;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    border-radius: 5px;
    padding: 1rem;
  }
</style>
