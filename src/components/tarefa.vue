<template>
  <Box>
    <div class="title">{{ tarefa.descricao || 'Tarefa sem descrição'}}</div>
    <Cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos" />
  </Box>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import Cronometro from "./cronometro.vue";
import Box from "./box.vue";
import ITarefa from '../interfaces/ITarefas'


export default defineComponent({
  name: "tarefaLista",
  props: {
    tarefa: {
      type: Object as PropType<ITarefa>,
      required: true
    },
  },
  components: {
    Cronometro,
    Box
  },
});
</script>

<style>
</style>
