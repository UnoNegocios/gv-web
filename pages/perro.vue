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
    
    app.head.meta = [/*{
      itemprop: "image",
      hid: 'og:image', 
      rel:"preload",
      property: 'og:image', 
      content: postDetails.featured_media_path
    },*/



    {property:"og:site_name", content:"The Rock Photo Studio"},
    {property:"og:title", content:"The Rock Photo Studio in Florida"},
    {property:"og:description", content:"The best photo studio for your events"},
    {property:"og:image", content:""},
    {property:"og:type", content:"website"},
    {property:"og:image:type", content:"image/jpeg"},
    {property:"og:image:width", content:"300"},
    {property:"og:image:height", content:"300"},
    {property:"og:url", content:"http://www.example.com"},
    
    
    
    
    
    
    
    
    ]
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
