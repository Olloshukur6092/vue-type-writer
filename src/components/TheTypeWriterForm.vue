<template>
  <TheHeader />
  <section>
    <div class="container">
      <div class="row">
        <div class="col-md-6 offset-md-3">
          <div class="card shadow mt-3" v-if="card_1">
            <div class="card-header bg-success text-white text-center">
              <h2>Type Write...!!!</h2>
            </div>
            <div class="card-body">
              <div class="textDiv text-center py-2 mb-2">
                <h3>{{ word }}</h3>
              </div>
              <div class="d-flex justify-content-center my-3">
                <h3 class="me-3">Score:{{ score }}</h3>
                <h3 class="ms-3">Time:{{ t }}</h3>
              </div>
              <form @submit.prevent="typeWriter">
                <input
                  type="text"
                  class="form-control py-2 px-3 mb-2"
                  placeholder="write..."
                  v-model="input"
                  autofocus
                />
                <small>{{error}}</small>
                <input
                  type="submit"
                  value="Submit ->"
                  class="btn btn-primary mt-4 w-100"
                />
              </form>
            </div>
          </div>
          <div class="card shadow border-0 mt-5" v-if="card_2">
            <div class="card-header bg-success text-center text-white">
              <h4>This is Result</h4>
            </div>
            <div class="card-body my-2 text-center">
              <h4><strong>Score:</strong><span>{{ score }}</span></h4>
              <p
                class="mt-2 result"
                :class="[
                  score < 5
                    ? 'text-danger'
                    : score < 20
                    ? 'text-warning'
                    : 'text-success',
                ]"
              >
                {{ message }}
              </p>
              <div class="">
                <button
                  class="btn btn-outline-primary px-3 py-2 me-3"
                  @click="restart()"
                >
                  Restart
                </button>
                <button
                  class="btn btn-outline-danger px-3 py-2 ms-3 me-3"
                  @click="closePage()"
                >
                  Close Page
                </button>
                <button class="btn btn-outline-info px-3 py-2 ms-3" @click="getHome" >Home Page</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { rand } from './containers/random'
import TheHeader from "@/layouts/TheHeader";

export default {
  name: "TheTypeWriterForm",
  components: {TheHeader},
  props: {
    getHome: {type: Function}
  },
  data() {
    return {
      input: "",
      words: rand,
      word: "",
      score: 0,
      t: 10,
      interval: "",
      card_1: true,
      card_2: false,
      message: "",
      error: "",
    };
  },
  mounted() {
    this.getRandom();
    this.startTime();
  },
  methods: {
    typeWriter() {
      if (this.input === this.word) {
        this.score++;
        this.getRandom();
        this.input = "";
        this.t = 10;
        this.error = ""
      } else {
        this.error = "Error!, this is word...";
      }
    },

    getRandom() {
      let rand = Math.floor(Math.random() * this.words.length);
      this.word = this.words[rand];
    },
    startTime() {
      this.interval = setInterval(() => {
        this.t--;
        if (this.t === 0) {
          this.stopTime();
          this.resultPage();
        }
      }, 1000);
    },
    stopTime() {
      clearInterval(this.interval);
    },

    resultPage() {
      this.card_1 = !this.card_1;
      this.card_2 = !this.card_2;
      if (this.score < 5) {
        this.message = "Your result is bad!";
      } else if (this.score < 20) {
        this.message = "Your result is middle!";
      } else {
        this.message = "Your result is good!";
      }
    },
    restart() {
      this.card_1 = !this.card_1;
      this.card_2 = !this.card_2;
      this.t = 10;
      this.score = 0;
      this.startTime();
      this.input = "";
      this.error = "";
    },

    closePage() {
      window.close();
    },
  },
};
</script>

<style scoped>

.textDiv h3 {
  font-size: 35px;
  font-weight: 500;
  font-family: sans-serif;
  text-shadow: 2px 3px 2px rgba(0, 0, 0, 0.2);
}

.card-body .result {
  font-size: 22px;
}

.card-body strong {
  font-size: 29px !important;
}

.btn {
  font-size: 20px;
}
/* Error style */
form small {
  color: #d70707;
  font-family: sans-serif;
  font-size: 15px;
}

</style>