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
  methods: {
    async getQuote() {
      this.quote = "( getting fact . . . )";
      const res = await fetch("https://api.chucknorris.io/jokes/random");
      const resJson = await res.json();
      this.quote = resJson.value;
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
  width: 100%;
  overflow: hidden;
  background-image: url("~/karate.png");
  background-position: 0px 0px;
  background-repeat: repeat-x repeat-y;

  animation: animatedBackground 40s linear infinite;
}
.quote {
  display: inline-block;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translateX(-50%) translateY(-50%);
  width: 90%;
  overflow: hidden;
  cursor: pointer;
  &:hover {
    color: red;
  }
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
