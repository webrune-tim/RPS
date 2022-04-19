<script>
  import '../reset.css';
  import '../styles.css';
</script>

<header>
  <h1>✊🏼, 🖐🏼, ✌🏼</h1>
  <h2>Rock, Paper, Scissors!</h2>
</header>
<main>
  <slot />
</main>
<footer>
  <p>Created with ❤️ by <a href="https://timsmith.tech">Tim Smith</a></p>
</footer>

<style>
  header {
  }
  footer {
    padding: 3rem;
    text-align: center;
    color: var(--text-color);
  }
</style>