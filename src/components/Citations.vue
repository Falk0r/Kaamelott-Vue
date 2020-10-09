<template>
  <div class="about">
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
                    :style="'background-image: url(' + image + ');'"
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
        <v-col cols="3" :style="'text-align: center;'">
            <v-btn color="primary" @click="getQuote">citations</v-btn>
        </v-col>
        <v-col cols="3" :style="'text-align: center;'">
            <v-btn color="error" :to="{name: 'Home'}" exact>retourner</v-btn>
        </v-col>
    </v-row>
    <v-row>

    </v-row>
  </div>
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
      image: "https://static.hitek.fr/img/actualite/2016/06/16/fb_gdwe51vl.jpg",
      model: 0,
    }),
    methods: {
        getQuote(){
            let url = 'https://kaamelott.chaudie.re/api/random/personnage/' + this.$route.params.name;
            let request = new Request(url, {
                method: 'get',
                headers: {
                    'Content-Type': 'application/json',
                    'Access-Control-Allow-Origin' : "*"
                }
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
    .citation{
        position: relative;
        font-family: sans-serif;
        font-size: 18px;
        line-height: 24px;
        min-width: 200px;
        background: #fff;
        border-radius: 40px;
        padding: 24px;
        text-align: center;
        color: #000;
    }
    .citation-bottom-left::before{
        content: "";
        width: 0px;
        height: 0px;
        position: absolute;
        border-left: 24px solid lightgrey;
        border-right: 12px solid transparent;
        border-top: 12px solid lightgrey;
        border-bottom: 20px solid transparent;
        left: 32px;
        bottom: -24px;
    }
    .talk-bubble {
        margin: 40px;
        display: inline-block;
        position: relative;
        min-width: 200px;
        max-width: 500px;
        height: auto;
        background-color: whitesmoke;
    }
    .border{
    border: 8px solid black;
    }
    .round{
    border-radius: 30px;
        -webkit-border-radius: 30px;
        -moz-border-radius: 30px;
    }
    .tri-right.border.left-in:before {
        content: ' ';
        position: absolute;
        width: 0;
        height: 0;
        left: -40px;
        right: auto;
        top: 30px;
        bottom: auto;
        border: 20px solid;
        border-color: black black transparent transparent;
    }
    .tri-right.border.btm-left:before {
        content: ' ';
        position: absolute;
        width: 0;
        height: 0;
        left: -8px;
        right: auto;
        top: auto;
        bottom: -40px;
        border: 32px solid;
        border-color: transparent transparent transparent black;
    }
    .tri-right.border.btm-left-in:before {
        content: ' ';
        position: absolute;
        width: 0;
        height: 0;
        left: 30px;
        right: auto;
        top: auto;
        bottom: -40px;
        border: 20px solid;
        border-color: black transparent transparent black;
    }
    .tri-right.btm-left-in:after{
        content: ' ';
        position: absolute;
        width: 0;
        height: 0;
        left: 38px;
        right: auto;
        top: auto;
        bottom: -20px;
        border: 12px solid;
        border-color: whitesmoke transparent transparent whitesmoke;
    }
    .carousel{
        background-size: cover;
        background-color: black;
    }
</style>