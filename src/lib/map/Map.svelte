<script>

  const initMap = (s) => {
    let mapBeingCreated = [];
    for (let y = 0; y < s; y++) {
      const row = [];
      for (let x = 0; x < s; x++) {
        row.push({x, y})
      }
      mapBeingCreated.push(row);
    }
    return mapBeingCreated;
  }

  export let size = 32;

  let map = initMap(size);

  $: map = initMap(size)

  let hoveredColumn = ""

  const setHoveredColumn = (column) => {
    hoveredColumn = `${column.y}.${column.x}`
  }
</script>

<main>
  <div class="map">
    {#each map as row}
      <div class="row">
      {#each row as column}
        <div class="column" on:mouseover={() => setHoveredColumn(column)}
                            on:focus={() => setHoveredColumn(column)}>
        </div>
      {/each}
      </div>
    {/each}  
  </div>
  <p>{hoveredColumn}</p>
</main>

<style lang="scss">

.map {
  border: 5px solid olivedrab;
  width: fit-content;
  max-width: 80vw;
  max-height: 80vh;
  text-align: left;
  overflow: scroll;
  white-space: nowrap;

  .row {
    display: inline-block;

    .column {
      width: 50px;
      height: 50px;
      border: 1px dotted black;
      text-align: center;
      line-height: 50px;
    }
  }
}

</style>