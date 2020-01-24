<template>
  
  <div id="app">

    <div class="navbar-fixed">
      <nav class="green">
        <div class="nav-wrapper">
          <a href="#" class="brand-logo center">Shopping List</a>
        </div>
      </nav>
    </div>
    
    <div class="container mTop">
      <ShoppingList :products="products" @removeProduct="removeProduct($event)"></ShoppingList>
      <Form @newProduct="addProduct($event)" @removeLine="removeLine()"></Form>
    </div>

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
    }, removeLine() {
      if (this.products.length === 0) {
        Swal.fire({
          icon: 'info',
          title: 'Empty',
          text: 'There is no product to remove',
          confirmButtonColor: 'green'
        })
      } else {
        this.products.pop()
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
}

.mBtn {
  margin-left: 10px;
}

.mTop {
  margin-top: 60px;
}

</style>
