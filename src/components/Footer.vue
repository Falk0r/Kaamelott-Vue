<template>
    <v-container>
      <v-row justify="center">
        <v-col cols="6">
          <v-img :src="picture"></v-img>
        </v-col>
      </v-row>
    </v-container>
</template>

<script>
  export default {
    name: 'Footer',
    props: ['picture'],
  }
</script>
