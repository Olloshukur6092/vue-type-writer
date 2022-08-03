<template>
  <div class="container">
    <div class="row">
      <div class="col-md-6 offset-md-3">
        <div class="card shadow mt-3">
          <div class="card-header bg-success text-white text-center">
            <h2>Write...!!!</h2>
          </div>
          <div class="card-body">
            <div class="textDiv bg-secondary text-center text-white py-2 mb-2">
              <h3>{{ word }}</h3>
            </div>
            <div class="mb-2">
              <strong>Score:{{ score }}</strong>
            </div>
            <div class="mb-2">
              <strong>Time:{{ t }}</strong>
            </div>
            <form @submit.prevent="typeWriter">
              <input
                type="text"
                class="form-control py-2 px-3"
                placeholder="write..."
                v-model="inputtext"
              />
              <input
                type="submit"
                value="Submit ->"
                class="btn btn-primary mt-4 w-100"
              />
            </form>
            <!-- <div class="errorText bg-danger text-center text-white py-2 mt-2">
                <span>Sizda notogri urinish qildingiz</span>
              </div> -->
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FormWriter",
  props: {
      word: String,
      score: Number,
      t: Number,
      typeWriter: { type: Function }
  }
};
</script>

<style>
</style>