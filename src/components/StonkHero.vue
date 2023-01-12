<script>
import { computed, defineComponent } from "vue";
import { useBreakpoint } from "../functions/useBreakpoint";

export default defineComponent({
  name: "StonkHero",
  setup() {
    const matches = useBreakpoint();
    const isMobile = computed(() => matches.value?.beforeLg);
    return {
      isMobile,
    };
  },
});
</script>

<template>
  <section class="stonk-hero h-screen w-full mb-8 lg:mb-12">
    <div class="description-wrapper h-full">hero</div>
    <div v-if="!isMobile" class="stonk-o-meter"></div>
  </section>
</template>

<style scoped lang="scss">
.stonk-hero {
  background-color: $c-blue;
  padding-top: rem(180);

  @media (min-width: 1024px) {
    display: grid;
    grid-template-columns: 75% 20%;
    column-gap: rem(68);
  }
}

.description-wrapper {
  background-color: $c-white;
  border: 10px solid #0c0b56;
  box-shadow: 12px 15px 4px #000000;
}
.stonk-o-meter {
  background-color: $c-white;
  box-shadow: 12px 15px 4px #000000;
  border: 10px solid #0c0b56;
}
</style>