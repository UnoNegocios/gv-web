<template>
  <NuxtLogo/>
</template>

<script>
import axios from 'axios'
export default {
  name: 'IndexPage',
  data(){return{
    image:''
  }},
  created(){
    axios.get('https://gv.unocrm.mx/api/v1/news?filter[title]=' + this.$route.query.noticia.replace(/porciento/g, '%').replace(/-/g, ' ').replace(/gionmdio/g, '-')).then(resp=>{
      this.image = resp.data.data[0].featured_media_path
      console.log(this.image)
    })
  },
  head:{
    //return{
      title:'Prueba',
      meta:[{property: 'og:image', content: 'https://www.purina.es/sites/default/files/styles/ttt_image_510/public/2021-02/BREED%20Hero%20Mobile_0026_siberian_husky.jpg'}]
    //}
  }
}
</script>
