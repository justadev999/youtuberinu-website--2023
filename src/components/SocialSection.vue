<script>
import { computed, defineComponent } from "vue";
import { useBreakpoint } from "../functions/useBreakpoint";

export default defineComponent({
  name: "SocialSection",
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
  <section
    class="
      stonk-hero
      h-auto
      lg:h-screen
      w-full
      mb-8
      lg:mb-12
      flex
      items-center
      justify-center
    "
  >
    <div class="socials-content w-full lg:w-[75%] h-screen">socials here</div>
  </section>
</template>

<style scoped lang="scss">
.stonk-hero {
  background-color: $c-blue;
  padding-top: rem(180);
  outline: auto;
}

.socials-content {
  outline: auto;
}
</style>