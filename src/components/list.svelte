<script lang="ts">
  import { fly } from "svelte/transition";
  import { flip } from "svelte/animate";
  interface item {
    text: string;
    key: string;
  }
  export let contents: item[] = [
    { text: "this", key: "this" },
    { text: "", key: "" },
    { text: "is", key: "is" },
    { text: "a", key: "a" },
    { text: "list", key: "list" },
  ];
  let k = 0;
</script>

<ul class="grid border-collapse w-fit">
  {#each contents as item (item.key)}
    <li
      animate:flip={{ duration: 200 }}
      in:fly={{ x: 100, duration: 200 }}
      class="p-1 h-8 border border-black"
    >
      {item.text}
    </li>
  {/each}
</ul>

<div>
  <button
    on:click={() => {
      contents.push({ text: "new", key: k.toString() });
      k += 1;
      contents = contents;
    }}>add bottom</button
  >
  <button
    on:click={() => {
      contents.splice(3, 0, { text: "new", key: k.toString() });
      k += 1;
      contents = contents;
    }}>add middle</button
  >
</div>
