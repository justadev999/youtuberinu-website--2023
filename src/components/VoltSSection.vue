<script>
import { defineComponent } from "vue";
export default defineComponent({
  name: "VoltSection",
});
</script>

<template>
  <section class="volt-section h-screen flex flex-col items-center justify-center">
    <div class="swap-label w-full flex items-center justify-center mb-4">
        <h2>Swap $STONK on Volt ⚡️</h2>
    </div>
    <iframe
      src="https://voltichange.net/api/widget/?chain=1&
darktheme=false&
tokenin=Native&
tokenout=0x5a101a127d5b0ff8d67ba0917e775c4b27c230ff&
slippage=0.5"
      frameborder="0"
      class="voltichange-widget"
    >
    </iframe>
  </section>
</template>

<style scoped lang="scss">
.swap-label{
    font-size: rem(24);
    color: $c-white;

    @media(min-width:1024px){
        font-size: rem(64);
    }
}
</style>