<template>
  <div>
    <h1>{{ post.title }}</h1>
    <p>{{ post.description }}</p>
    <img :src="post.image" alt="">
    <h4>{{ post.price }}</h4>

  </div>
</template>

<script>
import axios from 'axios'
export default {
    data: () =>({
        id: '',
        post: {}
    }),
    methods: {
        async getPostById() {
            let res = await axios.get(`https://fakestoreapi.com/products/${this.id}`)
            if(res.status ===200) {
                this.post = {...res.data}
            }
        }
    },
    mounted () {
        this.id = this.$route.params.id
        this.getPostById()
    }
}
</script>

<style>

</style>