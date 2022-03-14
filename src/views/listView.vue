
<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <h1>{{legend}}</h1>
    <div class="row">
        <div>
            <select v-model="selected" name="filtre" id="select-filtre">
                <option disabled value="">Choisissez</option>
                <option value="HOUSE">Maison</option>
                <option value="FLAT">Appartement</option>
                <option value="LAND">Terrain</option>
            </select>
        </div>
        <div v-for="good in goods"
             :key="good.id"
             class="col-xs-12">
            {{good.title}}
        </div>
        <div class="col-xs-12">
            <i class="fa-solid fa-arrow-left"></i>précedent
        </div>

    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";

export default {
  name: 'listView',
  components: {
  },
    data() {
        return {
            legend: "Les biens suivants vous sont présentés par Adapt'Immo : ",
            goods: [], // Contient toutes les données de l'API
            selected: '',
        };
    },
    async mounted(){
      const response = await axios.get(' https://apiclient.adaptimmo.com/test/bien?perpage=20');
      this.goods= response.data.data
    }
}
</script>
