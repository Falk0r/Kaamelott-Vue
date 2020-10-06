<template>
  <!-- <div class="about">
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
  </div> -->
    <v-container fluid>
        <v-row 
            align="center"
            no-gutters
        >
            <v-col cols="12">
                <img 
                    src="../assets/playground.jpg" 
                    alt="playground"
                    class="playground"
                >
                <div
                    class="perceval target"
                    @click="target('perceval')"
                ></div>
                <div
                    class="lancelot target"
                    @click="target('lancelot')"
                ></div>
                <div
                    class="arthur target"
                    @click="target('arthur')"
                ></div>
                <div
                    class="leodagan target"
                    @click="target('leodagan')"
                ></div>
                <div
                    class="bohort target"
                    @click="target('bohort')"
                ></div>      
            </v-col>
        </v-row>
    </v-container>

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
        },
        target(el){
            console.log(el);
        }
        
    },
}
</script>


<style>
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
    .playground{
        position: absolute;
        z-index: 1;
        width: 1920px;
    }
    .perceval{
        position: absolute;
        z-index: 2;
        top: 73px;
        left: 299px;
        height: 200px;
        width: 200px;
        border-radius: 100%;
        
    }
    .lancelot{
        position: absolute;
        z-index: 2;
        top: 267px;
        left: 429px;
        height: 220px;
        width: 220px;
        border-radius: 100%;
    }
    .arthur{
        position: absolute;
        z-index: 2;
        top: 258px;
        left: 860px;
        height: 220px;
        width: 220px;
        border-radius: 100%;
    }
    .leodagan{
        position: absolute;
        z-index: 3;
        top: 314px;
        left: 1372px;
        height: 230px;
        width: 230px;
        border-radius: 100%;
    }
    .bohort{
        position: absolute;
        z-index: 2;
        top: 19px;
        left: 1483px;
        height: 220px;
        width: 220px;
        border-radius: 100%;
    }
    .target{
       cursor: pointer; 
    }
    .target:hover{
        box-shadow: 0px 0px 2px 5000px rgba(0, 0, 0, 0.5);
        border-radius: 120px;
    }
</style>