<template>
    <div class="wrapper" >
    <div class="card" v-for="item in news" :key="item.id" @click="$router.push(`/${item.id}`)">
      <div class="img">
        <img :src="item.image" alt="">
      </div>
      <div class="content">
        <h3>{{ item.title }}</h3>
        <h5>{{ item.price }} $</h5>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
    data() {
    return {
        news:[]
    }
  },
  methods: {
    toPost(id) {
        
    },
    async getPost() {
      let res = await axios.get('https://fakestoreapi.com/products')
      if(res.status ===200) {
        this.news = [...res.data]
      }
    }
  },
  mounted(){
    this.getPost()
  }

}
</script>

<style>
.wrapper {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}
.card {
  width: 280px;
  height: 380px;
  border: 1px solid;
  padding: 1rem;
  margin-bottom: 1rem;
  
}
.card .img {
  width: 260px;
  height: 250px;
}
.card .img img {
  width: 100%;
  height: 100%;
}
.content {
  text-align: center;
}
</style>