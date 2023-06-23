<script lang="ts">
  import App from "$lib/components/App.svelte";
</script>

<div>
  <App />
</div>

<style>
  :global(body, h1, p) {
    margin: 0;
  }

  :global(html) {
    font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI",
      Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue",
      sans-serif;
  }
</style>
