<script>
  export let moveStage;
</script>

<div class="stage-wrapper">
  <h1>Opponent Choice</h1>
  <div>
    <button on:click={() => moveStage('back')}>back</button>
    <button on:click={() => moveStage('next')}>next</button>
  </div>
</div>