<template>
  <div>
    <SocialHead
      :title="noticia.data[0].title"
      :description="noticia.data[0].short_description"
      :image="noticia.data[0].featured_media_path"
    />
    Hola mundo
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData({route}) {
    const noticia = await fetch(`https://gv.unocrm.mx/api/v1/news?filter[slug]=${route.params.n}`).then((res)=>res.json())
    console.log(noticia)
    return { noticia }
  },
}
</script>
