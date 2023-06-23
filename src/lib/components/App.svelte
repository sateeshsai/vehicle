<script lang="ts">
  import { Canvas } from "@threlte/core";
  import Scene from "./Scene.svelte";
  import { Debug, World } from "@threlte/rapier";
</script>

<header>
  <div class="logo">Stockpile</div>
  <nav>
    <a href="/">Home</a>
  </nav>
</header>
<main>
  <div class="hero">
    <div class="hero-titles">
      <p>Search the</p>
      <h1>Stockpile</h1>
    </div>
    <div class="hero-search">
      <input type="text" class="search-input" />
    </div>
  </div>
</main>

<div class="scene">
  <Canvas>
    <World>
      <Debug />
      <Scene />
    </World>
  </Canvas>
</div>

<style>
  :global(input) {
    border: none;
    border-radius: 0.5rem;
  }
  header {
    display: flex;
    justify-content: space-between;
    margin-bottom: 10rem;
    padding: 2rem 3rem;
    color: lightcoral;
  }

  a {
    color: lightcoral;
    text-decoration: none;
  }

  h1 {
    text-align: center;
    font-size: 5rem;
  }

  p {
    text-align: center;
    font-size: 1.5rem;
    font-weight: 500;
  }

  .scene {
    width: 100vw;
    height: 100vh;
    position: absolute;
    top: 0;
    z-index: -1;
  }

  .hero {
    display: grid;
    justify-content: center;
  }

  .hero-search {
    display: grid;
    justify-content: center;
  }

  .search-input {
    padding: 0.5rem 1rem;
    width: 20rem;
    margin-block-start: 2rem;
    font-size: 1.5rem;
  }
</style>
