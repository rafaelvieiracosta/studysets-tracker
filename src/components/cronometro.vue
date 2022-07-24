<template>
  <section id="cronometro">
    <strong class="display">{{ tempoDecorrido }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "CronometroBar",
  props: {
    tempoEmSegundos: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    tempoDecorrido(): string {
      return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11, 8);
    },
  },
});
</script>

<style>
.botoesInput strong {
  display: block;
  font-family: "Poppins";
  font-style: normal;
  font-weight: 300;
  font-size: 16px;
  padding: 12.5px 20px;
  margin-right: 25px;
  min-width: 106px;
  color: var(--textTimer);
  background: var(--bgTimer);
  border-radius: 4px;
}
.lista_div strong{
  font-family: "Poppins";
  font-style: normal;
  font-weight: 300;
  font-size: 16px;
  color: var(--textBox);
}
@media (max-width: 510px) {
  .botoesInput #cronometro {
    width: 100%;
  }
}
</style>
