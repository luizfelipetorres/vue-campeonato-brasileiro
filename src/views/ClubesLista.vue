<template>
    <v-container>
        <h2 class="text-h5 text-center mb-3 mt-5">Classificação</h2>

        <v-simple-table>
            <template v-slot:default>
            <thead>
                <tr>         
                    <th class="text-center">
                        Colocaçãa
                    </th>
                    <th class="text-center">
                        Clube
                    </th>
                    <th class="text-center">
                        Pontos       
                    </th>
                </tr>

                <tr v-for="(clube, index) of clubesListaOrdenada" v-bind:key="clube.id">
                    <td class="text-center"> {{index + 1}} </td>
                    <td class="text-left"> 
                    <v-avatar size="24">
                            <img :src="clube.escudo" :alt="clube.nome">
                        </v-avatar>
                        <span class="pl-3   ">{{clube.nome}} </span>
                    </td>
                    <td class="text-center"> {{clube.pontos}} </td>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td></td>
                    <td></td>
                </tr>
            </tbody>
            </template>
        </v-simple-table>

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
    },
    computed: {
        clubesListaOrdenada(){
            const listaOrdenada = this.clubesLista.slice(0).sort(
                (a, b) =>   a.pontos > b.pontos ? -1 : 1 
            )
            return listaOrdenada    
        }
    }
    
}
</script>

<style scoped>

</style>