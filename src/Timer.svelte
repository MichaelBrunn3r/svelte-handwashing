<script>
	import ProgressBar from './ProgressBar.svelte';

	const washingLengthSeconds = 20;
	let secondsLeft = washingLengthSeconds;
	let isRunning = false;

	$: progress = secondsLeft / washingLengthSeconds * 100;

	function startTimer() {
		isRunning = true;
		const timer = setInterval(() => {
			secondsLeft -= 1;
			if(secondsLeft <= 0) {
				clearInterval(timer);
				isRunning = false;
				secondsLeft = washingLengthSeconds;
			}
		}
		, 1000);
	}
</script>

<style>
	h2 {
		margin: 0;
	}

	.start {
		background-color: rgb(154, 73, 73);
		width: 100%;
		margin: 10px 0;
	}

	.start[disabled] {
		background-color: #d6d6d6;
		cursor: not-allowed;
	}
</style>

<div bp="grid">
<h2 bp="offset-5@md 4@md 12@sm">Seconds left: {secondsLeft}</h2>
</div>

<ProgressBar {progress}/>

<div bp="grid">
	<button on:click={startTimer} disabled={isRunning} bp="offset-5@md 4@md 12@sm" class="start">Start</button>
</div>