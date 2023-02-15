<template>
    <BoxPadrao>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="columns">
                <Cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </BoxPadrao>
</template>

<script lang="ts">
    import { defineComponent, PropType } from 'vue';
    import Cronometro from './Cronometro.vue';
    import ITarefa from '../interfaces/ITarefa';
    import BoxPadrao from './Box.vue';

    export default defineComponent({
        name: 'TarefaCronometrada',
        components: {
            Cronometro,
            BoxPadrao
        },
        props: {
            tarefa: {
                type: Object as PropType<ITarefa>,
                required: true 
            }
        }
    })
</script>