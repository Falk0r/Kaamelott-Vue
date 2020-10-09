<template>
    <v-container fluid>
        <v-row 
            align="center"
            no-gutters
        >
            <v-col cols="12">
                <v-btn color="error" :to="{name: 'Home'}" exact class="return">retourner</v-btn>
                <img 
                    src="../assets/playground.jpg" 
                    alt="playground"
                    class="playground"
                >
                <div
                    class="perceval target"
                    @click="target('Perceval')"
                ></div>
                <div
                    class="lancelot target"
                    @click="target('Lancelot')"
                ></div>
                <div
                    class="arthur target"
                    @click="target('Arthur')"
                ></div>
                <div
                    class="leodagan target"
                    @click="target('Léodagan')"
                ></div>
                <div
                    class="bohort target"
                    @click="target('Bohort')"
                ></div>      
            </v-col>
        </v-row>
    <audio :src="citation" autoplay id="myAudio"></audio>
    </v-container>
</template>

<script>

import router from '../router/index';
import {files} from './sounds';

export default {
  name: 'Playground',
  components: {
  },
  data: () => ({
      citation : ""
    }),
    methods: {
        getBack(){
        router.push({name: 'Home'})
        },
        target(el){
            console.log(el);
            // console.log(files);
            const player = [];
            for (let index = 0; index < files.length; index++) {
                const element = files[index];
                if (element.character == el) {
                    player.push(element.file);
                }
            }
            console.log(player[this.getRandomInt(player.length)]);
            this.citation = "https://kaamelott-soundboard.2ec0b4.fr/sounds/" + player[this.getRandomInt(player.length)];
        },
        getRandomInt(max) {
            return Math.floor(Math.random() * Math.floor(max));
        },
    },
}
</script>


<style>
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
    .return{
        position: absolute;
        z-index: 2;
        margin: 10px;
    }
</style>