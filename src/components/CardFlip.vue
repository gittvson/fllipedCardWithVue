<template>
  <div class="card">
    <div class="card__inner" :class="{ is_flipped: isFlipped }" @click="onToggle">
      <div class="card__face card__face--front">
        <div class="card__content">Front</div>
      </div>
      <div class="card__face card__face--back">
        <div class="card__content">Back</div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      isFlipped: false,
    };
  },
  methods: {
    onToggle() {
      this.isFlipped = !this.isFlipped;
    },
  },
};
</script>
<style lang="css" scoped>
.card {
  display: inline-block;
  margin-right: 1rem;
  margin-bottom: 1rem;
  width: 90px;
  height: 120px;
}
.card__inner {
  height: 100%;
  width: 100%;
  transition: transform 1s;
  transform-style: preserve-3d;
  cursor: pointer;
  position: relative;
}
.card__inner.is_flipped {
  transform: rotateY(-180deg);
}

.card__face {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  overflow: hidden;
  border-radius: 1rem;
  padding: 1rem;
  box-shadow: 0 3px 10px 3px rgba(0, 0, 0, 0.2);
}

.card__face--back {
  background-color: var(--dark);
  transform: rotateY(-180deg);
}
</style>
