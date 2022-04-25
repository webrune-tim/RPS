<script>
  import StageButton from '$lib/stageButton.svelte';
  export let moveStage;
</script>

<div class="stage-wrapper">
  <h1>The Rules</h1>
  <img src="https://res.cloudinary.com/tihos/image/upload/c_scale,w_350/v1650783624/rpsls_hqnbir.jpg" alt="Rules" />
  <div>
    <button on:click={() => moveStage('back')}>back</button>
    <button on:click={() => moveStage('next')}>next</button>
  </div>
</div>