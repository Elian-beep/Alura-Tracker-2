<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <CronometroForm :tempoEmSegundos="tempoEmSegundos" />
    <BotaoForm @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando" />
    <BotaoForm @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import CronometroForm from './CronometroForm.vue';
import BotaoForm from './BotaoForm.vue';

export default defineComponent({
  name: "TemporizadorForm",
  emits: ['aoTemporizadorFinalizado'],                    //Em determinado momento, vai emitir algo
  components: { CronometroForm, BotaoForm },
  data(){                       //Vai criar e retornar os dados mutados que serão usados no componente
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      cronometroRodando: false,
    }
  },
  methods: {                   //Funções que serão utilizadas dentro do componente
    iniciar() {
      // começar a contagem
      // 1s = 1000ms
      this.cronometroRodando = true;
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos++
        
      }, 1000);
      console.log('iniciando');
      
    },
    finalizar() {
        this.cronometroRodando = false;
        clearInterval(this.cronometro);
        this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos); //Vai emitir o tempo em segundos ao finalizar
        this.tempoEmSegundos = 0;
    }
  }
});
</script>