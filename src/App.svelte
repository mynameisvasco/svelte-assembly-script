<script>
  import { onMount } from "svelte";

  import assembly from "../build/optimized.wasm";

  let add;
  let n1 = 0;
  let n2 = 0;
  let res = 0;

  onMount(async () => {
    let imports;
    const { instance } = await assembly({ ...imports });
    add = instance.exports.add;
  });
</script>

{res}
<input bind:value={n1} />
<input bind:value={n2} />
<button on:click={() => (res = add(n1, n2))}> Add </button>
