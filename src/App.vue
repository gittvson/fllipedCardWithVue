<template>
  <interact-screen :cardsContext="setting.cardsContext" v-if="statusScreen === 'match'"></interact-screen>
  <main-screen
    @onStart="handleOnStart($event)"
    v-if="statusScreen === 'default'"
  ></main-screen>
</template>

<script>
import MainScreen from "./components/MainScreen.vue";
import InteractScreen from "./components/InteractScreen.vue";
import { shuffled } from "./utils/array";
export default {
  name: "App",
  data() {
    return {
      statusScreen: "default",
      setting: {
        totalOfBlocks: 0,
        cardsContext: [],
        startAt: null,
      },
    };
  },
  components: {
    MainScreen,
    InteractScreen,
  },
  methods: {
    handleOnStart(config) {
      this.statusScreen = "match";
      this.setting.totalOfBlocks = config.totalOfBlocks;

      const firstCards = Array.from(
        { length: this.setting.totalOfBlocks / 2 },
        (_, i) => i + 1
      );
      const shuffledCards = shuffled([...firstCards, ...firstCards]);
      this.setting.cardsContext = shuffledCards;

      this.setting.startAt = new Date().getTime();
    },
  },
};
</script>
