<script>
import { computed, defineComponent, ref } from "vue";
import { useBreakpoint } from "../functions/useBreakpoint";

import GreenArrow from "../assets/svg/green-arrow.svg";

export default defineComponent({
  name: "TokenSection",
  components: { GreenArrow },
  setup() {
    const tokenContract = ref("0x4159862bcf6b4393a80550b1ed03dffa6f90533c");

    const matches = useBreakpoint();
    const isMobile = computed(() => matches.value?.beforeLg);
    return {
      isMobile,
      tokenContract,
    };
  },
});
</script>

<template>
  <section class="stonk-hero h-fit lg:h-screen w-full mb-8 lg:mb-12">
    <div class="token-infos-wrapper h-full w-full">
      <div
        class="
          infos-header
          h-full
          w-full
          flex flex-col
          lg:flex-row
          items-center
        "
      >
        <div
          class="
            token-wrapper
            h-full
            w-full
            lg:w-[25%]
            mr-[5%]
            flex
            items-center
            justify-center
          "
        >
          <p>Token</p>
        </div>
        <div
          class="
            contract-wrapper
            lg:h-full
            w-full
            lg:w-[70%]
            flex
            items-center
            justify-center
          "
        >
          <p class="cursor-pointer">
            Contract: <span class="contract-label">{{ tokenContract }}</span>
          </p>
        </div>
      </div>
      <div class="tokens-stats h-full w-full">
        <ul class="stats-wrapper w-full h-full">
          <li class="stat-li w-full h-full">
            <div
              class="stat-title w-full h-[20%] flex items-center justify-center"
            >
              <p>Supply</p>
            </div>
            <div
              class="
                stat-number
                w-full
                h-[70%]
                flex
                items-center
                justify-center
              "
            >
              <p>1_000_000_0</p>
            </div>
          </li>
          <li class="stat-li w-full h-full">
            <div
              class="stat-title w-full h-[20%] flex items-center justify-center"
            >
              <p>Taxes</p>
            </div>
            <div
              class="
                stat-number
                w-full
                h-[70%]
                flex
                items-center
                justify-center
              "
            >
              <p>3/3</p>
            </div>
          </li>
          <li class="stat-li w-full h-full">
            <div
              class="stat-title w-full h-[20%] flex items-center justify-center"
            >
              <p>Team Tokens</p>
            </div>
            <div
              class="
                stat-number
                w-full
                h-[70%]
                flex
                items-center
                justify-center
              "
            >
              <p>5%</p>
            </div>
          </li>
          <li class="stat-li w-full h-full">
            <div
              class="stat-title w-full h-[20%] flex items-center justify-center"
            >
              <p>Infos</p>
            </div>
            <div
              class="
                stat-number
                w-full
                h-[70%]
                flex flex-col
                items-center
                justify-center
              "
            >
              <p>Locked</p>
              <p>Renounced</p>
            </div>
          </li>
        </ul>
      </div>
    </div>
    <div
      v-if="!isMobile"
      class="stonk-o-meter flex flex-col items-center justify-end"
    >
      <GreenArrow class="green-arrow" />
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

.token-infos-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;

  @media (min-width: 1024px) {
    display: grid;
    grid-template-rows: 26% 65%;
    row-gap: 10%;
  }
}

.token-wrapper {
  height: rem(86);
  margin-bottom: rem(32);
  p {
    font-size: rem(64);
  }
  @media (min-width: 1024px) {
    height: 100%;
    margin-bottom: none;
  }
}
.contract-wrapper {
  height: rem(86);
  margin-bottom: rem(32);
  p {
    font-size: rem(13);

    @media (min-width: 1024px) {
      font-size: rem(24);
    }
  }

  @media (min-width: 1024px) {
    height: 100%;
    margin-bottom: none;
  }
}

.stat-title {
  height: rem(60);
  width: 75%;
  margin-bottom: rem(32);

  @media (min-width: 1024px) {
    height: 20%;
    width: 100%;
    margin-bottom: none;
  }
}
.stat-number {
  margin-bottom: rem(32);
  height: rem(122);

  @media (min-width: 1024px) {
    margin-bottom: none;
    height: 100%;
  }
}

.infos-header {
  & div {
    background-color: white;
    border: 10px solid #0c0b56;
    box-shadow: 12px 15px 0px #000000;
  }
}

.stats-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;

  @media (min-width: 1024px) {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    column-gap: rem(20);
  }

  & .stat-li {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;

    & div {
      border: 10px solid #0c0b56;
      box-shadow: 12px 15px 4px #000000;
      background-color: $c-white;
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

.contract-label {
  &:hover {
    color: $c-purple;
  }
}

.green-arrow {
  height: 80%;
}
</style>