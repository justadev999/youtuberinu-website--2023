<script>
import { computed, defineComponent, onMounted } from "vue";
import { useBreakpoint } from "../functions/useBreakpoint";
import RedArrow from "../assets/svg/red-arrow.svg";

import gsap from "gsap";

export default defineComponent({
  name: "StonkHero",
  components: { RedArrow },
  setup() {
    const matches = useBreakpoint();
    const isMobile = computed(() => matches.value?.beforeLg);

    onMounted(() => {
      gsap.set(".stonk-label, .stonk-label span", { autoAlpha: 0, y: 20 });
      const tl = gsap.timeline();

      tl.fromTo(
        ".stonk-label",
        { autoAlpha: 0, y: 20 },
        { autoAlpha: 1, y: 0, duration: 0.6, animation: "power3.in" }
      );
      tl.fromTo(
        ".stonk-label span",
        { autoAlpha: 0, y: 20, scale: 1 },
        {
          autoAlpha: 1,
          y: -70,
          duration: 0.4,
          animation: "power3.in",
        }
      );
      tl.fromTo(
        ".text-side p",
        { autoAlpha: 0, y: 20 },
        {
          autoAlpha: 1,
          y: 0,
          duration: 0.4,
          animation: "power3.in",
        },
        "<"
      );
      tl.fromTo(
        ".stonk-body-image",
        { autoAlpha: 0, scale: 0.5 },
        {
          autoAlpha: 1,
          scale: 1,
          duration: 0.4,
          animation: "power3.in",
        },
        "<"
      );
      tl.fromTo(
        ".red-arrow",
        { autoAlpha: 0, y: 50 },
        {
          autoAlpha: 1,
          y: 0,
          duration: 0.4,
          animation: "power3.in",
        },
        "<"
      );
    });
    return {
      isMobile,
    };
  },
});
</script>

<template>
  <section id="home" class="stonk-hero w-full mb-12 lg:mb-24">
    <div class="description-wrapper h-full">
      <div
        class="
          text-side
          w-full
          h-full
          flex flex-col
          items-start
          justify-center
          px-2
          lg:px-4
        "
      >
        <h2 class="stonk-label">One goal: <span>STONK!</span></h2>
        <p>
          Chad felt a deep sense of hopelessness as he struggled to come to
          terms with his losses and mistakes. But in his darkest hour, he let
          out a cry of determination. "I know! I'll create a crypto stonk!" he
          yelled out to the empty room, a glimmer of hope in his eyes.
        </p>
      </div>
      <div class="image-side w-full h-full relative">
        <img
          src="../assets/images/stonk-body-_1_.webp"
          class="stonk-body-image absolute bottom-0 right-0"
        />
      </div>
    </div>
    <div
      v-if="!isMobile"
      class="stonk-o-meter flex flex-col items-center justify-end"
    >
      <RedArrow class="red-arrow" />
      <div class="w-full flex items-center justify-center">
        <p class="uppercase">Stonk-o-meter</p>
      </div>
    </div>
  </section>
</template>

<style scoped lang="scss">
.stonk-hero {
  background-color: $c-blue;
  padding-top: rem(140);
  height: calc(100vh - 140px);

  @media (min-width: 1024px) {
    padding-top: rem(180);
    height: calc(118vh - 180px);
    display: grid;
    grid-template-columns: 75% 20%;
    column-gap: rem(68);
    max-height: rem(900);
  }
}

.description-wrapper {
  background-color: $c-white;
  border: 10px solid #0c0b56;
  box-shadow: 12px 15px 4px #000000;
  display: flex;
  flex-direction: column;
  align-items: center;

  @media (min-width: 1024px) {
    display: grid;
    grid-template-columns: repeat(2, 50%);
  }
}

.text-side {
  h2 {
    font-size: rem(36);

    @media (min-width: 1024px) {
      font-size: rem(64);
    }
  }
  p {
    font-size: rem(14);

    @media (min-width: 1024px) {
      font-size: rem(22);
    }
  }
}

.image-side {
  .stonk-body-image {
    max-height: 100%;
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

.red-arrow {
  height: rem(114);
}
</style>