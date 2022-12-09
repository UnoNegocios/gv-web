<template>
  <NuxtLogo/>
</template>

<script>
export default {
  name: 'IndexPage',
  created(){
    console.log(this.$route.query.noticia)
  },
  head:{
    title:'Prueba',
    meta:[{property: 'og:image', content: 'https://www.purina.es/sites/default/files/styles/ttt_image_510/public/2021-02/BREED%20Hero%20Mobile_0026_siberian_husky.jpg?itok=glDRcRov'}]
  }
}
</script>
