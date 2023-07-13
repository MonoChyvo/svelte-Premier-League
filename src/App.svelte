<script>
  import { paths } from './Data/regionPaths'
  import MapContainer from './Components/MapContainer.svelte'
  import MapRegion from './Components/MapRegion.svelte'
  import { getRegionData } from './Data/getRegionData.js'
  import RegionInformation from './Components/RegionInformation.svelte'
  import Overview from './Components/Overview.svelte'

  let activeRegion
  console.log(activeRegion)
</script>

<main class="app">
  {#if activeRegion}
    <RegionInformation
      region={getRegionData(activeRegion)}
      onClose={() => {
        activeRegion = undefined
      }}
    />
  {:else}
    <Overview />
  {/if}
  <div class="map_container">
    <MapContainer>
      {#each paths as { name, svgPath }}
        <MapRegion
          on:click={() => {
            activeRegion = name
          }}
          {svgPath}
          fillColour={activeRegion === name
            ? '#333'
            : getRegionData(name).colour}
          strokeColour="#000"
          strokeWidth="2px"
        />
      {/each}
    </MapContainer>
  </div>
</main>

<style>
  .app {
    display: flex;
  }

  .map_container {
    position: fixed;
    left: 0;
    right: 0;
    bottom: 0;
    top: 0;
    display: flex;
    justify-content: center;
  }

  @media (max-width: 860px) {
    .app {
      flex-direction: column;
    }

    .map_container {
      position: relative;
    }
  }
</style>
