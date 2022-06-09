<script>

    import { OnMount } from 'fractils'    
    import Typewriter from 'svelte-typewriter'
 
    import { fade, slide } from 'svelte/transition';
    import { flip } from 'svelte/animate'
    import { onMount } from 'svelte';
    import { reveal } from 'svelte-reveal';
    

    // ------ Animation ------- //
    import { afterUpdate } from 'svelte';

    let show = false;

    afterUpdate(() => {show = true;});
    // ------ --------- ------- //

    // Pass Variables to HTML
    let introText = `<strong>Mauris et arcu suscipit,</strong> tristique neque ac, feugiat elit. Morbi id sem nec velit porttitor aliquet et a nisl.`
	let rickGifSrc = './rickroll.gif';
	let rickName = 'Rick Astley';

    // Track Position
    let m = { x: 0, y: 0 };

    function handleMousemove(event) {
        m.x = event.clientX;
        m.y = event.clientY;
    }

    // Input made easy
    let name = '';

    // Render items made easy
    let cats = [
		{ id: 'J---aiyznGQ', name: 'Keyboard Cat' },
		{ id: 'z_AbfPXTKms', name: 'Maru' },
		{ id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat' }
	];

    // Reactive made easy
    let count = 0;
    let countTimes = 0;

    function handleClick() {
        if(count == 5){
            count = 0;
        } else{
            count += 1;
            countTimes++;
        }
    }




</script>



<svelte:head>
  <title>Agile Project App </title>
</svelte:head>
    
    <div class="mt-8">
        {#if show}
        
        <div class="flex flex-col w-full lg:flex-row my-12 space-y-6" >
            <div class="grid flex-grow md:my-10 md:w-80 card rounded-box place-items-left md:mr-3">
                
                <div use:reveal={{ transition: "fly" }} class="text-5xl md:text-8xl font-extrabold m-auto text-center md:text-left py-3" > Agile
                    <div class="text-transparent bg-clip-text bg-gradient-to-br from-yellow-300 to-blue-500">
                        Project App 
                    </div>
                </div>
                
                <div class="py-4 text-3xl font-bold text-center md:text-left">
                    <Typewriter loop>
                        <p>1. Lorem ipsum</p>
                        <p>2. dolor sit</p> 
                        <p>3. consectetur adipiscing </p> 
                    </Typewriter>
                </div>

                <div class="flex justify-center md:justify-start py-2 space-x-3 md:space-x-6 ">
                        <button on:click={handleClick} 
                        class="btn btn-outline md:btn-lg
                        {count == 0 ? 'btn-error' : 'btn-success'}">
                            Clicked {count} {count === 1 ? 'time' : 'times'}
                            <br>
                            Total: {countTimes}
                        </button>
    
                        <button on:mousemove={handleMousemove} class="btn btn-outline btn-info md:btn-lg" >
                            {m.x} x {m.y}
                        </button>
                        
                </div>
                <button on:click|once={() => {alert('ALERT')}} class="m-auto btn w-40 btn-outline btn-warning md:btn-lg" >
                    Alert Me
                </button>
            </div> 
            <div  class="grid flex-grow card rounded-box place-items-center">
    
                <img src="{rickGifSrc}" alt="{rickName}" use:reveal={{ transition: "fade" }} class="mask mask-hexagon">
            </div>
        </div>



        <div class="text-2xl text-center mb-6 md:p-6 md:m-6" use:reveal={{ transition: "fly" }}>
            {@html introText}
        </div>


        <div class="overflow-x-auto">
            <table class="table w-full">
              <!-- head -->
              <thead>
                <tr>
                  <th></th>
                  <th>Name</th>
                  <th>ID</th>
                  <th>Link</th>
                </tr>
              </thead>
              <tbody>
                {#each cats as { id, name }, i}
                <tr>
                    <th></th>
                    <th>{name}</th>
                    <th>{id}</th>
                    <th><a target="_blank" href="https://www.youtube.com/watch?v={id}"> Link</a></th>
                </tr>

                {/each}
              </tbody>
            </table>
        </div>
        
        <div class="form-control w-full m-auto max-w-xs">
            <label class="label">
              <span class="label-text">What is your name?</span>
              <span class="label-text-alt">{"HELLO " + name || 'stranger'}</span>
            </label>
            <input bind:value={name} type="text" placeholder="Type here" class="input input-bordered input-accent w-full max-w-xs" />
            <label class="label">
              <span class="label-text-alt">Hello {name || 'stranger'}!</span>
              <span class="label-text-alt">Alt label</span>
            </label>
        </div>

        <div class="mockup-code">
            <pre data-prefix=">"><code>git clone https://github.com/benekreng/agile</code></pre> 
            <pre data-prefix=">"><code>cd app</code></pre> 
            <pre data-prefix=">" class="text-warning"><code>yarn install</code></pre> 
            <pre data-prefix=">" class="text-success"><code>yarn dev --host</code></pre>
        </div>


        <div class="grid grid-cols-1 md:grid-cols-3 gap-4 justify-center  items-center">

                    <div class="card card-compact w-85 bg-base-100 shadow-xl">
                        <figure><img src="https://api.lorem.space/image/shoes?w=400&h=225" alt="Shoes" /></figure>
                        <div class="card-body">
                          <h2 class="card-title">Shoes!</h2>
                          <p>If a dog chews shoes whose shoes does he choose?</p>
                          <div class="card-actions justify-end items-center">
                            <input type="checkbox" class="toggle" checked />
                            <button class="btn btn-primary">Buy Now</button>
                          </div>
                        </div>
                    </div>

                    <div class="card w-85 bg-base-100 shadow-xl m-4">
                        <figure><img src="https://api.lorem.space/image/shoes?w=400&h=226" alt="Shoes" /></figure>
                        <div class="card-body">
                          <h2 class="card-title">
                            Shoes!
                            <div class="badge badge-secondary">NEW</div>
                          </h2>
                          <p>If a dog chews shoes whose shoes does he choose?</p>
                          <div class="card-actions justify-end">
                            <div class="badge badge-outline">Fashion</div> 
                            <div class="badge badge-outline">Products</div>
                          </div>
                        </div>
                    </div>
                    <div class="card card-compact w-85 bg-base-100 shadow-xl">
                        <figure><img src="https://api.lorem.space/image/shoes?w=401&h=225" alt="Shoes" /></figure>
                        <div class="card-body">
                          <h2 class="card-title">Shoes!</h2>
                          <p>If a dog chews shoes whose shoes does he choose?</p>
                          <div class="card-actions justify-end">
                            <div class="btn-group">
                                <input type="radio" name="options" data-title="1" class="btn" />
                                <input type="radio" name="options" data-title="2" class="btn" checked />
                                <input type="radio" name="options" data-title="3" class="btn" />
                                <input type="radio" name="options" data-title="4" class="btn" />
                              </div>
                          </div>
                        </div>
                    </div>
        </div>

        <div class="card lg:card-side bg-base-100 shadow-xl">
            <figure><img src="https://api.lorem.space/image/album?w=400&h=400" alt="Album"></figure>
            <div class="card-body">
              <h2 class="card-title">New album is released!</h2>
              <p>Click the button to listen on Spotiwhy app.</p>
              <div class="card-actions justify-end">
                <button class="btn btn-primary">Listen</button>
              </div>
            </div>
          </div>



        {/if}
    </div>
    
    