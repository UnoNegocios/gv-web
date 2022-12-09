<template>
  <div>hola</div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'IndexPage',
  async asyncData({ app, route }) {
    let postDetails = await app.$axios.get(`https://gv.unocrm.mx/api/v1/news?filter[title]=${encodeURI(route.query.n.replace(/porciento/g, '%').replace(/-/g, ' ').replace(/gionmdio/g, '-'))}`);
    postDetails = postDetails.data.data[0];
    const mutation = app.head.meta.map(i => {
      if(i && i.hid){
        if(i.hid === 'title'){
          i.content = postDetails.title
        }
        if(i.hid === 'og:image'){
          i.content = postDetails.featured_media_path
        }
      }
      return i;
    });
    app.head.meta = mutation;
    return { postDetails };
  },
}
/*
  data(){return{
    image:'',
  }},
  async fetch() {
    let { data } = await axios.get(`https://gv.unocrm.mx/api/v1/news?filter[title]=${encodeURI(this.$route.query.n.replace(/porciento/g, '%').replace(/-/g, ' ').replace(/gionmdio/g, '-'))}`);
    this.image = data.data[0].featured_media_path
    console.log(this.image)
  },
  head(){
    return{
      title:this.$route.query.n.replace(/porciento/g, '%').replace(/-/g, ' ').replace(/gionmdio/g, '-'),
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
