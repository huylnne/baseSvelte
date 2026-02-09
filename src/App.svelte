<script>
  import Header from './components/Header.svelte';
  import ViewerContainer from './components/ViewerContainer.svelte';
</script>

<main class="page">
  <Header />
  <ViewerContainer />
</main>

<style>
  .page {
    max-width: 1100px;
    margin: 40px auto;
    padding: 0 16px;
    font-family: system-ui;
  }
</style>
