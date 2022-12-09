<template>
  <div>hola</div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'IndexPage',
  head(){
    return{
      title:'Prueba',
      meta:[{
        hid: 'og:image', 
        property: 'og:image', 
        content: 'https://www.bubblypet.com/wp-content/uploads/2021/08/Shepherd-dog-breed-Australian-Shepherd.jpg'
      }]
    }
  }
}
</script>
