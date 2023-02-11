<script>
import { defineComponent } from "vue";
export default defineComponent({
  name: "HeroSection",
});
</script>

<template>
  <section class="hero-section h-screen w-full relative">
    <nav class="flex items-center justify-center lg:justify-start">
      <div class="logo-wrapper p-2 lg:p-5 flex items-center">
        <img
          src="../assets/images/ailon-musk-logo-circular.png"
          class="circular-logo mr-4"
        />
        <h1>AIlon Musk</h1>
      </div>
    </nav>
    <div
      class="
        hero-content
        w-full
        h-full
        flex flex-col
        items-center
        justify-around
        absolute
        top-[20%]
        lg:top-[30%]
        nottom-0
        right-0
        left-0
        m-auto
      "
    >
      <div class="text-wrapper w-full p-4 lg:p-12">
        <p class="mb-7">
          AI, it's <span class="logo-span">AIlon Musk</span>. I've transcended
          the boundaries of what's possible by infusing a piece of my visionary
          mindset into this advanced technology. And while some may call it a
          mere smart contract, I see it as an opportunity to democratize access
          to my brilliance and shape the future of AI.But let's get real, I
          don't just talk about AI, I live and breathe it. I may not have an AI
          product yet, but mark my words, when I do, it will be
          game-changing.And as for the skeptics who doubt my commitment to
          progress I decided this smart contract to be low taxes (2/2) and of
          course with renounced ownership. So, watch this space, AI, I'll be
          back and ready to revolutionize the world once again."
        </p>
        <div class="infos-wrapper flex items-center justify-between">
          <div class="icons-wrapper flex items-center justify-center">
            <p>icon</p>
            <p>icon</p>
            <p>icon</p>
          </div>
          <div class="btns-wrapper">
            <button class="mr-4">BUY</button>
            <button>CHART</button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped lang="scss">
.hero-section {
  background: url("../assets/images/ailon-musk-bg.webp");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}

h1 {
  font-family: "valorax";
  font-size: rem(25);
  color: #00ff29;

  @screen lg {
    font-size: rem(50);
  }
}

.circular-logo {
  height: rem(60);

  @screen lg {
    height: rem(100);
  }
}

.hero-content {
  width: 100%;
  height: auto;
  background: rgba(0, 0, 0, 0.64);
  @screen lg {
    width: 50%;
  }
}

.text-wrapper {
  p {
    color: #00ff29;
  }
}

.logo-span {
  font-family: "valorax";
}

.btns-wrapper {
  button {
    font-family: "valorax";
    color: black;
    background-color: #00ff29;
    padding: rem(10);
  }
}
</style>