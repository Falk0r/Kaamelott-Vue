<template>
  <div class="citations">
    <Citations :image="image" />
  </div>
</template>
<script>

import Citations from '../components/Citations';

export default {
  name: 'Character',
  components: {
      Citations
  },
  data: () => ({
    images : null
    }),
  beforeMount () {
      switch (this.$route.params.name) {
          case "Arthur":
              this.image = "https://static.hitek.fr/img/actualite/2016/06/16/fb_gdwe51vl.jpg";
              break;
          case "Léodagan":
              this.image = "https://file1.telestar.fr/var/telestar/storage/images/3/1/9/2/3192183/kaamelott-livre-livre-5.jpg?alias=original";
              break;
          case "Perceval":
              this.image = "https://lacomtedugeek.fr/wp-content/uploads/2018/07/Kaamelott-Fan-Fiction-La-Com%C3%A9die-Perceval-Arthur.jpg";
              break;
          case "Karadoc":
              this.image = "https://gameofshowsblog.files.wordpress.com/2017/02/sans-titre2.jpg";
              break;
      
          default:
              break;
      }
  }
}
</script>