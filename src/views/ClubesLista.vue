<template>
    <v-container>
        <h2 class="text-h5 text-center mb-3 mt-5">Classificação</h2>

    </v-container>
</template>

<script>
export default {
    name: 'ClubesLista',

    data(){
        return {
            clubesLista: []
        }
    },
    created(){
        fetch('https://hackthon-decola.firebaseio.com/clubes-lista.json')
            .then(resposta => resposta.json())
            .then(json => {
                this.clubesLista = json
                //console.log(this.clubesLista)
            })
    }
    
}
</script>

<style scoped>

</style>