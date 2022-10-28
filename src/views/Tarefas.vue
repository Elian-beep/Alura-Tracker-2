<template>
  <FormularioPrincipal @aoSalvarTarefa="salvarTarefa" />
  <div class="lista">
    <TarefaVue
      v-for="(tarefa, index) in tarefas"
      :key="index"
      :tarefa="tarefa"
    />
    <BoxVue v-if="listaEstaVazia">
      Você não está muito produtivo hoje :(</BoxVue
    >
  </div>
</template>
  
<script lang="ts">
import { defineComponent } from "vue";
import FormularioPrincipal from "@/components/FormularioPrincipal.vue";
import TarefaVue from "../components/TarefaVue.vue";
import ITarefa from "../interfaces/ITarefa";
import BoxVue from "../components/BoxVue.vue";

export default defineComponent({
  name: "TarefasView",
  components: { FormularioPrincipal, TarefaVue, BoxVue },
  data() {
    return {
      tarefas: [] as ITarefa[],
    };
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    },
  },
  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length == 0; //Retorna true se a lista estiver vazia
    },
  },
});
</script>
  
<style>
</style>