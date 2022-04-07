<template>
<ul>
  <li v-for="post in posts" :key="post">{{post[1]}} {{post[2]}}</li>
</ul>
</template>

<script>
export default {
  name: "Flight_data",
  methods: {
    async getData() {
      try{
        let res = await fetch('https://opensky-network.org/api/states/all');
        let data = await res.json();
        console.log(data)
        this.posts = data['states']
        this.time = data['time']
      } catch (error) {
        console.log(error)
      }
    }
  },
  data() {
    return {
      posts: []
    }
  },
  mounted() {
    this.getData()
  }
}
</script>

<style scoped>

</style>