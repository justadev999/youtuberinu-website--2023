<script>
import { computed, defineComponent } from "vue";
import { useBreakpoint } from "../functions/useBreakpoint";

export default defineComponent({
  name: "ProjectSection",
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
    <div class="description-wrapper h-full">
      <div class="chart-side w-full h-full"></div>
      <div class="images-side w-full h-full flex items-end justify-end"></div>
    </div>
    <div v-if="!isMobile" class="stonk-o-meter flex items-end">
      <div class="w-full flex items-center justify-center">
        <p class="uppercase">Stonk-o-meter</p>
      </div>
    </div>
  </section>
</template>

<style scoped lang="scss">
.stonk-hero {
  background-color: transparent;
  padding-top: rem(180);

  @media (min-width: 1024px) {
    display: grid;
    grid-template-columns: 75% 20%;
    column-gap: rem(68);
  }
}

.description-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;

  @media (min-width: 1024px) {
    display: grid;
    grid-template-columns: repeat(2, 50%);
  }
}

.chart-side {
  background-color: $c-white;
  border: 10px solid #0c0b56;
  box-shadow: 12px 15px 0px #000000;
  h2 {
    font-size: rem(36);

    @media (min-width: 1024px) {
      font-size: rem(64);
    }
  }
  p {
    font-size: rem(14);

    @media (min-width: 1024px) {
      font-size: rem(22);
    }
  }
}
.stonk-o-meter {
  background-color: $c-white;
  box-shadow: 12px 15px 4px #000000;
  border: 10px solid #0c0b56;

  & div {
    height: 15%;
    background-color: $c-purple;
    border-top: 10px solid #0c0b56;

    p {
      color: white;
      font-size: rem(26);
    }
  }
}
</style>