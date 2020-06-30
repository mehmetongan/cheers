<template>
  <v-container>
    <v-row class="beers">
      <v-col v-for="beer in beers" :key="beer.data.id" cols="3">
          test
        <!-- <img :src="beer.data.labels.medium"> -->
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";
  export default {
    name: 'Beers',
    data: () => ({
      beers: []
    }),
    mounted() {
        this.loadBeers();
    },
    methods: {
        loadBeers() {
            axios
            .get('https://sandbox-api.brewerydb.com/v2/beers/?key=6b4c6ac74f967e90036017a778942f57',
               { 
                    headers: {
                        'Content-Type': 'application/json',
                        'Transfer-Encoding': 'cunked',
                        'Connection': 'keep-alive'
                    }
               })
            .then(response => {
                this.beers = response.data;
                console.log('reponse : ' + response.data);
            })
            .catch(error => {
                console.log('erreur :' + error);
            })
        }
    }
  }
</script>
