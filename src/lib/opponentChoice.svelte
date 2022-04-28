<script>
	import Toggle from '$lib/toggle.svelte';

	let on = false;

	export let moveStage;
</script>

<div class="stage-wrapper">
	<h1>Choice Your Opponent</h1>
	<section class="oppenent-choice">
		<p>Computer</p>
		<Toggle checked={on} handleToggle={() => (on = !on)} />
		<p>Friend</p>
	</section>
	<div>
		{#if on === false}
			<button on:click={() => moveStage('next')}>Continue againt computer</button>
		{:else}
			<p>Friend</p>
		{/if}
	</div>
</div>

<style>
	p {
		text-align: center;
	}
	.oppenent-choice {
		display: grid;
		grid-template-columns: 1fr 1fr 1fr;
		place-items: center;
	}

	.oppenent-choice p {
		display: block;
		font-size: calc(var(--botton-font-size) / 2);
	}

	@media (max-width: 600px) {
		.oppenent-choice p {
			display: block;
			font-size: calc(var(--botton-font-size) / 3);
		}
	}
</style>
