<template>
  <v-layout row>
    <v-flex xs12 sm6 offset-sm3>
      <v-card>
        <v-list v-model="onSubmit">
          <v-toolbar class="cyan" dark>
            <v-toolbar-title>API Starwars</v-toolbar-title>
          </v-toolbar>
          <template v-for="item in items.results">
            <v-list-tile-content :key="item.id">
              <v-list-tile-title> {{ item.name }} </v-list-tile-title> 
            </v-list-tile-content>
          </template>
        </v-list>    
      </v-card>
    </v-flex>  
  </v-layout>  
</template>
<script>
import axios from 'axios';


export default {
  data () {
    return {
      items: ''
    }
  },
  computed: {
      onSubmit: function (){
        var vm = this;
        console.log (this.question);
        axios.get ('https://swapi.co/api/people')
          .then (function (response){
            console.log(response.data);
            vm.items = response.data;
          })
          .catch (function (error){
            console.log (error);
          })
    }
  }

}
</script>