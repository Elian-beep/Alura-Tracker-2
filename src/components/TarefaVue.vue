<template>
  <BoxVue>
    <div class="columns">
      <div class="column is-7">
        {{ tarefa?.descricao || "Tarefa sem descrição" }}
      </div>
      <div class="column">
        <CronometroForm :tempoEmSegundos="tarefa?.duracaoEmSegundos" />
      </div>
    </div>
  </BoxVue>
</template>

<script lang="ts">
import ITarefa from "@/interfaces/ITarefa";
import { defineComponent, PropType } from "vue";
import BoxVueVue from "./BoxVue.vue";
import CronometroForm from "./CronometroForm.vue";
import BoxVue from "./BoxVue.vue";

export default defineComponent({
  name: "TarefaVue",
  components: { CronometroForm, BoxVue },
  props: {
    tarefa: {
      type: Object as PropType<ITarefa>,
      requiered: true,
    },
  },
});
</script>