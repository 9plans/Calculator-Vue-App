<template>
  <div class="hello">
    <!-- <h1>{{ msg }}</h1> -->
    <b-row>
      <b-col class="SideNav">
        <h3 class="CalculatorHeading">
          Calculator App
        </h3>
      </b-col>
      <!-- Calculator Module -->
      <b-col cols="9">
        <div class="Calculator-Group">
          <!-- row 1 -->
          <div class="TextHeader">120</div>
          <div class="btn">D</div>
          <div class="btn">C</div>
          <div class="btn">%</div>
          <div class="btn">/</div>
          <!-- row 2 -->
          <div class="numbers btn">7</div>
          <div class="btn numbers">8</div>
          <div class="btn numbers">9</div>
          <div class="btn ">x</div>
          <!-- row 3 -->
          <div class="btn numbers">4</div>
          <div class="btn numbers">5</div>
          <div class="btn numbers">6</div>
          <div class="btn ">-</div>
          <!-- row 5 -->
          <div class="btn numbers">1</div>
          <div class="btn numbers">2</div>
          <div class="btn numbers">3</div>
          <div class="btn ">+</div>
          <!-- row 6 -->
          <div class="numbers zero btn ">0</div>
          <div class="btn">.</div>
          <div class="btn">=</div>
        </div>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      currentValue: ""
    };
  },
  methods: {
    clear() {}
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.SideNav {
  background-color: rgba(15, 23, 34, 1);
  height: 600px;
}
h3 {
  color: rgba(220, 220, 220, 1);
}
.CalculatorHeading {
  margin-top: 100px;
  text-align: center;
  font-family: Impact, Haettenschweiler, "Arial Narrow Bold", sans-serif;
}
.Calculator-Group {
  width: 300px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  /* grid-row: minmax(160px, 1fr); */
  grid-gap: 10px;
  margin: 100px auto;
}
.btn {
  background-color: rgb(53, 67, 87, 1);
  border-radius: 4px;
  color: rgba(220, 220, 220, 1);
  text-align: center;
  font-size: 25px;
  padding: 10px 10px;
}
.zero {
  grid-column: 1/3;
}
.numbers {
  font-weight: bold;
}
.TextHeader {
  grid-column: 1/5;
  text-align: right;
  color: rgba(220, 220, 220, 1);
  font-size: 30px;
  padding: 5px 10px;
  background-color: rgb(53, 67, 87, 0.2);
}
</style>
