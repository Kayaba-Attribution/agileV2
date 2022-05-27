<script>
	import { page } from '$app/stores';
	import { base } from '$app/paths';

	import { tweened } from 'svelte/motion';
	import { onMount } from 'svelte';
	import { themeChange } from 'theme-change';

	// NOTE: the element that is using one of the theme attributes must be in the DOM on mount
	// from: https://github.com/saadeghi/theme-change
	onMount(() => {
	themeChange(false)
	// 👆 false parameter is required for svelte
	})

    
</script>

<!-- Binding to the window disables themes changes -->
<!-- <svelte:window bind:innerWidth/> -->
<!-- <p>
	Inner Width: {innerWidth}
	Chain: {$wrongNetwork}
	Number: {$chain}
</p> -->

<div class="navbar fixed bg-base-300 z-40 rounded-box" style="width: 98%;">
	<div class="navbar-start">
	  <div class="dropdown">
		<label tabindex="0" class="btn btn-ghost lg:hidden">
		  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h8m-8 6h16" /></svg>
		</label>
		<ul tabindex="0" class="menu menu-compact dropdown-content mt-3 p-2 shadow bg-base-100 rounded-box w-52">
		<li><a href="/">Home</a></li>
		  <li tabindex="0">
			<a class="justify-between">
				Socials
			  <svg class="fill-current" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path d="M8.59,16.58L13.17,12L8.59,7.41L10,6L16,12L10,18L8.59,16.58Z"/></svg>
			</a>
			<ul class="p-2">
				<li><a href="">1</a></li>
				<li><a href="l">2</a></li>
			</ul>
		  </li>
		  <li><a href="/app">App</a></li>
		</ul>
	  </div>
	  <a class="btn btn-ghost normal-case text-xl hidden md:flex">
		<div class="avatar">
			<div class="w-12 rounded">
				<img class="mask mask-squircle" src="./logo.jpg" alt= "Logo">
			</div>
		  </div>
	  </a>

	  <a class="btn btn-ghost normal-case text-xl">Agile App</a>
	</div>
	<div class="navbar-center hidden lg:flex">
	  <ul class="menu menu-horizontal p-0">
		<li><a href="/">Home</a></li>
		<li tabindex="0">
		  <a>
			Socials
			<svg class="fill-current" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24"><path d="M7.41,8.58L12,13.17L16.59,8.58L18,10L12,16L6,10L7.41,8.58Z"/></svg>
		  </a>
		  <ul class="p-2  bg-base-200">
			<li><a href="">1</a></li>
			<li><a href="">2</a></li>
		  </ul>
		</li>
		<li><a href="/app">App</a></li>
	  </ul>
	</div>
	<div class="navbar-end flex">
		<div title="Change Theme" class=" dropdown dropdown-end flex">
			
			<div tabindex="0" class="m-1 normal-case btn-ghost btn">
				<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
					class="inline-block w-6 h-6 stroke-current md:mr-2">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
						d="M7 21a4 4 0 01-4-4V5a2 2 0 012-2h4a2 2 0 012 2v12a4 4 0 01-4 4zm0 0h12a2 2 0 002-2v-4a2 2 0 00-2-2h-2.343M11 7.343l1.657-1.657a2 2 0 012.828 0l2.829 2.829a2 2 0 010 2.828l-8.486 8.485M7 17h.01">
					</path>
				</svg>
				<span class="hidden md:inline">
					Change Theme
				</span>
				<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1792 1792"
					class="inline-block w-4 h-4 ml-1 fill-current">
					<path
						d="M1395 736q0 13-10 23l-466 466q-10 10-23 10t-23-10l-466-466q-10-10-10-23t10-23l50-50q10-10 23-10t23 10l393 393 393-393q10-10 23-10t23 10l50 50q10 10 10 23z">
					</path>
				</svg>
			</div>
			<div
				class=" mt-16 overflow-y-auto shadow-2xl top-px dropdown-content h-96 w-52 rounded-b-box bg-base-200 text-base-content">
				<ul class="p-4 menu compact">
					<li><a tabindex="0" data-set-theme="light" data-act-class="active">🌝
							 light</a></li>
					<li><a tabindex="0" data-set-theme="dark" data-act-class="active">🌚
							 dark</a></li>
					<li><a tabindex="0" data-set-theme="wireframe" data-act-class="active">📝
						 Wireframe</a></li>
					<li><a tabindex="0" data-set-theme="retro" data-act-class="active">👴
							 retro</a></li>
					<li><a tabindex="0" data-set-theme="lofi" data-act-class="active">👓
							 lofi</a></li>
					<li><a tabindex="0" data-set-theme="bumblebee" data-act-class="active">🐝
							 bumblebee</a></li>
					<li><a tabindex="0" data-set-theme="valentine" data-act-class="active">🌸
							 valentine</a></li>
					<li><a tabindex="0" data-set-theme="halloween" data-act-class="active">🎃
							 halloween</a></li>
					<li><a tabindex="0" data-set-theme="garden" data-act-class="active">🌷
							 garden</a></li>
					<li><a tabindex="0" data-set-theme="forest" data-act-class="active">🌲
							 forest</a></li>
					<li><a tabindex="0" data-set-theme="pastel" data-act-class="active">🖍
							 pastel</a></li>
				</ul>
			</div>
		</div>
	</div>
</div>


<style>
/* Add custom Styles here */
</style>
