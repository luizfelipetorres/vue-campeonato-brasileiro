<template>
    <v-container>

        <!--Radio buttons de ordem-->
 <v-radio-group
            v-model="radio"
            column
            >
            <v-radio
                label="Ordem decrescente"
                value="1"
                color="light-green"
                @select="radio = '1'"
            ></v-radio>
            <v-radio 
                label="Ordem crescente"
                value="2"
                color="light-green"
                @select="radio = '2'"
            ></v-radio>
            </v-radio-group>
        
        <!--Tabela-->
        <v-simple-table>
            <template v-slot:default>
            <thead>
                    <tr>         
                        <th class="text-center ">
                            Colocaçãa
                        </th>
                        <th class="text-center">
                            Clube
                        </th>
                        <th class="text-center">
                            Pontos       
                        </th>
                    </tr>

                <tr  v-for="(clube, index) of ordenarLista" v-bind:key="clube.id">
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
    name: 'TabelaClubes',
    data(){
        return {
            clubesLista: [],
            radio: '1',
        }
    },
    created(){
        fetch('https://hackthon-decola.firebaseio.com/clubes-lista.json')
            .then(resposta => resposta.json())
            .then(json => {
                this.clubesLista = json
                //console.log(this.clubesLista)
            })
        console.log(this.radio)


    },
    computed: {
        ordenarLista(){
            let lista
            if (this.radio == '1'){
                lista = this.clubesLista.slice(0).sort(
                    (a, b) =>   a.pontos > b.pontos ? -1 : 1 
                )
            }else{
                lista = this.clubesLista.slice(0).sort(
                    (a, b) =>   a.pontos > b.pontos ? 1 : -1 
                )
            }
            return lista
        },
        listaOrdenada(){
            const lista = this.clubesLista.slice(0).sort(
                (a, b) =>   a.pontos > b.pontos ? -1 : 1 
            )
            return lista
        }
    }
}
</script>

