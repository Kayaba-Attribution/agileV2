<script>
  import Chart from './Chart.svelte';

  let data = [1,2,3,4,5,6]

  function modifyData(i, delta){
    delta ? data[i]++ : data[i]--
  }

  function reset(){
    data = [1,2,3,4,5,6]
  }

  function randomize(){
    for (let i = 0; i < data.length; i++) {
      data[i] = getRandomInt(-10,10) 
    }
  }

  // Helpers
  function getRandomInt(min, max) {
    min = Math.ceil(min);
    max = Math.floor(max);
    return Math.floor(Math.random() * (max - min + 1) + min);
  }
  let chosenChart = "bar"
  function changeChart(_type) {
    chosenChart = _type
  }
</script>

<div class="mt-14">
  <div class="text-2xl text-center m-8">
    Change the values with by clicking the arrows below or click the randomize button and see the chart change!
  </div>
  
  <div class="flex items-center justify-center space-x-4">
    <button on:click={reset} class="btn btn-outline btn-info">Reset!</button>
    <button on:click={randomize} class="btn btn-outline btn-info">Randomize!</button>
  </div>

  <div class="flex items-center justify-center space-x-4 my-3">
    <button on:click={() => changeChart("bar")} class="btn btn-outline btn-info">Bars</button>
    <button on:click={() => changeChart("line")} class="btn btn-outline btn-info">Lines</button>
    <button on:click={() => changeChart("radar")} class="btn btn-outline btn-info">Radar</button>
 
  </div>

  <div class="flex items-center justify-center space-x-4 my-3">
    <button on:click={() => changeChart("pie")} class="btn btn-outline btn-info">PieChart</button>
    <button on:click={() => changeChart("polarArea")} class="btn btn-outline btn-info">polarArea</button>
  </div>

  <div class="flex flex-col-reverse w-full lg:flex-row space-x-5 items-center mr-5">

    <div class="grid grid-rows-2 grid-flow-col md:flex md:flex-col md:space-y-5 my-5">
      {#each data as item, i}
         <!-- content here -->
        <div class="flex items-center">
          <div class="mr-2">
            <p on:click={() => modifyData(i, true)}  class="text-center btn-outline btn-success w-8">⬆️</p>
            <p on:click={() => modifyData(i, false)} class="text-center btn-outline btn-error w-8">⬇️</p>
          </div>
          <input bind:value={data[i]} type="text" placeholder="Type here" class="input input-bordered input-info w-20 max-w-xs" />
        </div>

      {:else}
         <!-- empty list -->
      {/each}
    </div>
    
    <Chart data={data} chartType={chosenChart}/>
  </div>
</div>
