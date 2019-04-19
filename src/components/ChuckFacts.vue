<template>
  <div class="container">
    <div class="quote" @click="getQuote">
      <h2>{{ quote }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      quote: "CLICK FOR A CHUCK FACT"
    };
  },
  computed: {},
  methods: {
    async getQuote() {
      this.quote = "( getting fact . . . )";
      let self = this;
      fetch("https://api.chucknorris.io/jokes/random").then(function(response) {
        response.json().then(function(res) {
          self.quote = res.value;
        });
      });
    }
  }
};
</script>

<style lang="scss" scoped>
h2 {
  font-family: "Quicksand", Helvetica, sans-serif;
  font-weight: 500;
  font-size: 2.5em;
  line-height: 120%;
  @media screen and (min-width: 600px) {
    font-size: 4em;
  }
}
.container {
  text-align: center;
  position: relative;
  height: 100vh;
  width: 100vw;
  background-image: url("~/karate.png");
  background-position: 0px 0px;
  background-repeat: repeat-x repeat-y;

  animation: animatedBackground 40s linear infinite;
}
.quote {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translateX(-50%) translateY(-50%);
  width: 90%;
  margin: 0 auto;
  cursor: pointer;
  &:hover {
    color: red;
  }
  overflow-y: scroll;
}

@keyframes animatedBackground {
  from {
    background-position: 0 0;
  }
  to {
    background-position: 0 100%;
  }
}
</style>