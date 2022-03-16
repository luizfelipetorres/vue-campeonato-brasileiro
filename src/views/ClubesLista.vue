<template>
    <v-container>
        <h2 class="text-h5 text-center mb-3 mt-5">Classificação</h2>
        <TabelaClubes/>
    </v-container>
</template>

<script>
import TabelaClubes from '../components/TabelaClubes.vue'

export default {
    name: 'ClubesLista',
    components: {
        TabelaClubes
    }
    
}
</script>

<style scoped>

</style>