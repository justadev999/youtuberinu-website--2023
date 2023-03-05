<script>
import { defineComponent} from "vue";

import HeroSection from "./components/HeroSection.vue";

export default defineComponent({
  name: "App",
  components: {HeroSection},
  setup() {
    return {};
  },
});
</script>

<template>
  <div class="main-wrapper w-full relative">
    <HeroSection />
  </div>
</template>

<style scoped lang="scss">
.main-wrapper {
  //
}
</style>
