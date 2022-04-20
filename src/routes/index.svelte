<script>
  const choices = ['🪨', '📄', '✂️', '🦎', '🖖🏼'];
  let yourIndex = 0;
  let theirIndex = 0;
  let playing = '';
  let currentIndex = 0;
  let winner = '';

  function changePlayerChoice(dir) {
    switch (dir) {
      case 'left':
        yourIndex = (yourIndex - 1 + choices.length) % choices.length;
        break;
      case 'right':
        yourIndex = (yourIndex + 1) % choices.length;
        break;
    }
  }

  function theirLeft() {
    if (theirIndex === 0) {
      theirIndex = choices.length - 1;
    } else {
      theirIndex--;
    }
  }

  function handleKeydown({keyCode}) {
    switch (keyCode) {
      case 37:
      changePlayerChoice('left');
        break;
      case 39:
      changePlayerChoice('right');
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
    } else if (yourIndex === 0 && currentIndex === 3) {
      return 'You won 😀';
    } else if (yourIndex === 1 && currentIndex === 0) {
      return 'You won 😀';
    } else if (yourIndex === 2 && currentIndex === 1) {
      return 'You won 😀';
    } else if (yourIndex === 3 && currentIndex === 4) {
      return 'You won 😀';
    } else if (yourIndex === 4 && currentIndex === 2) {
      return 'You won 😀';
    } else if (yourIndex === 2 && currentIndex === 3) {
      return 'You won 😀';
    } else if (yourIndex === 3 && currentIndex === 1) {
      return 'You won 😀';
    } else if (yourIndex === 1 && currentIndex === 4) {
      return 'You won 😀';
    } else if (yourIndex === 4 && currentIndex === 0) {
      return 'You won 😀';
    } else if (yourIndex === 0 && currentIndex === 2) {
      return 'You won 😀';
    } else {
      return 'They won 🤬';
    }
  }

  function play() {
    let randomNumber = Math.floor(Math.random() * 20);
    playing = 'playing';
    const loop = setInterval(() => {
      if (randomNumber > 0) {
        theirLeft();
        randomNumber--;
        currentIndex = theirIndex;
      } else {
        playing = 'done'
        clearInterval(loop);
        winner = whoWon()
      }
    }, 250)
  }

  function reset() {
    playing = '';
    theirIndex = 0;
    currentIndex = 0;
    winner = '';
  }
</script>

<svelte:window on:keydown={handleKeydown}/>

<div class='wrapper'>
  <section class='game'>
    <div class='choice'>
      <button on:click={() => changePlayerChoice('left')}>◀</button>
      {choices[yourIndex]}
      <button on:click={() => changePlayerChoice('right')}>▶</button>
    </div>
    {#if playing === ''}
    <p class='choice-p'>What is your choice?</p>
    {/if}
    {#if playing === 'playing'}
      {choices[theirIndex]}
    {:else if playing === 'done'}
      <p>{winner}</p>
      {choices[currentIndex]}
      <button class='reset-button' on:click={reset}>↺</button>
    {:else}
      <button class='play-button' on:click={play}>▶</button>
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
  
  .game {
    margin: 2rem auto;
    flex: 1 1 550px;
    gap: 2rem;
  }
  
  .game {
    min-height: 245px;
    border: 6px var(--highlight-color) solid;
    background-color: var(--background-color);
    box-shadow: 0 0 10px var(--dark-highlight-color);
    border-radius: 4rem;
    text-align: center;
    margin: 0 auto;
    flex: 1 1 550px;
    font-size: 5rem;
    padding: 2rem;
    margin: 2rem;
    gap: 2rem;
  }

  .game p {
    font-size: 3.5rem;
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

  @media (max-width: 600px) {
    .game p {
      margin-top: 0.5rem;
      font-size: 1.25rem;
      text-align: center;
    }
  }

  .game button {
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
    background: transparent;
    color: var(--highlight-color);
    font-size: 5rem;
    -webkit-text-stroke: 4px var(--text-color);
    margin-bottom: 0.5rem;
    cursor: pointer;
  }

  .reset-button {
    background: transparent;
    color: var(--text-color);
    font-size: 5rem;
    margin-bottom: 0.5rem;
    cursor: pointer;
  }
</style>
