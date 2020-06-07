<template>
  <div id="app">
       <h1>Paginando Tabela</h1>
       <Tabela v-if="dadosTabela" :osDados="dadosTabela" :configuracao="configuracao"  :style="{height: '600px'}"/>
  </div>
</template>

<script>
import Tabela from './components/Tabela.vue'

export default {
     components: {Tabela},     
     data() {
        return {
             dadosTabela: undefined,
             configuracao: [
                 {chave: 'foto', titulo: 'Foto', tipo: 'image'},
                 {chave: 'nome', titulo: 'Nome', tipo: 'text'},
                 {chave: 'cidade', titulo: 'Cidade', tipo: 'text'},
                 {chave: 'ocupacao', titulo: 'Ocupação', tipo: 'text'},
                 {chave: 'periodo', titulo: 'Registro', tipo: 'date'}
             ]
        }
     },
     mounted() {
         this.$axios.get('http://localhost:8081/link')
             .then(({data}) => {
                 this.dadosTabela = data
             })
     }
}
</script>

<style>
body {
  font-family: Helvetica, sans-serif;
  font-weight: 400;
  background-color: #4cb69f;
  color: white;
  
}

h1 {
  font-size: 5rem;
   align-self: center;
   justify-content: center;
   display: flex;
   -webkit-text-stroke-width: 3px;
   -webkit-text-stroke-color: black;
   
}
</style>
