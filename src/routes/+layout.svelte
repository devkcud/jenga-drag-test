<script lang="ts">
  import { page } from '$app/stores';
  import '../app.css';

  const path = $page.url.pathname.slice(1).replace(/(\w)(\w+)/, (_, a, b) => a.toUpperCase() + b);
</script>

<svelte:head>
  <title>Jenga | {path}</title>
</svelte:head>

<main>
  <slot />
</main>
