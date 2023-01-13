<script>
import { defineComponent, onMounted, ref } from "vue";
import LoadingScreen from "./components/LoadingScreen.vue";

import NavBar from "./molecules/NavBar.vue";
import StonkHero from "./components/StonkHero.vue";
import ProjectSection from "./components/ProjectSection.vue";

export default defineComponent({
  name: "App",
  components: { LoadingScreen, StonkHero, NavBar, ProjectSection },
  setup() {
    const isLoading = ref(false);

    onMounted(() => {
      setTimeout(() => {
        isLoading.value = false;
      }, 2300);
    });
    return {
      isLoading,
    };
  },
});
</script>

<template>
  <div class="main-wrapper w-full relative px-8 lg:px-16">
    <NavBar v-if="!isLoading" />
    <LoadingScreen v-if="isLoading" />
    <StonkHero v-if="!isLoading" />
    <ProjectSection v-if="!isLoading" />
  </div>
</template>

<style scoped lang="scss">
.main-wrapper {
  max-width: rem(1680);
  background-color: $c-blue;

  @media (min-width: 1680px) {
    width: rem(1680) !important;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}
</style>
