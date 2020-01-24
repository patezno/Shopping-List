<template>
  <div id="app" class="container">
    <h1>Shoppping List</h1>
    <ShoppingList></ShoppingList>
    <div>
      <span>Total expense: {{total}}</span>
    </div>
    <Form v-on:newProduct="addProduct($event)"></Form>
  </div>
</template>

<script>
import Form from './components/Form'
import ShoppingList from './components/ShoppingList'

export default {
  name: "app",
  components: {
    Form,
    ShoppingList
  },
  methods: {
    addProduct(product) {
      this.total += product.price
    }
  },
  data() {
    return {
      total: null
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
