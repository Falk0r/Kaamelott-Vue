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
                <h2>Bienvenue sur les citations de Kaamelott</h2>
            </v-col>
        </v-row>
                <v-row
            align="center"
            justify="center"
            class="title"
        >
            <v-col
                class="text-right"
                cols="5"
            >
            <p>
                Venez découvrir les plus belles citations de votre série préféré.
                Ici vous aurez le choix de votre personnage et aurez accès à ses meilleurs citations écrites et audio (en cours de développement.)
            </p>
            </v-col>
            <v-col cols="4" class="d-flex justify-center">
                <img
                    :src="image"
                    height="300"
                    width="300"
                >
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
