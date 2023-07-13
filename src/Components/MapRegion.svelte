<script>
  export let svgPath
  export let fillColour = ''
  export let strokeColour = ''
  export let strokeWidth = ''
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<path
  on:click
  class="path"
  d={svgPath}
  fill={fillColour}
  stroke={strokeColour}
  style="stroke-width: {strokeWidth}"
/>

<style>
  .path {
    transition: fill 0.3s ease;
  }

  .path:hover {
    fill: #333;
    transition: fill 0.3s ease;
  }
</style>
