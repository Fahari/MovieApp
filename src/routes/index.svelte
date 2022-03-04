<script context="module">
  export async function load({ fetch }) {
    const res = await fetch(
      `https://api.themoviedb.org/3/discover/movie?api_key=${import.meta.env.VITE_API}&language=en-US&sort_by=popularity.desc&include_adult=false&include_video=false&page=1&with_watch_monetization_types=flatrate`
    );
    const movies = await res.json();
    if (res.ok) {
      return {
        props: { movies: movies.results },
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
import Discover from "$lib/Discover.svelte";
import Search from "$lib/Search.svelte";
import { fly } from 'svelte/transition';
  export let movies
</script>
<svelte:head>
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
</svelte:head>
<section in:fly={{ y:50, duration:500,delay:500 }} out:fly={{ duration:500 }} >
    <Search />
    <Discover {movies} />
</section>
  
    
