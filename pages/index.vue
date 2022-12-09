<template>
  <Tutorial/>
</template>

<script>
export default {
  name: 'IndexPage',
  created(){
    console.log(this.$route.params.slug,)
  }
}
</script>
