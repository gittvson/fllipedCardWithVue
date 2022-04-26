<template>
  <card-flip
    v-for="(card, index) in cardsContext"
    :backImgUrl="`images/${card}.png`"
    :key="index"
    :card="card"
    @onFlip="checkRule($event)"
  ></card-flip>
</template>

<script>
import CardFlip from "./CardFlip.vue";
export default {
  props: {
    cardsContext: {
      type: Array,
      default: function () {
        return [];
      },
    },
  },
  components: {
    CardFlip,
  },
  data() {
    return {
      rules:[],

    };
  },
  methods:{
    checkRule(card){
      console.log(card);
    }
  }
};
</script>
