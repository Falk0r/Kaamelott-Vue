<template>
    <v-row
      align="center"
      justify="center"
      class="title"
    >
      <v-col
        class="text-center"
        cols="12"
      >
        <h1 class="display-1 font-weight-thin mb-4">
          {{text}}
        </h1>
        <h4 class="subheading">
            {{subText}}
        </h4>
        <h3 class="font-weight-thin">
            L'application
        </h3>
      </v-col>
    </v-row>
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


<style lang="less">
  body{
    .title {
      height: 20vh;
    }
  }
</style>
