<script>
    import '../styles/global.css';
    let present = new Date().getFullYear();
  </script>
  
<svelte:head>
    <title>Movies App</title>
  </svelte:head>

<main class="content">
<slot></slot>
</main>
<footer>
<p class="foot">&copy; Kironji Kevin {present}</p>
</footer>

<style>
    .foot{
        display: flex;
        justify-content: center;
    }
</style>