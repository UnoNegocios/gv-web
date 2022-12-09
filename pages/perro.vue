<template>
  <div>hola</div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'IndexPage',
  data(){return{
    image:'',
  }},
  async fetch() {
    let { data } = await axios.get(`https://gv.unocrm.mx/api/v1/news?filter[title]=${encodeURI(this.$route.query.n.replace(/porciento/g, '%').replace(/-/g, ' ').replace(/gionmdio/g, '-'))}`);
    this.image = data
  },
  head(){
    return{
      title:this.$route.query.n.replace(/porciento/g, '%').replace(/-/g, ' ').replace(/gionmdio/g, '-'),
      meta:[{
        hid: 'og:image', 
        property: 'og:image', 
        content: this.image.data[0].featured_media_path
      }]
    }
  }
}
</script>
