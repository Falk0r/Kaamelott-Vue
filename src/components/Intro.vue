<template>
    <v-container class="intro">
        <v-row
            align="center"
            justify="center"
            class="sub-title"
        >
            <v-col
                class="text-center"
                cols="12"
            >
                <h2>Bienvenue sur les citations de Kaamelott</h2>
            </v-col>
        </v-row>
                <v-row
            align="center"
            justify="center"
            class="intro-content"
        >
            <v-col
                class="text-right"
                cols="5"
            >
            <p>
                Venez découvrir les plus belles citations de votre série préféré.
                Cette application vous permet de retrouver les citations cultes de la séries Kaamelott.
                Nous vous proposons deux types de citation : écrite et audio.
            </p>
            </v-col>
            <v-col cols="4" class="d-flex justify-center">
                <img :src="image">
            </v-col>
        </v-row>  
    </v-container>
</template>

<script>
  export default {
    name: 'Intro',
    data: () => ({
      image: "https://seek-team-prod.s3.fr-par.scw.cloud/users/5f5f10351668d813344823.png",
    }),
  }

</script>

<style>
.intro{
    height: 40vh;
}
.intro-content{
    height: 30vh;
}
.intro-content .d-flex, .intro-content img{
    height: 100%;
}

.sub-title{
    height: 5vh;
}

</style>
