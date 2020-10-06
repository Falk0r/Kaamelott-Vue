<template>
  <div class="home">
    <Parallax :image="imageParallax.image1"/>
    <Title/>
    <Parallax :image="imageParallax.image2"/>
    <Intro/>
    <Characters :choice="choice" />
  </div>
</template>

<script>
// @ is an alias to /src
import Parallax from '../components/Parallax';
import Title from '../components/Title';
import Intro from '../components/Intro';
import Characters from '../components/Characters';
import router from '../router/index'


export default {
  name: 'Home',
  components: {
    Parallax,
    Title,
    Intro,
    Characters,
  },
  data: () => ({
    imageParallax:
      {
        image1 : "https://actugeekgaming.com/wp-content/uploads/2019/01/thumb-1920-806749.jpg",
        image2 : "https://img.filmsactu.net/datas/series/k/a/kaamelott/xl/kaamelott-5638c66448079.jpg"
      },
    }),
  methods : {
    choice(character){
      router.push({name: 'Character', params: {name: character}})
    }
  }
}
</script>
