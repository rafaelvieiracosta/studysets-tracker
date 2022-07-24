<template>
  <div class="box">
    <slot></slot>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "BoxWrapper",
});
</script>

<style>
.box {
  background: var(--bgBox);
  border: 1px solid var(--lineBorderBox);
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 20px;
}
.box .title {
  font-family: "Poppins";
  font-style: normal;
  font-weight: 600;
  font-size: 16px;
  line-height: 20px;
  color: var(--textBox);
}
</style>
