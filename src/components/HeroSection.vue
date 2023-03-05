<script>
import { defineComponent, computed } from "vue";
import {useBreakpoint} from "../functions/useBreakpoint"
export default defineComponent({
  name: "HeroSection",
  setup(){
    const matches = useBreakpoint()
    const isMobile = computed(() => matches.value?.beforeLg)

    return {
      isMobile
    }
  }
});
</script>

<template>
  <section class="hero-section h-screen w-full relative">
  </section>
</template>

<style scoped lang="scss">
</style>