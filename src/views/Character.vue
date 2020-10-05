<template>
  <div class="about">
    <h1>This is {{$route.params.name}}</h1>
    <v-btn color="success" @click="getQuote">citations</v-btn>
    <v-row v-if="citation">
        <v-col cols="12">  
            <div class="talk-bubble tri-right border round btm-left-in">
                <div class="talktext">
                    <p>{{citation}}</p>
                </div>
            </div>
        </v-col>
    </v-row>
    <v-row>
        <router-link to="/">
            <v-btn color="success">retourner</v-btn>
        </router-link>
    </v-row>
  </div>
</template>

<script>

import router from '../router/index'

export default {
  name: 'Character',
  components: {
  },
  data: () => ({
      citation : null
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
                this.citation = text.citation.citation;
            })
        },
        getBack(){
        router.push({name: 'Home'})
        }
    },
}
</script>

<style lang="less">
    .v-application p{
        margin: 30px;
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
</style>