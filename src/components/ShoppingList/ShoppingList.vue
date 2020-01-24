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
                  {{product.name}}
              </td>
              <td>
                  {{product.price}} € x
              </td>

              <td>
                  uds. = {{product.price * product.quantity}} €
              </td>
              <td>
                  <a class="btn-floating btn-min green" @click="product.quantity += 1"><i class="material-icons">add</i></a>
                  <a class="btn-floating btn-min red mBtn" @click="product.quantity = removeItem(product)"><i class="material-icons">remove</i></a>
              </td>
          </tr>
        </tbody>

      </table>

      <div class="row">
          <span>Total expense: {{total}}</span>
      </div>

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

</style>