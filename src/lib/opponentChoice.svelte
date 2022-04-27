<script>
  import { ToggleCore } from "svelte-toggle";

  let on = false;

  export let moveStage;
</script>

<div class="stage-wrapper">
  <h1>Choice Your Opponent</h1>
  <ToggleCore toggled={on} let:label let:button>
    <!-- svelte-ignore a11y-label-has-associated-control -->
    <label {...label}>Computer or Freind</label>
    <button {...button} on:click={() => (on = !on)}>
      {on ? "Computer" : "Friend"}
    </button>
  </ToggleCore>
  <div>
    {#if on === true}
      <button on:click={() => moveStage('next')}>Continue againt computer</button>
    {:else}
      <p>Freind</p>
    {/if}
  </div>
</div>