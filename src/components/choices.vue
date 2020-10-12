<template>
  <v-container class="choices" fluid>
      <v-row>
          <v-col cols="12" class="text-center">
              <h2>A vous de choisir :</h2>
              <p>Vous avez le choix entre les citations audio où vous entendrez dans votre navigateur les répliques indémodables parmis un choix de personnage.</p>
              <p>Ou si les citations écrites, pour vous remémorer les passages devenus cultes de Kaamelott, vous pouvez prendre le temps de la lire et pourquoi pas la mémoriser !</p>
          </v-col>
      </v-row>
      <v-row>
        <v-col cols="6" class="d-flex justify-center">
          <v-btn
            elevation="6"
            rounded
            text
            x-large
            to="/audio"
          >
            <v-icon left>
              mdi-volume-high
            </v-icon>
            Audio
          </v-btn>
        </v-col>
        <v-col cols="6" class="d-flex justify-center">
          <v-btn
          depressed
            elevation="6"
            rounded
            text
            x-large
            @click="overlay = !overlay"
          >
            <v-icon left>
              mdi-pencil
            </v-icon>
            Ecrit
          </v-btn>
        </v-col>
        <v-overlay
          :absolute="absolute"
          :opacity="opacity"
          :value="overlay"
        >
          <Characters :choice="choice" />
          <v-btn
            color="red lighten-2"
            @click="overlay = false"
          >
          Annuler
          </v-btn>
        </v-overlay>
      </v-row>
  </v-container>
</template>

<script>

import Characters from '../components/Characters';
import router from '../router/index';

export default {
  name: 'Choices',
  components: {
    Characters,
  },
  data : () => ({
    absolute: false,
    opacity: 0.9,
    overlay: false,
  }),
  methods : {
    choice(character){
      router.push({name: 'Character', params: {name: character}})
    }
  }
}
</script>

<style>

.choices{
  height: 40vh;
}
</style>