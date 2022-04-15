<script>
  const choices = ['✊🏼', '🖐🏼', '✌🏼'];
  const randomChoice = choices[Math.floor(Math.random() * choices.length)];
  let choiceIndex = 0;
  let theirIndex = 0;
	let key;
	let keyCode;
  let playing = false;
  let randomNumber = 0;

  function left() {
    if (choiceIndex === 0) {
      choiceIndex = choices.length - 1;
    } else {
      choiceIndex--;
    }
  }

  function right() {
    if (choiceIndex === choices.length - 1) {
      choiceIndex = 0;
    } else {
      choiceIndex++;
    }
  }

  function theirLeft() {
    if (theirIndex === 0) {
      theirIndex = choices.length - 1;
    } else {
      theirIndex--;
    }
  }

  function handleKeydown(event) {
		key = event.key;
		keyCode = event.keyCode;
    if (keyCode === 37) {
      left();
    } else if (keyCode === 39) {
      right();
    }
	}

  function play() {
    randomNumber = Math.floor(Math.random() * 20);
    console.log('random', randomNumber);
    playing = true;
    console.log('playing', playing);
    while (randomNumber > 0) {
      theirLeft();
      randomNumber--;
    }
    playing = false;
  }
</script>

<svelte:window on:keydown={handleKeydown}/>

<h1>✊🏼, 🖐🏼, ✌🏼</h1>
<h2>Rock, Paper, Scissors!</h2>

<section class="my-choice">
  <div class="choice">
    <button on:click={left}>◀</button>
    <p>{choices[choiceIndex]}</p>
    <button on:click={right}>▶</button>
  </div>
  <p class="choice-p">What is your choice?</p>
</section>
<button class="play-button" on:click={play}>▶</button>
<section class="their-choice">
  {#if playing}
    <p>{choices[theirIndex]}</p>
  {:else}
    <p>❔</p>
  {/if}
</section>


<style >
  .my-choice,
  .their-choice {
    width: 45vw;
    margin: 2rem auto;
    border: 6px var(--text-color) solid;
    border-radius: 4rem;
    font-size: 5rem;
    padding: 2rem;
  }

  .their-choice p {
    text-align: center;
  }

  .choice {
    display: flex;
    justify-content: space-evenly;
    align-items: center;
  }

  .choice-p {
    font-size: 2rem;
    text-align: center;
  }

  .my-choice button,
  .play-button {
    font-size: 2rem;
    width: 4rem;
    height: 3rem;
    border-radius: 2rem;
    background: var(--text-color);
    cursor: pointer;
    color: var(--background-color);
    text-align: center;
  }

  .play-button {
    display: block;
    background: transparent;
    color: var(--text-color);
    font-size: 5rem;
    margin: -1rem auto 6rem auto;
  }
</style>
