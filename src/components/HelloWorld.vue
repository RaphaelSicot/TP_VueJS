<template>

  <div>
      <div>
    <h1>La grosse liste</h1>
  </div>

  <label for="item">Fruits</label>
  <input type="text" id="item" v-model="item">
  <button @click="Send">Ajouter</button>


  <ul>
    <li v-for="item in items" :key="item" > {{ item  }}</li>
  </ul>
  </div>
</template>

<script>
import axios from 'axios';


export default {
  name: 'HelloWorld', 
  data() {
    return {
      items: ['Bananes meilleur fruit'],
      item: ""
    }
  },
  mounted: function () {
    axios.get('https://api.github.com/users/lblandin%27%27')
      .then( (reponse) => {
      console.log(reponse.data);
    });
  },
  methods : {
      Send(item){
        this.items.push(document.getElementById('item').value);
        item.value = '';
      }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>