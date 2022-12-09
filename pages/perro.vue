<template>
  <div>hola</div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'IndexPage',
  async asyncData({ app, route }) {
    let postDetails = await axios.get(`https://gv.unocrm.mx/api/v1/news?filter[slug]=${route.query.n}`);
    postDetails = postDetails.data.data[0];
    app.head.meta = [{
      itemprop: "image",
      hid: 'og:image', 
      rel:"preload",
      name: 'og:image', 
      content: postDetails.featured_media_path
    }]
    return { postDetails };
  },
}
/*
  data(){return{
    image:'',
  }},
  async fetch() {
    let { data } = await axios.get(`https://gv.unocrm.mx/api/v1/news?filter[slug]=${this.$route.query.n}`);
    this.image = data.data[0].featured_media_path
    console.log(this.image)
  },
  head(){
    return{
      title:'prueba',
      meta:[{
        hid: 'og:image', 
        property: 'og:image', 
        content: this.image
      }]
    }
  }
}
*/
</script>
