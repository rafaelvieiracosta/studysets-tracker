<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
        <input type="text" class="input" placeholder="Qual tarefa você deseja iniciai?" v-model="descricaoTarefa">
      </div>
      <div class="column">
        <Temporizador @aoTemporizadorFinalizado="finalizarTarefa"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Temporizador from './temporizador.vue'

export default defineComponent({
  name: 'formularioPrincipal',
  data(){
    return{
      descricaoTarefa : null
    }
  },
  components: {
    Temporizador
  },
  methods: {
    finalizarTarefa(tempoDecorrido: number) : void{
      console.log(tempoDecorrido, this.descricaoTarefa)
      this.descricaoTarefa = null
    }
  }
})
</script>

<style>

</style>