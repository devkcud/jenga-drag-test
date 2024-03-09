<script lang="ts">
  let width: number = 500;
  let height: number = 300;
  $: dimension = `${width || 500}x${height || 300}` as string;
</script>

<section>
  <div class="space-x-8">
    <input
      bind:value={width}
      type="number"
      placeholder="500"
      class="input input-bordered input-md"
    />
    <span>x</span>
    <input
      bind:value={height}
      type="number"
      placeholder="300"
      class="input input-bordered input-md"
    />
  </div>

  <a href={`/blueprint/${dimension}`} class="btn">Create new area {dimension}</a>
</section>
