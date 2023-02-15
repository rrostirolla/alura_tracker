<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <CronometroTarefas :tempoEmSegundos="tempoEmSegundos" />
        <BotaoPlayPause @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando" />
        <BotaoPlayPause @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando" />
    </div>
</template>

<script lang="ts">
    import { defineComponent } from 'vue'
    import CronometroTarefas from './Cronometro.vue'
    import BotaoPlayPause from './Botao.vue'

    export default defineComponent({
        name: 'TemporizadorTarefas',
        emits: ['aoTemporizadorFinalizado'],
        components: {
            CronometroTarefas,
            BotaoPlayPause
        },
        data () {
            return {
                tempoEmSegundos: 0,
                cronometro: 0,
                cronometroRodando: false
            }
        },
        methods: {
            iniciar () {
                this.cronometroRodando = true
                this.cronometro = setInterval(() => {
                    this.tempoEmSegundos += 1
                }, 1000)
            },
            finalizar () {
                this.cronometroRodando = false
                clearInterval(this.cronometro)
                this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
                this.tempoEmSegundos = 0
            }
        }
    })
</script>