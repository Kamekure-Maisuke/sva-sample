<script>
  export let name;
  export let bgColor;
</script>

<button
  class="{bgColor} text-white font-bold py-2 px-4 rounded"
  on:click
>
{name}
</button>