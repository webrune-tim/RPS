<script>
  import { ga } from '@beyonk/svelte-google-analytics';
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
    ga.games.levelStart('Rock Paper Scissors Lizard Spock', 'Sheldon Cooper');
    let randomNumber = Math.floor(Math.random() * 20) + 10;
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


<section class='stage-wrapper game'>
  <div class='choice'>
    <button class="game-button" on:click={() => changePlayerChoice('left')}>&lt;</button>
    {choices[yourIndex]}
    <button class="game-button" on:click={() => changePlayerChoice('right')}>&gt;</button>
  </div>
  {#if playing === ''}
    <p>What is your choice?</p>
  {/if}
  {#if playing === 'playing'}
    <p>Good Luck</p>
    <div>
      {choices[theirIndex]}
    </div>
  {:else if playing === 'done'}
    <p>{winner}</p>
    <div>
      {choices[currentIndex]}
      <button class='reset-button game-button' on:click={reset}>↺</button>
    </div>
  {:else}
    <div>
      <button class='play-button game-button' on:click={play}>▶</button>
    </div>
  {/if}
</section>

<style>
  .game {
    min-height: 245px;
    font-size: 5rem;
  }

  .game p {
    font-size: 3.5rem;
    text-align: center;
  }

  .game-button {
    border: none;
    padding: 0 2rem;
    background: none;
    line-height: 4rem;
  }
  
  .play-button {
    background: transparent;
    color: var(--highlight-color);
    -webkit-text-stroke: 4px var(--text-color);
    margin-bottom: 0.5rem;
    cursor: pointer;
  }

  .play-button,
  .reset-button {
    font-size: var(--button-font-size);
    cursor: pointer;
    margin-bottom: 0.5rem;
    background: transparent;
  }

  .play-button {
    color: var(--bright-color);
    -webkit-text-stroke: 4px var(--text-color);
  }

  .reset-button {
    color: var(--text-color);
  }



  @media (max-width: 600px) {
    :root {
      --button-font-size: 4rem;
    }
    .game {
      font-size: 3rem;
    }

    .game p {
      margin-top: 0.5rem;
      font-size: 1.25rem;
      text-align: center;
    }
  }
</style>
