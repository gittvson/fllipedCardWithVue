<template>
  <div class="card">
    <div
      class="card__inner"
      :class="{ is_flipped: isFlipped, is_disable : isDisable}"
      @click="onToggle"
    >
      <div class="card__face card__face--front">
        <div class="card__content">Front</div>
      </div>
      <div class="card__face card__face--back">
        <div
          class="card__content"
          :style="{
            backgroundImage: `url(${require('@/assets/' + backImgUrl)})`,
          }"
        ></div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    backImgUrl: {
      type: String,
      require: true,
    },
    card:{
      type: [String, Number, Array, Object],
      require: true,
    },
  },
  data() {
    return {
      isFlipped: false,
      isDisable : false,
    };
  },
  methods: {
    onToggle() {
      if(this.isDisable != true){
        this.isFlipped = !this.isFlipped;
        if(this.isFlipped) this.$emit('onFlip', this.card );
      }
    },
    onFlip(){
      this.isFlipped = false;
    },
    changeModeToDisable(){
      this.isDisable = true;
    }
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
  background-color: white;
  transform: rotateY(-180deg);
}

.card__face--front .card__content {
  background: url("../assets/images/icon_back.png") no-repeat center center;
  background-size: 40px;
  width: 100%;
  height: 100%;
}

.card__face--back .card__content {
  background-size: contain;
  background-position: center center;
  background-repeat: no-repeat;
  height: 100%;
  width: 100%;
}
.is_disable{
  cursor: default;
}
</style>
