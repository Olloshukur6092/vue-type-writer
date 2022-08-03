<template>
  <div class="container my-4">
    <div class="row">
      <div class="col-md-6">
        <div class="card shadow">
          <div class="card-header text-center bg-info text-white">
            <h4>Add Product</h4>
          </div>
          <div class="card-body">
            <form @submit.prevent="addProduct">
              <div class="mb-3">
                <input
                  type="text"
                  class="form-control"
                  placeholder="Enter product name..."
                  v-model="product"
                />
              </div>
              <div class="mb-3">
                <input
                  type="number"
                  class="form-control"
                  placeholder="Enter product price..."
                  v-model="price"
                />
              </div>
              <div class="mb-3">
                <input
                  type="submit"
                  class="btn btn-success px-4 py-3"
                  value="Add Product ->"
                />
              </div>
            </form>
          </div>
        </div>
      </div>
      <div class="col-md-6">
        <div class="card">
          <div class="card-header text-center bg-primary text-white">
            <h4>All Products  {{count}}</h4>
          </div>
          <div class="card-body">
            <div>
              <ul
                class="list-group"
                v-for="product in products"
                :key="product.price"
              >
                <li class="list-group-item">
                  <strong>{{ product.product }}:</strong> &nbsp;
                  {{ product.price }} so'm
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TheForm",
  data() {
    return {
      count: 0,
      products: [],
    };
  },
  methods: {
    addProduct() {
        this.count = this.count + 1
      this.products = [...this.products,
        { product: this.product, price: this.price },
        
      ];
      console.log(this.products);
      this.product = "";
      this.price = "";
    },
  },
};
</script>

<style>
</style>