<script>
  import { onMount } from 'svelte'

  let svg
  let width = '0'
  let height = '0'

  const resizeSVG = () => {
    let svgBoundingBox = svg.getBBox()

    width = svgBoundingBox.x + svgBoundingBox.width + svgBoundingBox.x
    height = svgBoundingBox.y + svgBoundingBox.height + svgBoundingBox.y
  }

  onMount(resizeSVG)

  let windowHeight = 10
</script>

<svelte:window on:resize={resizeSVG} bind:innerHeight={windowHeight} />

<svg viewBox="0 0 {width} {height}" height={windowHeight - 10} bind:this={svg}>
  <g class="regions">
    <slot />
  </g>
</svg>
