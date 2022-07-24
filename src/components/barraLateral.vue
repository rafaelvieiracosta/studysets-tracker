<template>
  <header>
    <div class="header_div containerGeral">
      <img src="../assets/logo.svg" alt="studysets" />
      <button class="button" @click="alterarTema" v-html="textoBotao"></button>
    </div>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "BarraLateral",
  emits: ["aoTemaAlterado"],
  data() {
    return {
      modoEscuroAtivo: false,
    };
  },
  computed: {
    textoBotao() {
      if (this.modoEscuroAtivo) {
        return "&#10022";
      }
      return "&#10023";
    },
  },
  methods: {
    alterarTema() {
      this.modoEscuroAtivo = !this.modoEscuroAtivo;
      this.$emit("aoTemaAlterado", this.modoEscuroAtivo);
    },
  },
});
</script>

<style>
header {
  background: var(--bgHeader);
  padding: 0 20px;
}
.header_div {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 40px 0 20px;
}
.header_div > button{
  border: none;
  background: none;
  color: var(--colorBoxNull);
  cursor: pointer;
  font-size: 32px;
  line-height: 34px;
}
@media (max-width: 600px) {
  .header_div {
    padding: 30px 0;
  }
}
</style>
