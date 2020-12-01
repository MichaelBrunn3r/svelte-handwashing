<script>
	import Timer from './Timer.svelte';
	import HowTo from './HowTo.svelte';

	let audio;

	function timerEnds(e) {
		audio.play();
	}
</script>

<style>
	h1,h3 {
		text-align: center;
	}
</style>

<h1>Handwashing App</h1>

<Timer on:end={timerEnds} length=20/>
<HowTo/>


<h3>
	<a href="https://www.who.int/gpsc/clean_hands_protection/">Picture source</a>
	<a href="https://freesound.org/people/nckn/sounds/256113/">Sound source</a>
</h3>

<audio bind:this={audio} src="done.wav"/>