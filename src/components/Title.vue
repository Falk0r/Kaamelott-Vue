<template>
  <v-container>
    <v-row
      align="center"
      justify="center"
      class="title"
    >
      <v-col
        class="text-center"
        cols="12"
      >
        <h1>
          {{text}}
        </h1>
        <h4>
          {{subText}}
        </h4>
        <h3>
          L'application
        </h3>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'Title',
    data: () => ({
        text : "Kaamelott",
        subText : "Les chevaliers de la table ronde",
    }),
  }
</script>

<style>
.title{
  height: 20vh;
}
</style>