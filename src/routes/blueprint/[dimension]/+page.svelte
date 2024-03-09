<script lang="ts">
  import { page } from '$app/stores';
  import { Layer, Rect, Stage, Text, type KonvaDragTransformEvent } from 'svelte-konva';

  const [width, height] = $page.params.dimension.split('x', 2).map((a) => parseInt(a) || 500);

  let x = 50;
  let y = 50;
  let showText = false;

  function updatePos(e: KonvaDragTransformEvent) {
    const target = e.detail.currentTarget;
    x = target.x();
    y = target.y();
  }
</script>

<div
  class="ring-2 ring-transparent ring-offset-2 ring-offset-primary"
  style={`width: ${width}px; height: ${height}px`}
>
  <Stage config={{ width, height }}>
    <Layer>
      <Rect
        config={{ x: 50, y: 50, width: 100, height: 100, fill: 'red', draggable: true }}
        on:dragmove={updatePos}
        on:mouseenter={() => (showText = true)}
        on:mouseleave={() => (showText = false)}
      />
      <Text
        config={{
          x: x + 100 / 3,
          y: y - 20,
          text: showText ? '100' : '',
          fill: 'white',
          fontSize: 20
        }}
      />
      <Text
        config={{
          x: x + 100 / 3,
          y: y + 100 + 10,
          text: showText ? '100' : '',
          fill: 'white',
          fontSize: 20
        }}
      />
      <Text
        config={{
          x: x + 100 + 20,
          y: y + 100 / 4,
          text: showText ? '100' : '',
          fill: 'white',
          rotation: 90,
          fontSize: 20
        }}
      />
      <Text
        config={{
          x: x - 20,
          y: y + 100 / 2 + 10,
          text: showText ? '100' : '',
          fill: 'white',
          rotation: 270,
          fontSize: 20
        }}
      />
    </Layer>
  </Stage>
</div>
