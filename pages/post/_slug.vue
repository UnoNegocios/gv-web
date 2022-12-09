<!--template>
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
    const noticia = await fetch(`https://gv.unocrm.mx/api/v1/news?filter[slug]=el-detras-de-los-meses-sin-intereses-factibles-o-no`).then((res)=>res.json())
    
    return { noticia }
  },
}
</script-->


<template>
  <article>
    <SocialHead
      :title="mountain.data[0].title"
      :description="mountain.data[0].short_description"
      :image="mountain.data[0].featured_media_path"
    />
    <h1>{{ mountain.data[0].title }}</h1>
    <section>
      <img :src="mountain.data[0].featured_media_path" :alt="mountain.data[0].title" />
      <p>{{ mountain.data[0].short_description }}</p>
    </section>
    <button @click="goBack">Back</button>
  </article>
</template>
<script>
export default {
  async asyncData({ params }) {
    const mountain = await fetch(
      `https://gv.unocrm.mx/api/v1/news?filter[slug]=${params.slug}`
    ).then((res) => res.json())
    return { mountain }
  },
  methods: {
    goBack() {
      return this.$router.go(-1)
    }
  },
  head() {
    return {
      link: [
        {
          hid: 'canonical',
          rel: 'canonical',
          href: `https://gv.unocrm.mx/api/v1/news?filter[slug]=${this.$route.params.slug}`
        }
      ]
    }
  }
}
</script>
<style scoped>
article {
  max-width: 600px;
  margin: 0 auto;
}
img {
  height: 200px;
}
p {
  text-align: left;
}
</style>
