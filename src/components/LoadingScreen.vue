<script>
import { computed, defineComponent, onMounted } from "vue";
import { useBreakpoint } from "../functions/useBreakpoint";
import gsap from "gsap";

export default defineComponent({
  name: "StonkingScreen",
  setup() {
    const matches = useBreakpoint();
    const isMobile = computed(() => matches.value?.beforeLg);

    onMounted(() => {
      gsap.fromTo(
        ".stonk-dot",
        { opacity: 1 },
        { opacity: 0, stagger: 0.2, repeat: -1 }
      );
    });

    return {
      isMobile,
    };
  },
});
</script>

<template>
  <div
    class="
      stonking-screen-wrapper
      h-screen
      w-full
      flex flex-col
      items-center
      justify-center
      fix
    "
  >
    <div class="gif-container h-[40%]">
      <img src="../assets/gif/stonking-gif.gif" />
    </div>
    <p class="stonking-label">
      Stonking <span class="stonk-dot">.</span><span class="stonk-dot">.</span
      ><span class="stonk-dot">.</span>
    </p>
  </div>
</template>

<style scoped lang="scss">
.stonking-screen-wrapper {
  background-color: $c-blue;
}

.gif-container {
  img {
    height: 80%;
  }
}

.stonking-label {
  color: $c-white;
}
</style>