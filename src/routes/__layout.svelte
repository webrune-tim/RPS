<script>
  import { GoogleAnalytics } from '@beyonk/svelte-google-analytics';
  import '../reset.css';
  import '../styles.css';
</script>

<header>
  <h1>
    <div>
      <span>🪨</span>
      <span>Rock</span>
    </div>
    <div>
      <span>📄</span>
      <span>Paper</span>
    </div>
    <div>
      <span>✂️</span>
      <span>Scissors</span>
    </div>
    <div>
      <span>🦎</span>
      <span>Lizard</span>
    </div>
    <div>
      <span>🖖</span>
      <span>Spock</span>
    </div>
  </h1>
</header>
<main>
  <slot />
</main>
<footer>
  <p>Created with ❤️ by <a href="https://timsmith.tech">Tim Smith</a></p>
  <p>Contribute on <a href="https://github.com/timscodebase/RPS">GitHub</a></p>
  <!-- Footer Ad -->
  <ins 
    class="adsbygoogle"
    style="display:block"
    data-ad-client="ca-pub-3189326528459169"
    data-ad-slot="4137371154"
    data-ad-format="auto"
    data-full-width-responsive="true"
  />
</footer>

<GoogleAnalytics properties={[ 'G-HTQDTMBL3V' ]} />

<style>
  header {
    padding: 4rem 0;
    background-image: radial-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0));
  }
  
  h1 {
    font-size: 4rem;
    font-weight: 400;
    color: var(--heading-color);
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-evenly;
    /* padding: 0 6rem; */
    gap: 2rem;
    text-align: center;
    text-shadow: 0 0 0.5rem var(--dark-highlight-color);
  }

  div {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  span:nth-child(1) {
    position: relative;
    z-index: 2;
  }
  span:nth-child(2) {
    margin-top: -6.5rem;
  }

  footer {
    padding: 3rem;
    text-align: center;
    color: var(--text-color);
  }

  @media (max-width: 600px) {
    h1 {
      font-size: 3.5rem;
      padding: 0;
    }

    header {
      padding: 2rem;
    }
    span:nth-child(1),
    span:nth-child(2) {
      font-size: 2rem;
    }

    span:nth-child(2) {
      margin-top: -3rem;
    }
  }
</style>