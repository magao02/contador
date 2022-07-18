<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="formulario de nova atividade">
                <input
                 type="text" class="input" placeholder="qual tarefa você deseja iniciar"
                 v-model="descricao"
                 />
            </div>
            <div class="column">
                <temporizador-i @aoTemporizadorFinalizado="finalizarTarefa"></temporizador-i>
            </div>
        </div>
    </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue'

import TemporizadorI from './TemporizadorI.vue'
    export default  defineComponent({
  components: { TemporizadorI },
        name: "FormularioAtividade",
        data(){
            return{
                descricao: ''
            }
        },
        methods:{
            finalizarTarefa(tempoDecorrido: number) :void {
                console.log(tempoDecorrido);
                console.log(this.descricao);
                this.descricao = '';
            }
        }
        
    }
    )



</script>
