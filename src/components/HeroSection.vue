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
    <nav class="w-full p-4">
      <div class="logo-wrapper flex items-center">
        <img src="../assets/images/oBC-logo.png" class="logo mr-4" />
        <h1 class="text-logo">Ordinal Old Bitcoin</h1>
      </div>
    </nav>
    <div class="desktop w-full">
    </div>
  </section>
</template>

<style scoped lang="scss">

nav {
  box-shadow: 1px 1px 1px rgba(0,0,0,0.5);
  background-color: #D6CEB9;
}

.logo{
  height: rem(50);

  @screen lg {
    height: rem(80);
  }
}

.desktop{
  height: calc(100% - 82px);

  @screen lg {
    height: calc(100% - 112px);
  }
}

.text-logo{
  font-family: "bold";
}
</style>