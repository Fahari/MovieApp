<script>
  let inputValue = '';
  import { goto } from "$app/navigation";
  import { fly } from 'svelte/transition';

  function submitSearch() {
    goto( '/search/' + inputValue);
  }
</script>

<form on:submit|preventDefault  ={submitSearch} class="searchBox">
  <input
    bind:value={inputValue}
    class="searchInput"
    type="text"
    name="Search Movie"
    placeholder="Search"
  />
  <button class="searchButton" href="#">
    <i class="material-icons"> search </i>
  </button>
</form>

<style>
  .searchBox {
    display: flex;
    justify-content: start;
    width: fit-content;
    background: #2f3640;
    height: 40px;
    border-radius: 40px;
    margin-top: 2em;
    padding: 10px;
  }

  .searchBox:hover > .searchInput {
    width: 240px;
    padding: 0 6px;
  }

  .searchBox:hover > .searchButton {
    background: white;
    color: #2f3640;
  }

  .searchButton {
    color: white;
    float: right;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: #2f3640;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: 0.4s;
  }

  .searchInput {
    border: none;
    background: none;
    outline: none;
    float: left;
    padding: 0;
    color: white;
    font-size: 16px;
    transition: 0.4s;
    line-height: 40px;
    width: 0px;
  }

  @media screen and (max-width: 620px) {
    .searchBox:hover > .searchInput {
      width: 285px;
      padding: 0 6px;
    }
  }
</style>
