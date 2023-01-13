<script>
import { computed, defineComponent } from "vue";
import { useBreakpoint } from "../functions/useBreakpoint";

import TgLogo from "../assets/svg/telegram-logo(1).svg";
import EthLogo from "../assets/svg/etherscan-logo(1).svg"
import UniswapLogo from "../assets/svg/uniswap-logo(1).svg";
import TwLogo from "../assets/svg/twitter-logo(1).svg";
import DexToolsLogo from "../assets/svg/dextools-logo(1).svg"

export default defineComponent({
  name: "SocialSection",
  components: { TgLogo, EthLogo, UniswapLogo, TwLogo, DexToolsLogo },
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
  <section class="social-section lg:h-screen flex items-center justify-center">
    <div
      class="
        socials-content
        w-full
        lg:w-[75%]
        h-full
        flex flex-col
        items-center
      "
    >
      <div class="stonk-claim flex items-center justify-center mb-[10%]">
        <p class="stonk-w-us">Stonk with us!</p>
      </div>
      <ul class="social-list-wrapper w-full">
        <li class="social-list-item cursor-pointer">
          <TgLogo />
        </li>
        <li class="social-list-item cursor-pointer">
          <EthLogo />
        </li>
        <li class="social-list-item cursor-pointer">
          <UniswapLogo />
        </li>
        <li class="social-list-item cursor-pointer">
          <TwLogo />
        </li>
        <li class="social-list-item cursor-pointer">
          <DexToolsLogo/>
        </li>
      </ul>
    </div>
  </section>
</template>

<style scoped lang="scss">
.social-section {
  background-color: transparent;
  padding-top: rem(220);
  transform: translateY(55%);
  min-height: 100vh;

  @media (min-width: 1024px) {
    min-height: auto;
    transform: none;
  }
}

.stonk-claim {
  height: rem(110);
  width: rem(320);
  background-color: $c-white;
  border: 10px solid #0c0b56;
  box-shadow: 12px 15px 4px #000000;

  @media (min-width: 1024px) {
    height: rem(140);
    width: rem(440);
  }

  p {
    font-size: rem(40);

    @media (min-width: 1024px) {
      font-size: rem(64);
    }
  }
}

.social-list-wrapper {
  background-color: transparent;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(2, 1fr);
  row-gap: rem(16);

  @media (min-width: 1024px) {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  @media (min-width: 1600px) {
    width: 150%;
    outline: auto;
  }
}

.social-list-item {
  border: 10px solid #0c0b56;
  box-shadow: 12px 15px 4px #000000;
  background-color: $c-white;
  height: rem(75);
  width: rem(75);
  display: flex;
  align-items: center;
  justify-content: center;

  @media (min-width: 1024px) {
    height: rem(150);
    width: rem(150);
  }

  & svg {
    height: 50%;
  }

  :hover {
    svg {
      transform: scale(1.1);
    }
  }
}
</style>