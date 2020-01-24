<template>
  
  <div id="app" class="container">
    
    <h1>Shoppping List</h1>
    
    <ShoppingList :products="products" @removeProduct="removeProduct($event)"></ShoppingList>
    
    <Form @newProduct="addProduct($event)" @removeLine="products.pop()"></Form>

  </div>

</template>

<script>

import Form from './components/Form/Form'
import ShoppingList from './components/ShoppingList/ShoppingList'
import Swal from 'sweetalert2'

export default {
  name: "app",
  components: {
    Form,
    ShoppingList
  },
  methods: {
    addProduct(product) {
      if (this.products.length > 0) {
        for (const prod of this.products) {
          if (product.name === prod.name) {
            Swal.fire({
              icon: 'error',
              title: 'Error',
              text: 'The name alredy exists',
              confirmButtonText: 'Retry',
              confirmButtonColor: 'green'
            })
            break
          } else {
            this.products.push(product)
            break
          }
        }
      } else {
        this.products.push(product)
      }
    },
    removeProduct(product) {
      for (let i = 0; this.products.length; i++) {
        if (this.products[i].name === product.name) {
          this.products.splice(i, 1)
          break
        }
      }
    }
  },
  data() {
    return {
      products: []
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

.mBtn {
  margin-left: 10px;
}

</style>
