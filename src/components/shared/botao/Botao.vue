<!-- alurapic/src/components/shared/botao/Bota.vue -->

<template>
    <button :class="estiloDoBotao" :type="tipo" estilo="perigo" @click="disparaAcao()">{{rotulo}}</button>
</template>
<script>
export default {

   props: {
       tipo: {
           type: String,
           required: true
       },

       rotulo: {
           type: String,
           required: true
       },

       confirmacao: Boolean,
       estilo: String
   },
   methods: {

       disparaAcao() {
           console.log(typeof(this.confirmacao));
           if(this.confirmacao) {
               if(confirm('Confirma operacao?')) {
                    this.$emit('botaoAtivado');
                }
                return;
           }
           this.$emit('botaoAtivado');
       }
   },

   computed: {

       estiloDoBotao() {

           // se o valor é padrão ou não passou nada para estilo
           if(this.estilo == 'padrao') return 'botao botao-padrao';

           if(this.estilo == 'perigo') return 'botao botao-perigo';
       }
   }
}

</script>

<style scoped>
    .botao {
        display: inline-block;
        padding: 10px;
        border-radius: 3px;
        margin: 10px;
        font-size: 1.2em;
    }

    .botao-perigo {
        background: firebrick;
        color: white;
    }

    .botao-padrao {
        background: darkcyan;
        color: white;
    }

</style>
