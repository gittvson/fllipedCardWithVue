<template>
  <interact-screen v-if="statusScreen === 'match'"></interact-screen>
  <main-screen
    @onStart="handleOnStart($event)"
    v-if="statusScreen === 'default'"
  ></main-screen>
</template>

<script>
import MainScreen from "./components/MainScreen.vue";
import InteractScreen from "./components/InteractScreen.vue";
// import ResultScreen from './components/ResultScreen.vue'
// import CoppyRightScreen from './components/CoppyRightScreen.vue'

export default {
  name: "App",
  data() {
    return {
      statusScreen: "default",
    };
  },
  components: {
    MainScreen,
    InteractScreen,
  },
  methods: {
    handleOnStart(config) {
      console.log(config);
      this.statusScreen = "match";
    },
  },
};
</script>
