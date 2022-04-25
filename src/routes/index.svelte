<script>
  import OpponentChoice from '$lib/OpponentChoice.svelte';
  import Game from '$lib/game.svelte';
  import Rules from '$lib/rules.svelte';
  import Welcome from '$lib/welcome.svelte';

  let stage = 0;

  function moveStage(dir) {
    switch (dir) {
      case 'next':
        stage++
        break;
      case 'back':
        stage--
        break;
    }
  }
</script>

<div class='wrapper'>
  {#if stage === 0}
    <Welcome moveStage={moveStage} />
  {:else if stage === 1}
    <Rules moveStage={moveStage} />
  {:else if stage === 2}
    <OpponentChoice moveStage={moveStage} />
  {:else}
    <Game />
  {/if}
</div>

<style>
  .wrapper {
    display: grid;
    place-items: center;
  }

  h1 {
    font-size: 5rem;
    font-weight: bold;
    color: #fff;
  }
</style>