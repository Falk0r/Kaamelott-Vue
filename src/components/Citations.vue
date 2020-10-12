<template>
  <v-container fluid>
    <v-row
        align="center"
        justify="center"
        class="citations"
    >
        <v-col cols="6">
            <v-carousel v-model="model" hide-delimiters :show-arrows="false">
                <v-carousel-item
                v-for="(citation) in citations"
                :key="citation"
                >
                <v-sheet
                    height="100%"
                    min-width="700"
                    dark
                    :style="'background-image: url(' + picture + ');'"
                    class="carousel"
                    color="black"
                >
                    <v-row
                    class="fill-height"
                    align="center"
                    justify="center"
                    >
                    <div class="display-1">
                        <p>{{citation}}</p>
                    </div>
                    </v-row>
                </v-sheet>
                </v-carousel-item>
            </v-carousel>
        </v-col>
    </v-row>
    <v-row
        justify="center"
        class="controls"
    >
        <v-col cols="3">
            <v-btn color="primary" @click="getQuote">citations</v-btn>
        </v-col>
        <v-col cols="3">
            <v-btn color="error" :to="{name: 'Home'}" exact>retourner</v-btn>
        </v-col>
    </v-row>
  </v-container>
</template>

<script>

import router from '../router/index'

export default {
  name: 'Citations',
  components: {
  },
  props: ['image'],
  data: () => ({
      citations : ['Cliquer sur "citations"'],
      picture: "https://static.hitek.fr/img/actualite/2016/06/16/fb_gdwe51vl.jpg",
      model: 0,
    }),
    methods: {
        getQuote(){
            let url = 'https://kaamelott.chaudie.re/api/random/personnage/' + this.$route.params.name;
            let request = new Request(url, {
                method: 'get',
                headers: {
                    'Content-Type': 'application/json',
                    'Origin' : "https://kaamelott.onrender.com/",
                },
                mode: 'cors',
            })
            fetch(request).then(response => {
                return response.json();
            }).then(text => {
                console.log(text.citation.citation);
                // this.citations = text.citation.citation;
                this.citations.push(text.citation.citation);
                this.model++;
            })
        },
        getBack(){
        router.push({name: 'Home'})
        }
    },
}
</script>

<style>
    .display-1 p{
        margin: 30px;
        text-shadow: 2px 2px 2px black;
        font-size: 0.8em;
    }
    .citations{
        height: 80vh;
        background: rgb(148,148,148);
        background: linear-gradient(180deg, rgba(148,148,148,1) 55%, rgba(255,255,255,0) 35%);
        
    }
    .controls{
        height: 10vh;
    }
    .controls .col{
        text-align: center;
    }
    .carousel{
        background-size: cover;
        background-color: black;
    }
</style>