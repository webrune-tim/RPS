<script>
  const choices = ['✊🏼', '🖐🏼', '✌🏼'];
  let yourIndex = 0;
  let theirIndex = 0;
	let keyCode;
  let playing = '';
  let currentIndex = 0;
  let winner = '';

  function left() {
    if (yourIndex === 0) {
      yourIndex = choices.length - 1;
    } else {
      yourIndex--;
    }
  }

  function right() {
    if (yourIndex === choices.length - 1) {
      yourIndex = 0;
    } else {
      yourIndex++;
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
		keyCode = event.keyCode;
    switch (keyCode) {
      case 37:
        left();
        break;
      case 39:
        right();
        break;
      case 13:
        play();
        break;
      default:
        break;
    }
	}

  function whoWon() {
    if (yourIndex === currentIndex) {
      return 'It\'s a tie!';
    } else if (yourIndex === 0 && currentIndex === 2) {
      return 'You won :)';
    } else if (yourIndex === 1 && currentIndex === 0) {
      return 'You won :)';
    } else if (yourIndex === 2 && currentIndex === 1) {
      return 'You won :)';
    } else {
      return 'They won :(';
    }
  }

  function play() {
    let randomNumber = Math.floor(Math.random() * 20);
    playing = 'playing';
    setInterval(() => {
      if (randomNumber > 0) {
        theirLeft();
        randomNumber--;
        currentIndex = theirIndex;
      } else {
        playing = 'done'
        winner = whoWon()
      }
    }, 250)
  }

  function reset() {
    playing = '';
    yourIndex = 0;
    theirIndex = 0;
    currentIndex = 0;
    winner = '';
  }
</script>

<svelte:window on:keydown={handleKeydown}/>

<div class='wrapper'>
  {#if playing === 'done'}
    <section class="winner">{winner}</section>
  {/if}
  <section class='my-choice'>
    <div class='choice'>
      <button on:click={left}>◀</button>
      <p>{choices[yourIndex]}</p>
      <button on:click={right}>▶</button>
    </div>
    <p class='choice-p'>What is your choice?</p>
  </section>
  <section class='their-choice'>
    {#if playing === 'playing'}
      <p>{choices[theirIndex]}</p>
    {:else if playing === 'done'}
      <button class='reset-button' on:click={reset}>↺</button>
      <p>{choices[currentIndex]}</p>
    {:else}
      <button class='play-button' on:click={play}>▶</button>
      <p>❔</p>
    {/if}
  </section>
</div>


<style>
  .wrapper {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
  }

  .middle,
  .my-choice,
  .their-choice{
    margin: 2rem auto;
    flex: 1 1 550px;
    gap: 2rem;
  }

  .winner,
  .my-choice,
  .their-choice {
    min-height: 245px;
    border: 6px var(--text-color) solid;
    border-radius: 4rem;
    font-size: 5rem;
    padding: 2rem;
    margin: 1rem;
  }

  .winner {
    width: 100%;
    display: grid;
    place-items: center;
  }

  .their-choice p {
    text-align: center;
  }

  .choice,
  .their-choice {
    display: flex;
    justify-content: space-evenly;
    align-items: center;
  }

  .choice-p {
    font-size: 2rem;
    text-align: center;
  }

  .my-choice button {
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
    color: var(--highlight-color);
    font-size: 5rem;
    -webkit-text-stroke: 4px var(--text-color);
    margin-bottom: 0.5rem;
    cursor: pointer;
  }

  .reset-button {
    display: block;
    background: transparent;
    color: var(--highlight-color);
    font-size: 5rem;
    -webkit-text-stroke: 4px var(--text-color);
    margin-bottom: 0.5rem;
    cursor: pointer;
  }
</style>
