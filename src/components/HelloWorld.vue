<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
   <div >
     <select v-model="selected">
  <option disabled value="">Please select one</option>
  <option>Coffee</option>
  <option>Hot-Water</option>
  <option>Cappucino</option>
  </select>
<span>Selected: {{ selected }}</span>



  <h2>sugarAmount</h2>
    <vue-slider v-model="sugarAmount"></vue-slider>
  <h2> milkAmount </h2> 
    <vue-slider v-model="milkAmount"></vue-slider>

          <button class="btn btn-primary" v-on:click="send" >submit</button>
   </div>
</div>
</template>

<!--npm install vue-slider-component!-->
<script>
import vueSlider from 'vue-slider-component';
import axios from 'axios';
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: {
    vueSlider
  },

  data() {
    return{
      selected : '', 
      sugarAmount : 0,
      milkAmount : 0,
    }
  },
  methods: {
    send: function(){
      let data = {
        "product": this.selected,
        "milkAmount": this.sugarAmount,
        "sugarAmount": this.milkAmount
      }
      axios.post('http://localhost:8090/coffee/order', {
        data
      })
  }}}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
