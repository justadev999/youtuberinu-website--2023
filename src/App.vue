<script>
import { computed, defineComponent, onMounted, ref } from "vue";
import { useBreakpoint } from "./functions/useBreakpoint";

import HeroSection from "./components/HeroSection.vue";

export default defineComponent({
  name: "App",
  components: {HeroSection},
  setup() {
    const matches = useBreakpoint();
    const isMobile = computed(() => matches.value?.beforeLg);
    return {
      isMobile
    };
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
  background-color: #D6CEB9;
}
</style>
