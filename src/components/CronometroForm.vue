<template>
  <section>
    <strong class="display">{{ tempoDecorrido }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "CronometroForm",
  props: {
    tempoEmSegundos: {
      type: Number,
      default: 0
    }
  },
  computed: {                   //Vai monitorar e computar uma informaçõa caso ela seja alterada
    tempoDecorrido() : string { //Retorna uma string
      return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11, 8);
    }
  },
});
</script>

<style scoped>
.display{
  color: var(--texto-primario);
}
</style>