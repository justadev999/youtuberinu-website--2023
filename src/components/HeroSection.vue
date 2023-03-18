<script>
import { defineComponent, computed } from "vue";
import {useBreakpoint} from "../functions/useBreakpoint"

import Dex from "../assets/svg/dex-icon.svg"
import Eth from "../assets/svg/scan-icon.svg"
import Tw from "../assets/svg/tw-icon.svg"
import Uni from "../assets/svg/uni-icon.svg"
import Tg from "../assets/svg/tg-icon.svg"

export default defineComponent({
  name: "HeroSection",
  components: {Dex, Eth, Tw, Uni, Tg},
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
    <nav class="w-full flex items-center justify-between px-3 pt-4 mb-4">
      <div class="logo-wrapper flex items-center">
        <img src="../assets/images/Youtube_logo.png" class="yt-logo mr-4" />
        <div class="logo-text">YouTuber Inu</div>
      </div>
      <img src="../assets/images/ytinu-logo.png" />
    </nav>
    <div class="main-container  px-3">
      <ul class="icons-wrapper flex flex-col items-start">
        <li>
          <button class="flex items-center">
            <Dex class="icon" />
            <p class="icon-text" v-if="!isMobile">DexTools</p>
          </button>
        </li>
        <li>
          <button class="flex items-center">
            <Uni class="icon" />
            <p class="icon-text" v-if="!isMobile">Uniswap</p>
          </button>
        </li>
        <li>
          <button class="flex items-center">
            <Eth class="icon" />
            <p class="icon-text" v-if="!isMobile">Etherscan</p>
          </button>
        </li>
        <li>
          <button class="flex items-center">
            <Tw class="icon" />
            <p class="icon-text" v-if="!isMobile">Twitter</p>
          </button>
        </li>
        <li>
          <button class="flex items-center">
            <Tg class="icon" />
            <p class="icon-text" v-if="!isMobile">Telegram</p>
          </button>
        </li>
      </ul>
      <div class="videos-wrapper">
        <img class="video-card mb-4 lg:mb-0" src="../assets/images/card-1.png" />
        <img class="video-card mb-4 lg:mb-0" src="../assets/images/card-4.png" />
        <img class="video-card mb-4 lg:mb-0" src="../assets/images/card-2.png" />
        <img class="video-card mb-4 lg:mb-0" src="../assets/images/card-5.png" />
        <img class="video-card mb-4 lg:mb-0" src="../assets/images/card-3.png" />
        <img class="video-card" src="../assets/images/card-6.png" />
      </div>
    </div>
  </section>
</template>

<style scoped lang="scss">
.yt-logo{
  height: rem(27);

  @screen lg {
    height: rem(37);
  }
}

.logo-text{
  font-family: "bold";
  font-size: rem(25);
  color: white;

  @screen lg {
   font-size: rem(30); 
  }
}

.main-container{
  /* height: calc(100% - 66px); */
  display: grid;
  grid-template-columns: 12.5% 87.5%;
}

.icon{
  height: rem(25);
  margin-bottom: rem(10);

  @screen lg {
    height: rem(35);
    margin-right:rem(10);
  }
}

.icon-text{
  font-size: rem(24);
  font-family: "light";
  color: white;
}

.videos-wrapper{
  display: flex;
  flex-direction: column;
  align-items: center;

  @media(min-width:1080px){
    align-items: start;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    column-gap: rem(12);
    row-gap: rem(12);
  }
}

.video-card {
  height: rem(155);
  width: rem(295);
}
</style>