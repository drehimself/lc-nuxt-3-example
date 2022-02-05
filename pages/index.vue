<template>
<div>
  <div>This is the main page</div>
  <Counter />
  <div>
    x: {{ x }}
    y: {{ y }}
  </div>
</div>
</template>

<script setup>
  const {x, y} = useMouse()
</script>
