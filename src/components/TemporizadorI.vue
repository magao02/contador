<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <cronometro-i :tempoSegundos="tempoSegundos"></cronometro-i>
            <button class="button" @click="iniciar" :disabled="CronometroRodando">
                <span class="icon">
                    <i class="fas fa-play"></i>
                </span>
                <span>play</span>
            </button>
            <button class="button" @click="finalizar" :disabled="!CronometroRodando">                    <span class="icon">
                        <i class="fas fa-stop"></i>
                    </span>
                    <span>stop</span>
                </button>
                </div>
</template>
<script lang="ts">
    import { defineComponent } from 'vue'
    import CronometroI from './CronometroI.vue'
    
    export default  defineComponent({
        components: { CronometroI },
        name: "TemporizadorI",
        emits:['aoTemporizadorFinalizado'],
        data (){
            return {
                tempoSegundos: 0,
                cronometro : 0,
                CronometroRodando: false,
            }
        },
        computed: {
            tempoDecorrido () : string {
                return new Date(this.tempoSegundos * 1000).toISOString().substr(11,8)
            }
        },
        methods:{
            iniciar(){
                this.CronometroRodando = true;
                this.cronometro = setInterval(()=>{
                    this.tempoSegundos +=1
                },1000)
                console.log('inicial')
            },
            finalizar (){
                this.CronometroRodando = false;
                clearInterval(this.cronometro);
                console.log('final');
                this.$emit('aoTemporizadorFinalizado',this.tempoSegundos)
                this.tempoSegundos = 0;
            }
        }
    })



</script>
