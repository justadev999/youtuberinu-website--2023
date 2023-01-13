<script>
import { computed, defineComponent } from "vue";
import { useBreakpoint } from "../functions/useBreakpoint";
export default defineComponent({
  name: "StonkNav",
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
  <nav class="w-full fixed top-0 left-0 pt-8 px-8 lg:px-16">
    <div
      v-if="!isMobile"
      class="nav-content w-full flex items-center justify-between pl-7 pr-20"
    >
      <div class="logo-wrapper">
        <h2 class="logo-label">$STONK Inu</h2>
      </div>
      <ul class="nav-items-wrapper flex items-center justify-between w-[60%]">
        <li>
          <a>home</a>
        </li>
        <li>
          <a>project</a>
        </li>
        <li>
          <a>token</a>
        </li>
      </ul>
    </div>
    <button class="buy-btn">
      <p class="buy-label">BUY</p>
    </button>
  </nav>
</template>

<style scoped lang="scss">
nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  max-width: rem(1680);

  @media (min-width: 1024px) {
    display: grid;
    grid-template-columns: 75% 20%;
    column-gap: rem(40);
  }

  @media (min-width: 1024px) {
    left: 0;
    right: 0;
    margin: auto;
  }
}

.nav-content {
  background-color: $c-white;
  border: 10px solid #0c0b56;
  box-shadow: 12px 15px 4px #000000;
  height: rem(112);
}

.logo-label {
  font-size: rem(42);
}

.buy-btn {
  border: 10px solid #0c0b56;
  box-shadow: 12px 15px 4px #000000;
  background-color: $c-white;
  height: rem(80);
  width: rem(110);
  transition: all 0.12s ease-in;

  @media (min-width: 1024px) {
    height: rem(112);
    width: auto;
  }

  p {
    font-size: rem(32);
    @media (min-width: 1024px) {
      font-size: rem(40);
    }
  }

  &:hover {
    box-shadow: 11px 12px 4px #000000;
  }
  &:focus {
    background-color: $c-purple;
    border: none;
    color: $c-white;
    box-shadow: none;
  }
}
</style>