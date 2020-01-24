<template>
    
    <div id="ShoppingList">
        
        <table class="highlight centered responsive-table">
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
                  uds. = {{product.price}} €
              </td>
              <td>
                  <a class="btn-floating btn-large waves-effect waves-light red"><i class="material-icons">remove</i></a>
              </td>
          </tr>
        </tbody>

      </table>

    </div>

</template>

<script>
    
export default {
    name: 'ShoppingList',
    props: ['products']
}
    
</script>

<style scoped>

</style>