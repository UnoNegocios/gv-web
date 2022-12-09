<template>
  <v-container>
    <SocialHead
      :title="noticia.data[0].title"
      :description="noticia.data[0].short_description"
      :image="noticia.data[0].featured_media_path"
    />
  </v-container>
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData({route}) {
    const noticia = await fetch(`https://gv.unocrm.mx/api/v1/news?filter[slug]=${route.params.id}`).then((res)=>res.json())
    return { noticia }
  },
}
</script>
