<script>
import { computed, defineComponent } from "vue";
import { useBreakpoint } from "../functions/useBreakpoint";

import YellowArrow from "../assets/svg/yellow-arrow.svg";
import ChartImage from "../assets/svg/chart-img(1).svg";

import gsap from "gsap";

export default defineComponent({
  name: "ProjectSection",
  components: { YellowArrow, ChartImage },
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
  <section id="project" class="project-section w-full mb-12 lg:mb-24">
    <div class="description-wrapper h-full">
      <div class="chart-side w-full h-full mb-8 lg:mb-0">
        <!-- <div class="chart-title p-4">
          <h2>Stonking the market</h2>
        </div> -->
        <div class="chart h-full">
          <!-- <ChartImage class="w-full h-full" /> -->
          <iframe
              src="https://dexscreener.com/ethereum/0x9C69D0ABf43dA8cf0E64AC8be56B1FceA81Dc6fC?embed=1&theme=dark&info=0"
            ></iframe>
          
        </div>
      </div>
      <div class="images-side w-full h-full flex items-end justify-end">
        <div
          class="
            images-wrapper
            w-full
            lg:w-[80%]
            h-full
            flex flex-col
            items-center
            justify-between
          "
        >
          <div class="stonk-img relative overflow-hidden">
            <img
              class="w-full h-full absolute top-0 left-0 object-cover"
              src="../assets/images/stonk-img.jpg"
            />
          </div>
          <div class="stonk-img relative overflow-hidden">
            <img
              class="w-full h-full absolute top-0 left-0 object-cover"
              src="../assets/images/confused-stonk.jpg"
            />
          </div>
          <div class="stonk-img relative overflow-hidden">
            <img
              class="w-full h-full absolute top-0 left-0 object-cover"
              src="../assets/images/not-stonk.jpg"
            />
          </div>
        </div>
      </div>
    </div>
    <div
      v-if="!isMobile"
      class="stonk-o-meter flex flex-col items-center justify-end"
    >
      <YellowArrow class="yellow-arrow" />
      <div class="w-full flex items-center justify-center">
        <p class="uppercase">Stonk-o-meter</p>
      </div>
    </div>
  </section>
</template>

<style scoped lang="scss">
.chart {
  outline: auto;
  min-height: 500px;
}
.project-section {
  background-color: transparent;
  @media (min-width: 1024px) {
    display: grid;
    grid-template-columns: 75% 20%;
    column-gap: rem(68);
    max-height: rem(900);
  }
}

.description-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;

  @media (min-width: 1024px) {
    display: grid;
    grid-template-columns: repeat(2, 50%);
  }
}

.chart-side {
  outline: auto;
  background-color: $c-white;
  border: 10px solid #0c0b56;
  box-shadow: 12px 15px 0px #000000;
  /* display: grid; */
  /* grid-template-rows: 30% 70%; */
  h2 {
    font-size: rem(24);

    @media (min-width: 1024px) {
      font-size: rem(32);
    }
  }
  p {
    font-size: rem(14);

    @media (min-width: 1024px) {
      font-size: rem(22);
    }
  }
}

.images-wrapper {
  transition: all 0.14 ease-in;
  & .stonk-img {
    height: rem(192);
    width: 100%;
    /* object-fit: cover; */
    background-color: white;
    border: 10px solid #0c0b56;
    filter: drop-shadow(12px 15px 4px #000000);
    margin-bottom: rem(22);
    transition: all 0.14 ease-in;

    @media (min-width: 1024px) {
      height: 30%;
    }

    &:hover {
      img {
        transform: scale(1.1);
      }
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

.yellow-arrow {
  height: rem(275);
}

iframe {
  height: 100%;
  width: 100%;
}
#dexscreener-embed {
  position: relative;
  width: 100%;
}
@media (min-width: 1400px) {
  #dexscreener-embed {
    padding-bottom: 65%;
  }
}
#dexscreener-embed iframe {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  border: 0;
}
</style>