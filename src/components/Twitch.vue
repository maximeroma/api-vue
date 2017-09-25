<template>
<v-layout row>
    <v-flex xs12 sm6 offset-sm3>
        <v-form id="form-twitch">
            <v-text-field
                label="Name"
                v-model="user"
                type="text"
                id="username"
                required
            ></v-text-field>
             <v-btn @click="getStream">submit</v-btn>
        </v-form>
        <v-card>
            <v-list>
                <v-toolbar class="cyan" dark>
                    <v-toolbar-title>API Twitch</v-toolbar-title>
                </v-toolbar>
                <template v-if="stream !== null">
                    <v-list-tile-content>
                        <v-list-tile-title> {{ infos.game }} </v-list-tile-title>
                        <v-list-tile-title> {{ infos.viewers }} </v-list-tile-title> 
                        <v-list-tile-title> {{ infos.channel.display_name }} </v-list-tile-title> 
                        <v-list-tile-title> {{ infos.channel.status }} </v-list-tile-title>
                        <img :src="infos.preview.large" alt="stream en cours">  
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
            apiKey: 'YOUR_API_KEY',
            user: '',
            stream: null
        }
    },
    methods: {
        getStream: function (e){
            e.preventDefault();
            let stream = axios.get(`https://api.twitch.tv/kraken/streams/${this.user}?client_id=${this.apiKey}`)
            		.then(res =>  this.infos = res.data.stream)
					.catch(function(err){
						console.log(err)
					})
            stream.then(res => this.stream = res)
        }
    }

}
</script>