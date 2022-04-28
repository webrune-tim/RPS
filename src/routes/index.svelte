<script>
	import OpponentChoice from '$lib/opponentChoice.svelte';
	import Game from '$lib/game.svelte';
	import Rules from '$lib/rules.svelte';
	import Welcome from '$lib/welcome.svelte';

	let stage = 0;

	function moveStage(dir) {
		switch (dir) {
			case 'next':
				stage++;
				break;
			case 'back':
				stage--;
				break;
		}
	}
</script>

<div class="wrapper">
	{#if stage === 0}
		<Welcome {moveStage} />
	{:else if stage === 1}
		<Rules {moveStage} />
	{:else if stage === 2}
		<OpponentChoice {moveStage} />
	{:else}
		<Game />
	{/if}
</div>

<style>
	.wrapper {
		display: grid;
		place-items: center;
	}
</style>
