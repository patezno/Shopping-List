<template>
  
  <div id="Form">
    <div class="row">
      
      <form class="col s12" @submit.prevent="onSubmit()">
        <div class="row">
          
          <div class="input-field col s12 m6 l4 offset-l2">
            <i class="material-icons prefix">add_shopping_cart</i>
            <input id="product" type="text" class="validate" v-model="product.name"/>
            <label for="product">Product</label>
          </div>

          <div class="input-field col s12 m6 l2 offset-l1">
            <i class="material-icons prefix">attach_money</i>
            <input id="price" type="number" class="validate" min="1" v-model.number="product.price"/>
            <label for="price">Price</label>
          </div>

        </div>

          <div class="row">
            <button class="btn green" type="submit" name="action">
                Add
              <i class="material-icons right">add</i>
            </button>
            <button class="btn red mBtn" type="button" name="action" @click="$emit('removeLine')">
                Remove
              <i class="material-icons right">remove</i>
            </button>
          </div>
        
      </form>

    </div>
  </div>

</template>

<script>

import Swal from 'sweetalert2'

export default {
  name: "Form", 
  data() {
      return {
          product: {
              name: null,
              price: null
          }
      }
  }, 
  methods: {
    onSubmit() {
      if (!this.product.name || !this.product.price) {
        Swal.fire({
          icon: 'warning',
          title: 'Warning',
          text: 'Some information is missing, check it again',
          confirmButtonText: 'Retry',
          confirmButtonColor: 'green'
        })
        return
      }
      let element = this.createNewElement(this.product.name, this.product.price);
      this.$emit('newProduct', element)
    }, 
    createNewElement(product, price) {
        let newElement = {
            name: product, 
            price: price,
            quantity: 1
        }
        return newElement
    }
  }
};

</script>

<style scoped></style>
