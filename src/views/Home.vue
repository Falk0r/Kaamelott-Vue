<template>
  <div class="home">
    <Parallax :image="imageParallax.image1"/>
    <Title/>
    <Parallax :image="imageParallax.image2"/>
    <Intro/>
    <Choices/>
    <Footer :picture="picture" />
  </div>
</template>

<script>
// @ is an alias to /src
import Parallax from '../components/Parallax';
import Title from '../components/Title';
import Intro from '../components/Intro';
import Choices from '../components/Choices';
import Footer from '../components/Footer';
import router from '../router/index';



export default {
  name: 'Home',
  components: {
    Parallax,
    Title,
    Intro,
    Choices,
    Footer,
  },
  data: () => ({
    imageParallax:
      {
        image1 : "https://aws.vdkimg.com/tv_show/6/0/6/1/60614_backdrop_scale_1280xauto.jpg",
        image2 : "https://img.filmsactu.net/datas/series/k/a/kaamelott/xl/kaamelott-5638c66448079.jpg",
      },
    picture : 'https://i25.servimg.com/u/f25/16/45/41/90/kaamel10.png'
    }),
  methods : {
    choice(character){
      router.push({name: 'Character', params: {name: character}})
    }
  }
}
</script>
