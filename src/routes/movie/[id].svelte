<script context="module">
  export async function load({ fetch, params }) {
    const res = await fetch(
      `https://api.themoviedb.org/3/movie/${params.id}?api_key=${import.meta.env.VITE_API}&language=en-US&page=1`
    );
    const movieDetails = await res.json();
    if (res.ok) {
      return {
        props: { movieDetails },
      };
    }
    return {
      status: res.status,
      error: new Error("Could NOT FETCH movie DATA!!!"),
    };
  }
</script>

<script>
  import.meta.env.VITE_API
  export let movieDetails;
</script>

<div class="wrapper">
  <div class="header">
    <a href="/"><h1>Movie Details</h1></a>
  </div>
  <div class="holder">
    <div class="image-container">
      <img
        src={`https://image.tmdb.org/t/p/original` + movieDetails.backdrop_path}
        alt={movieDetails.title}
      />
    </div>
  </div>
  <div class="text">
    <h1>{movieDetails.title}</h1>
    <p>{movieDetails.overview}</p>
    <p><span>Release date:</span> {movieDetails.release_date}</p>
    <p><span>Rating:</span> {movieDetails.vote_average}</p>
    <p><span>Runtime:</span> {movieDetails.runtime} minutes</p>
  </div>
</div>

<style>
  .header {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  h1 {
    padding: 1rem 0rem 2rem;
  }
  p {
    padding: 1rem 0rem;
  }
  .holder {
    padding: 0 5%;
  }
  .image-container {
    width: 100%;
  }
  img {
    width: 100%;
    border-radius: 0.7rem;
  }
  a {
    text-decoration: none;
    color: inherit;
  }
  .text {
    margin: 2rem 20%;
  }
  span {
    font-weight: bold;
  }
</style>
