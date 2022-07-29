<script>
  export let moveStage;
</script>

<div class="stage-wrapper">
  <h1>Welcome</h1>
  <p>
    Rock, Paper, Scissors, Lizards, Spock is a <a href="https://en.wikipedia.org/wiki/Rock_paper_scissors#Additional_weapons" target="_blank" rel="noreferrer noopener">reimaginaginatin</a> of <a href="https://en.wikipedia.org/wiki/Rock_paper_scissors" target="_blank" rel="noreferrer noopener">Rock, Paper, Scissors</a>  created by <a href="https://en.wikipedia.org/wiki/Sam_Kass" target="_blank" rel="noreferrer noopener">Sam Kass</a>. Opponents choice their weapons and compete in a classic game of chance.
  </p>
  <button on:click={() => moveStage('next')}>next</button>
</div>

<style>
  a {
    color: var(--bright-color);
  }
</style>
