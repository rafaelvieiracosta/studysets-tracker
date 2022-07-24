<template>
  <main :class="{ 'modo-escuro': modoEscuroAtivo }">
    <BarraLateral @aoTemaAlterado="trocarTema" />
    <Formulario @aoSalverTarefa="salvarTarefa" />
    <transition mode="out-in">
      <div class="lista" v-if="tarefas.length">
        <div class="lista_div containerGeral">
          <Tarefa v-for="(tarefa, i) in tarefas" :key="i" :tarefa="tarefa" />
        </div>
      </div>
      <div class="boxNull" v-else>
        <Box>
          <p>Você não finalizou nenhuma tarefa</p>
        </Box>
      </div>
    </transition>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from "./components/barraLateral.vue";
import Formulario from "./components/formulario.vue";
import Tarefa from "./components/tarefa.vue";
import Box from "./components/box.vue";
import ITarefa from "./interfaces/ITarefas";

export default defineComponent({
  name: "App",
  components: {
    BarraLateral,
    Formulario,
    Tarefa,
    Box,
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false,
    };
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      console.log(tarefa);
      this.tarefas.push(tarefa);
      console.log(this.tarefas);
    },
    trocarTema(modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo;
    },
  },
});
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Roboto", sans-serif;
}
:root {
  --bg: #ffffff;
  --bgHeader: #0b0c12;

  --bgTimer: #363b47;
  --textTimer: #f5f7fa;

  --bgBoxInput: #ffffff;
  --bgInput: #f5f7fa;
  --lineBorderInput: #e6eaf0;
  --textInput: #0b0c12;
  --bgInputFocus: #ffffff;

  --bgBox: #f5f7fa;
  --lineBorderBox: #ced3d9;
  --textBox: #363b47;

  --colorBoxNull: #b2b8bf;
}
main.modo-escuro {
  --bg: #363b47;
  --bgPrimario: #363b47;

  --bgBoxInput: #636973;
  --bgInput: #7e838c;
  --lineBorderInput: #7e838c;
  --textInput: #f5f7fa;
  --bgInputFocus: #7e838c;

  --bgBox: #636973;
  --lineBorderBox: #636973;
  --textBox: #f5f7fa;
}
main {
  background: var(--bg);
  min-height: 100vh;
}
.containerGeral {
  max-width: 1200px;
  margin: 0 auto;
}
.lista {
  padding: 0 20px;
  margin-top: 40px;
}
.lista_div {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
  gap: 20px;
}
@media (max-width: 440px) {
  .lista_div {
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  }
}
.boxNull {
  margin-top: 40px;
  padding: 0 20px;
}
.boxNull > .box {
  max-width: 1200px;
  margin: 0 auto;
  background: var(--bg);
  border: 1px solid var(--colorBoxNull);
  color: var(--colorBoxNull);
}
.v-enter-active,
.v-leave-active {
  transform: translate3d(0, 0, 0);
  transition: 0.2s;
}
.v-enter-from,
.v-leave-to {
  transform: translate3d(-10px, 0, 0);
  opacity: 0;
}
</style>
