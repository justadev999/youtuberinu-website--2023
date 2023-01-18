<script>
import { computed, defineComponent } from "vue";
import { useBreakpoint } from "../functions/useBreakpoint";

import TgLogo from "../assets/svg/telegram-logo(1).svg";
import EthLogo from "../assets/svg/etherscan-logo(1).svg";
import UniswapLogo from "../assets/svg/uniswap-logo(1).svg";
import TwLogo from "../assets/svg/twitter-logo(1).svg";
import DexToolsLogo from "../assets/svg/dextools-logo(1).svg";

export default defineComponent({
  name: "SocialSection",
  components: { TgLogo, EthLogo, UniswapLogo, TwLogo, DexToolsLogo },
  setup() {
    const matches = useBreakpoint();
    const isMobile = computed(() => matches.value?.beforeLg);

    const navigateTo = (add) => {
      window.open(add, "_blank");
    };
    return {
      isMobile,
      navigateTo,
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
      <ul class="social-list-wrapper w-full mb-24 lg:mb-0">
        <button class="social-list-item cursor-pointer">
          <TgLogo @click="navigateTo('https://t.me/stonkgram')" />
        </button>
        <button class="social-list-item cursor-pointer">
          <EthLogo
            @click="
              navigateTo(
                'https://etherscan.io/token/0x5a101a127d5b0ff8d67ba0917e775c4b27c230ff'
              )
            "
          />
        </button>
        <button class="social-list-item cursor-pointer">
          <UniswapLogo
            @click="
              navigateTo(
                'https://app.uniswap.org/#/swap?outputCurrency=0x5a101a127d5b0ff8d67ba0917e775c4b27c230ff'
              )
            "
          />
        </button>
        <button class="social-list-item cursor-pointer">
          <TwLogo @click="navigateTo('https://twitter.com/stonkerc')" />
        </button>
        <button class="social-list-item cursor-pointer">
          <DexToolsLogo
            @click="
              navigateTo(
                'https://www.dextools.io/app/en/ether/pair-explorer/0x9c69d0abf43da8cf0e64ac8be56b1fcea81dc6fc'
              )
            "
          />
        </button>
      </ul>
      <footer
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
        <h2>Copyright 2023 | Stonk | All Rights Reserved</h2>
      </footer>
    </div>
  </section>
</template>

<style scoped lang="scss">
.social-section {
  background-color: transparent;
  max-height: 100vh;

  @media (min-width: 1024px) {
    max-height: rem(900);
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

.footer {
  height: rem(36);
  background-color: $c-white;
}
</style>