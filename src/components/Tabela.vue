<template>
      <section class="tabela">
          <table>
              <thead>
                 <tr>
                     <th v-for="(objeto, indice) in configuracao" :key="indice">
                          {{objeto.titulo}}
                     </th>
                 </tr>
              </thead>
              <tbody>
                  <tr v-for="(linha, i) in osDados" :key="i">
                      <td v-for="(objeto, indice) in configuracao" :key="indice">
                          <span v-if="objeto.tipo === 'text'">{{linha[objeto.chave]}}</span>
                          <span v-if="objeto.tipo === 'date'">{{new Date(linha[objeto.chave]).toLocaleDateString()}}</span>
                          <figure v-if="objeto.tipo === 'image'">
                              <img :src="linha[objeto.chave]" height="80px" width="100px">
                          </figure>
                      </td>
                  </tr>
              </tbody>
          </table>
      </section>
</template>

<script>
export default {
   props: ['osDados','configuracao']
}
</script>

<style lang="scss">
.tabela {
    border: 1px solid #999;
    border-radius: 9px;
    color: #333;
    overflow: auto;
    width: 1000px;
    margin: 50px;
    background-color: white;

    figure {
        margin-block-start: 0;
        margin-block-end: 0;
        margin-inline-start: 0;
        margin-inline-end: 0;

        img {
            border: 1px solid #bbb;
            border-radius: 50%;
            overflow: hidden;
        }
    }

    table {
        border-collapse: collapse;
        width: 100%;

        th {
            position: sticky;
            top: 0;
            background: #0f2862;
            padding: 10px 5px;
            text-align: left;
            border-bottom: 1px solid grey;
            color: gold;
            text-align: center;
        }
        
        td {
            padding: 5px 5px;
            text-align: left;
            color: darkgreen;
            font-weight: 900;
            font-family:Arial, Helvetica, sans-serif;
            text-align: center;
        }
    }
}

</style>