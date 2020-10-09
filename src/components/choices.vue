<template>
  <v-container class="choices">
      <v-row>
          <v-col cols="12" class="text-center">
              <h1>A vous de choisir :</h1>
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
          >
            <v-icon left>
              mdi-pencil
            </v-icon>
            Ecrit
          </v-btn>
        </v-col>
      </v-row>
  </v-container>
</template>

<script>

export default {
  name: 'Choices'

}
</script>

<style>

.choices{
  height: 50vh;
  background-color: hotpink;
}

</style>