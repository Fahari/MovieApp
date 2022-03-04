<script context="module">
  export async function load({ fetch, params }) {
    const res = await fetch(
      `https://api.themoviedb.org/3/search/movie?api_key=${import.meta.env.VITE_API}&language=en-US&query=${params.id}&page=1&include_adult=false`
    );
    const searchedMovies = await res.json();
    if (res.ok) {
      return {
        props: { searchedMovies: searchedMovies.results },
      };
    }
    return {
      status: res.status,
      error: new Error("Could NOT FETCH movies!!!"),
    };
  }
</script>

<script>
  import.meta.env.VITE_API
  import { fly } from 'svelte/transition';
  export let searchedMovies;
</script>

<div class="content" in:fly={{ y:50, duration:500, delay:500 }} out:fly={{ duration:500 }}>
    {#each searchedMovies as movie}
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
  