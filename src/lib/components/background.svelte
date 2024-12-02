<script>
	import { onMount } from 'svelte';
	let snf1 = 1;
	let sn1 = [];
	let snf2 = 21;
	let sn2 = [];
	let snf3 = 41;
	let sn3 = [];
	let snf4 = 61;
	let sn4 = [];
	let position = [];

	while (sn1.length < 20) {
		sn1.push(snf1++);
	}
	while (sn2.length < 20) {
		sn2.push(snf2++);
	}
	while (sn3.length < 20) {
		sn3.push(snf3++);
	}
	while (sn4.length < 20) {
		sn4.push(snf4++);
	}

	while (position.length < 80) {
		const num = position.push(Math.floor(Math.random() * 100));
		if (position.indexOf(num) !== -1) {
			position.push(num);
		}
	}
</script>

<div id="background">
	{#each sn1 as sf1}
		<div class={`snowflakes snowflake1 sf${sf1}`} style={`left: ${position[sf1]}%`} />
	{/each}
	{#each sn2 as sf2}
		<div class={`snowflakes snowflake2 sf${sf2}`} style={`left: ${position[sf2]}%`} />
	{/each}
	{#each sn3 as sf3}
		<div class={`snowflakes snowflake3 sf${sf3}`} style={`left: ${position[sf3]}%`} />
	{/each}
	{#each sn4 as sf4}
		<div class={`snowflakes snowflake2 sf${sf4}`} style={`left: ${position[sf4]}%`} />
	{/each}
</div>

<style>
	#background {
		position: fixed;
		top: 0;
		left: 0;
		width: 100vw;
		height: 100vh;
		background: #323232;
		z-index: -1;
	}

	.snowflakes {
		border-radius: 50%;
		background: #fff;
		position: absolute;
		top: 0;
	}

	.snowflake1 {
		width: 0.5vw;
		height: 0.5vw;
	}
	.snowflake2 {
		width: 0.15vw;
		height: 0.15vw;
	}
	.snowflake3 {
		width: 0.25vw;
		height: 0.25vw;
	}
	.snowflake2 {
		width: 0.35vw;
		height: 0.35vw;
	}
</style>
