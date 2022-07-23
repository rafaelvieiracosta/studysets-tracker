<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometro :tempoEmSegundos="tempoEmSegundos" />
    <botaoPrincipal
      @click="iniciar"
      :disabled="cronometroRodando"
      iconeBotao="fas fa-play"
      textoBotao="play"
    />
    <botaoPrincipal
      @click="finalizar"
      :disabled="!cronometroRodando"
      iconeBotao="fas fa-stop"
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

<style></style>
