<script>
  export let moveStage;
  export let dir;
</script>

<button class='stage-button' on:click={() => moveStage({dir})}>
  {#if dir === 'next'}
    next
  {:else}
    back
  {/if}
</button>