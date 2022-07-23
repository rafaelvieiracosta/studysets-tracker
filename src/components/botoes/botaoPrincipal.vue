<template>
  <button class="button">
    <span class="icon">
      <i :class="iconeBotao"></i>
    </span>
    <span>{{textoBotao}}</span>
  </button>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "botaoPrincipal",
  props: ["iconeBotao", "textoBotao"],
});
</script>

<style></style>
