<template>
  <section id="forms">
    <div class="forms_div containerGeral">
      <input
        type="text"
        placeholder="Qual tarefa você deseja iniciar?"
        v-model="descricaoTarefa"
      />
      <Temporizador @aoTemporizadorFinalizado="finalizarTarefa" />
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Temporizador from "./temporizador.vue";

export default defineComponent({
  name: "formularioPrincipal",
  emits: ["aoSalverTarefa"],
  data() {
    return {
      descricaoTarefa: null,
    };
  },
  components: {
    Temporizador,
  },
  methods: {
    finalizarTarefa(tempoDecorrido: number): void {
      console.log(tempoDecorrido, this.descricaoTarefa);
      this.$emit("aoSalverTarefa", {
        duracaoEmSegundos: tempoDecorrido,
        descricao: this.descricaoTarefa,
      });
      this.descricaoTarefa = null;
    },
  },
});
</script>

<style>
#forms {
  background: linear-gradient(180deg, #0b0c12 50%, var(--bg) 50%);
  padding: 0 20px;
}
.forms_div {
  display: flex;
  justify-content: space-between;
  gap: 10px;
  padding: 25px;
  background: var(--bgBoxInput);
  border-radius: 4px;
  box-shadow: 0px 0px 32px rgba(0, 0, 0, 0.1);
}
.forms_div input {
  flex-grow: 1;
  padding: 12px;
  font: 400 1rem/1.5 "Roboto", sans serif;
  background: var(--bgInput);
  border: 1px solid var(--lineBorderInput);
  border-radius: 4px;
  outline: none;
  color: var(--textInput);
}
.forms_div input::placeholder {
  color: #B2B8BF;
}
.forms_div input:focus {
  border-color: #18a0fb;
  background: var(--bgInputFocus);
  box-shadow: 0 0 0 2px #a8dcff;
}
@media (max-width: 600px) {
  #forms {
    padding: 0;
  }
  .forms_div {
    border-radius: 0;
    flex-wrap: wrap;
  }
}
</style>
