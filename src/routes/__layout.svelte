<script>
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
      <span>Pa er</span>
    </div>
    <div>
      <span>✂️</span>
      <span>Sci  ors</span>
    </div>
    <div>
      <span>🦎</span>
      <span>Li  rd</span>
    </div>
    <div>
      <span>🖖</span>
      <span>Sp ck</span>
    </div>
  </h1>
</header>
<main>
  <slot />
</main>
<footer>
  <p>Created with ❤️ by <a href="https://timsmith.tech">Tim Smith</a></p>
</footer>

<style>
  header {
    background-image: radial-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0));
  }

  h1 {
    width: 100vw;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    align-items: center;
    padding: 0 6rem;
  }

  div {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin: 1.5rem;
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
    header {
      padding: 1rem;
    }
    h1 {
      font-size: 3.5rem;
      padding: 0;
    }

    span:nth-child(2) {
    margin-top: -5.5rem;
  }
  }
</style>