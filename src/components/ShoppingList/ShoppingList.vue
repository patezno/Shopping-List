<template>
    
    <div id="ShoppingList">
        
        <table class="highlight centered responsive-table row">
        <thead>
          <tr>
              <th>Name</th>
              <th>Price per unit</th>
              <th>Total Price</th>
              <th>Operations</th>
          </tr>
        </thead>

        <tbody>
          <tr v-for="product in products" :key="product.name">
              <td>
                  <span v-bind:class="{'colorRed': product.price < 10}">
                      {{product.name}}
                  </span>
              </td>
              <td>
                  <span v-bind:class="{'colorRed': product.price < 10}">
                      {{product.price}} € x
                  </span>
              </td>

              <td>
                  <span v-bind:class="{'colorRed': product.price < 10}">
                      {{product.quantity}} unit/s = {{product.price * product.quantity}} €
                  </span>
              </td>
              <td>
                  <a class="btn-floating btn-min green" @click="product.quantity += 1"><i class="material-icons">add</i></a>
                  <a class="btn-floating btn-min red mBtn" @click="product.quantity = removeItem(product)"><i class="material-icons">remove</i></a>
              </td>
          </tr>
        </tbody>

      </table>

    </div>

</template>

<script>
    
export default {
    name: 'ShoppingList',
    props: ['products'],
    data() {
        return {
            total: null
        }
    },
    methods: {
        removeItem(product) {
            if (product.quantity === 1) {
                this.$emit('removeProduct', product)
            } else {
                return product.quantity - 1
            }
        }
    }
}

</script>

<style scoped>

.colorRed {
    color: red !important;
}

</style>