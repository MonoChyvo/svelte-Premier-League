<script>
  export let name
  export let seasons
</script>

<div class="container">
  <p class="name">{name}</p>
  {#each seasons.reverse() as { year, team, appearances }}
    <p>
      <b>{year}</b>
      with
      <b>{appearances}</b>
      appearances for
      <b
        style="color: {team === 'Manchester United'
          ? 'crimson'
          : team === 'Arsenal FC'
          ? 'red'
          : team === 'Chelsea FC'
          ? '#1510aa'
          : team === 'Blackburn Rovers'
          ? '#1057d1'
          : team === 'Manchester City'
          ? '#38a8e4'
          : team === 'Leicester City'
          ? '#2571fe'
          : 'gray'};">{team}</b
      >
    </p>
  {/each}
</div>

<style>
  .container {
    width: 100%;
    background-color: #071020;
    margin-bottom: 5px;
  }

  .name {
    margin-bottom: 10px;
    font-weight: bold;
  }
</style>
