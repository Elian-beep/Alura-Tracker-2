<template>
  <div class="box has-text-weight-bold">
    <slot></slot> <!-- o que estive dentro do componente será renderizado normal -->
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "BoxVue",
});
</script>

<style scoped>
.box {
  background: #faf0ca;
}
</style>