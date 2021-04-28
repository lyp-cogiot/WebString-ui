<template>
  <div id="app">
    <img src="./assets/logo.png" float="left">
    <div align="center">
      输入的字符串: <input type="text" v-model="string" float = "right">
      <button @click="sendMessage" type="submit">提交</button>
      <p>{{ message }}</p>
    </div>
  </div>
</template>
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
<script>
export default {
  name: 'App',
  data () {
    return {
      string: '',
      message: ''
    }
  },
  methods: {
    sendMessage () {
      var vm = this
      axios.post('http://localhost:8080/getWebString',{
      "webString":vm.string
    })
      .then(function (response) {
          console.log(response)
          console.log(JSON.stringify(response))
          vm.message=response["data"]["webString"]
      })
      .catch(function (error) {
          console.log(error);
      });
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
