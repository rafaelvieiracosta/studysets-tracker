<template>
  <div class="botoesInput">
    <Cronometro :tempoEmSegundos="tempoEmSegundos" />
    <botaoPrincipal
      @click="iniciar"
      :disabled="cronometroRodando"
      iconeBotao="<svg width='14' height='18' fill='none' xmlns='http://www.w3.org/2000/svg'><path d='m1 1 11.974 7.697L1 16.395V1Z' stroke='#00234C' stroke-width='1.711' stroke-linecap='round' stroke-linejoin='round'/></svg>"
      textoBotao="play"
    />
    <botaoPrincipal
      @click="finalizar"
      :disabled="!cronometroRodando"
      iconeBotao="<svg width='18' height='18' fill='none' xmlns='http://www.w3.org/2000/svg'><path d='M14.684 1H2.711A1.71 1.71 0 0 0 1 2.71v11.974c0 .945.766 1.71 1.71 1.71h11.974a1.71 1.71 0 0 0 1.71-1.71V2.711A1.71 1.71 0 0 0 14.685 1Z' stroke='#00234C' stroke-width='1.711' stroke-linecap='round' stroke-linejoin='round'/></svg>"
      textoBotao="stop"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometro from "./cronometro.vue";
import botaoPrincipal from "./botoes/botaoPrincipal.vue";

export default defineComponent({
  name: "TemporizadorBar",
  emits: ["aoTemporizadorFinalizado"],
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      cronometroRodando: false,
    };
  },
  methods: {
    iniciar() {
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos += 1;
      }, 1000);
      this.cronometroRodando = true;
    },
    finalizar() {
      clearInterval(this.cronometro);
      this.cronometroRodando = false;
      this.$emit("aoTemporizadorFinalizado", this.tempoEmSegundos);
      this.tempoEmSegundos = 0;
    },
  },
  components: {
    Cronometro,
    botaoPrincipal,
  },
});
</script>

<style>
.botoesInput {
  display: flex;
}
@media (max-width: 510px) {
  .botoesInput {
    width: 100%;
  }
}
</style>
