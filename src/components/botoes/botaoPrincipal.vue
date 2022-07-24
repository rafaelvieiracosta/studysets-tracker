<template>
  <button class="buttonPrincipal" v-html="iconeBotao"></button>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "botaoPrincipal",
  props: ["iconeBotao", "textoBotao"],
});
</script>

<style>
.buttonPrincipal {
  display: flex;
  justify-content: center;
  align-items: center;
  min-width: 50px;
  min-height: 50px;
  border: none;
  border-radius: 4px;
  background: linear-gradient(180deg, #18a0fb 0%, #0077c7 100%);
  cursor: pointer;
  transition: 0.2s;
}
.buttonPrincipal:hover {
  transform: scale(0.92);
}
.buttonPrincipal:disabled {
  opacity: 0.3;
}
.buttonPrincipal + .buttonPrincipal {
  margin-left: 10px;
}
</style>
