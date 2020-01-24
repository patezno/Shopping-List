<template>
  <div id="Form">
    <div class="row">
      <form class="col s12" @submit.prevent="onSubmit()">
        <div class="row">
          <div class="input-field col s6">
            <i class="material-icons prefix">add_shopping_cart</i>
            <input id="product" type="text" class="validate" v-model="product.name"/>
            <label for="product">Product</label>
          </div>
          <div class="input-field col s6">
            <i class="material-icons prefix">attach_money</i>
            <input id="price" type="number" class="validate" min="1" v-model.number="product.price"/>
            <label for="price">Price</label>
          </div>
          <div class="row">
            <button class="btn waves-effect blue" type="submit" name="action">
                Add
              <i class="material-icons right">add</i>
            </button>
            <button class="btn waves-effect red" type="button" name="action">
                Remove
              <i class="material-icons right">remove</i>
            </button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
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
        this.$emit('newProduct', this.product)
    },
  }
};
</script>

<style scoped></style>
