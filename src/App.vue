<script>
import { computed, defineComponent, onMounted, ref } from "vue";
import LoadingScreen from "./components/LoadingScreen.vue";

import NavBar from "./molecules/NavBar.vue";
import StonkHero from "./components/StonkHero.vue";
import ProjectSection from "./components/ProjectSection.vue";
import TokenSection from "./components/TokenSection.vue";
import SocialSection from "./components/SocialSection.vue";

import { useBreakpoint } from "./functions/useBreakpoint";

export default defineComponent({
  name: "App",
  components: {
    LoadingScreen,
    StonkHero,
    NavBar,
    ProjectSection,
    TokenSection,
    SocialSection,
  },
  setup() {
    const isLoading = ref(true);

    const matches = useBreakpoint();
    const isMobile = computed(() => matches.value?.beforeLg);

    onMounted(() => {
      setTimeout(() => {
        isLoading.value = false;
      }, 2300);
    });
    return {
      isLoading,
      isMobile,
    };
  },
});
</script>

<template>
  <div class="main-wrapper w-full relative px-4 lg:px-16">
    <NavBar v-if="!isLoading" />
    <LoadingScreen v-if="isLoading" />
    <StonkHero v-if="!isLoading" />
    <ProjectSection v-if="!isLoading" />
    <TokenSection v-if="!isLoading" />
    <SocialSection v-if="!isLoading" />
    <footer
      v-if="!isMobile"
      class="
        footer
        w-full
        absolute
        bottom-0
        left-0
        flex
        items-center
        justify-center
      "
    >
      <h2>Copyright 2023 | Stonks Inu | All Rights Reserved</h2>
    </footer>
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

.footer {
  height: rem(36);
  background-color: $c-white;
}
</style>
