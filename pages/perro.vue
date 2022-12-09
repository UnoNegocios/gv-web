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
  head(){
    return{
      title:'Prueba',
      meta:[{hid: 'og-image', property: 'og:image', content: 'https://gv.unocrm.mx/files/1669855106.png'}]
    }
  }
}
</script>
