<template>
  <div class="about">
    <h1>This is {{$route.params.name}}</h1>
  </div>
</template>

<script>
export default {
  name: 'Character',
  components: {
  },
  data: () => ({
    imageParallax:
      {
        image1 : "https://actugeekgaming.com/wp-content/uploads/2019/01/thumb-1920-806749.jpg",
        image2 : "https://img.filmsactu.net/datas/series/k/a/kaamelott/xl/kaamelott-5638c66448079.jpg"
      },
    })
}
</script>