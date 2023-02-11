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
  max-width: rem(1680);
  color: black;

  @media (min-width: 1680px) {
    width: rem(1680) !important;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}
</style>
