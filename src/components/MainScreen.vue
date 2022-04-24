<template>
  <h1>Welcome</h1>
  <div class="screen">
    <div class="actions">
      <button @click="onStart(16)">
        <span>Easy Mode</span>
        <span>4 x 4</span>
      </button>
    </div>
    <div class="actions">
      <button @click="onStart(36)">
        <span>Normal Mode</span>
        <span>6 x 6</span>
      </button>
    </div>
    <div class="actions">
      <button @click="onStart(64)">
        <span>Hard Mode</span>
        <span>8 x 8</span>
      </button>
    </div>
    <div class="actions">
      <button @click="onStart(100)">
        <span>Super Hard Mode</span>
        <span>10 x 10</span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    onStart(totalOfBlocks) {
      this.$emit("onStart", { totalOfBlocks });
    },
  },
};
</script>
