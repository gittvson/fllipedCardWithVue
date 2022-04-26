<template>
  <card-flip
    v-for="(card, index) in cardsContext"
    :backImgUrl="`images/${card}.png`"
    :key="index"
    :card="{ index, value: card }"
    :ref="`card-${index}`"
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
      rules: [],
    };
  },
  methods: {
    checkRule(card) {
      console.log(this.rules);
      if (this.rules.length >= 2) return false;

      this.rules.push(card);

      if (this.rules.length == 2 && this.rules[0].value == this.rules[1].value) {
        console.log("Right");
        this.rules = [];
      } else if (this.rules.length == 2 && this.rules[0].value != this.rules[1].value) {
        console.log("Wrong");
        setTimeout(()=>{
             this.$refs[`card-${this.rules[0].index}`][0].onFlip();
             this.$refs[`card-${this.rules[1].index}`][0].onFlip();
             this.rules = [];
        },1500);
       
        
      } else {
        return false;
      }
    },
  },
};
</script>