<script>
  export let movies;
</script>

<div class="header">
  <h1>Discover Movies</h1>
</div>
<div class="content">
  {#each movies as movie}
    <div class="card">
<a sveltekit:prefetch href={"/movie/" + movie.id}>      <img
    src={`https://image.tmdb.org/t/p/w500/` + movie.poster_path}
    alt={movie.title}
  /></a>
      <div class="description">
        <h4>{movie.title}</h4>
        <p>{movie.release_date}</p>
      </div>
    </div>
  {/each}
</div>

<style>
  .header {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .description {
    padding: 0 1.5rem;
  }

  .content {
    width: 100%;
    height: auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    grid-column-gap: 1rem;
    grid-row-gap: 2rem;
  }
  .card{
      display:flex;
      flex-direction: column;
      justify-content: space-between;
      padding: 1rem;
  }
  img {
    width: 100%;
    height: auto;
    object-fit: cover;
    border-radius: 0.7rem;
  }
  a {
    text-decoration: none;
  }
</style>
