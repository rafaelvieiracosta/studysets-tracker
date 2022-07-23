<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro' : modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <Formulario @aoSalverTarefa="salvarTarefa"/>
      <div class="lista" v-if="tarefas.length">
        <Tarefa v-for="tarefa, i in tarefas" :key="i" :tarefa="tarefa"/>
      </div>
      <Box v-else>
        Você não está muito produtivo hoje
      </Box>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/barraLateral.vue'
import Formulario from './components/formulario.vue'
import Tarefa from './components/tarefa.vue'
import Box from "./components/box.vue";
import ITarefa from './interfaces/ITarefas'

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Formulario,
    Tarefa,
    Box
  },
  data(){
    return{
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa){
      console.log(tarefa)
      this.tarefas.push(tarefa)
      console.log(this.tarefas)
    },
    trocarTema(modoEscuroAtivo: boolean){
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>

<style>
main{
  --bgPrimario: #fff;
  --textoPrimario: #000
}
main.modo-escuro{
  --bgPrimario: rgb(39, 39, 39);
  --textoPrimario: #fff
}
.conteudo{
  background-color: var(--bgPrimario);
}
.lista strong{
  color: #000;
}
</style>
