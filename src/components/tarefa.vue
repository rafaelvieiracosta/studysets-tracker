<template>
  <Box>
    <div class="columns">
      <div class="column is-7">{{ tarefa.descricao || 'Tarefa sem descrição'}}</div>
      <div class="column">
        <Cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos" />
      </div>
    </div>
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

<style scoped>

</style>
