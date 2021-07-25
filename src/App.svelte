<script>
  import { writable } from "svelte/store";
  import { tweened } from "svelte/motion";
  import { cubicIn } from "svelte/easing";

  import Spring from "./Spring.svelte";

  const progress = tweened(0, {
    delay: 0,
    duration: 700,
    easing: cubicIn,
    // interpolate: () => {}
  });

  setTimeout(() => {
    progress.set(0.5);
  }, 1500);
</script>

<Spring />

<!-- <progress value={$progress} /> -->
