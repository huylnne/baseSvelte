<script>
  import { onMount, onDestroy } from 'svelte';

  let viewerEl;

  onMount(() => {
    console.log('Viewer mounted', viewerEl);

    
    // initViewer(viewerEl);

    return () => {
      console.log('Viewer cleanup');
      // destroyViewer();
    };
  });
</script>

<div class="viewer" bind:this={viewerEl}>
  Viewer Container
</div>

<style>
  .viewer {
    margin-top: 24px;
    height: 520px;
    border: 1px solid #ddd;
    border-radius: 12px;
    display: grid;
    place-items: center;
    background: #f7f7f7;
    color: #666;
  }
</style>
