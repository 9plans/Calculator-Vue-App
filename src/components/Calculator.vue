<template>
  <div class="hello">
    <!-- <h1>{{ msg }}</h1> -->
    <b-row>
      <b-col class="SideNav">
        <h3 class="CalculatorHeading">
          Calculator App
          <br />
          Vue Js
        </h3>
      </b-col>
      <!-- Calculator Module -->
      <b-col cols="9">
        <div class="Calculator-Group">
          <!-- row 1 -->
          <div class="TextHeader">
            {{ currentValue || 0 }}
            <sup>{{ operatorSymbol }}</sup>
          </div>
          <div @click="clear()" class="btn">AC</div>
          <div @click="SignValue()" class="btn">+/-</div>
          <div @click="Delete()" class="btn">DEL</div>
          <div @click="Division()" class="btn Operators">/</div>
          <!-- row 2 -->
          <div @click="Append('7')" class="numbers btn">7</div>
          <div @click="Append('8')" class="btn numbers">8</div>
          <div @click="Append('9')" class="btn numbers">9</div>
          <div @click="Multiplication()" class="btn Operators">x</div>
          <!-- row 3 -->
          <div @click="Append('4')" class="btn numbers">4</div>
          <div @click="Append('5')" class="btn numbers">5</div>
          <div @click="Append('6')" class="btn numbers">6</div>
          <div @click="Subtraction()" class="btn Operators">-</div>
          <!-- row 5 -->
          <div @click="Append('1')" class="btn numbers">1</div>
          <div @click="Append('2')" class="btn numbers">2</div>
          <div @click="Append('3')" class="btn numbers">3</div>
          <div @click="Addition()" class="btn Operators">+</div>
          <!-- row 6 -->
          <div @click="Append('0')" class="numbers zero btn ">0</div>
          <div @click="DecimalPoint('.')" class="btn">.</div>
          <div @click="Equal()" class="btn Operators">=</div>
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
      currentValue: "",
      previousValue: "",
      operatorClicked: false,
      operatorAction: null,
      operatorSymbol: "+"
    };
  },
  methods: {
    // ================================================ Extras======================
    clear() {
      this.currentValue = "";
      this.operatorClicked = false;
      this.operatorAction = null;
      this.operatorSymbol = "+";
      this.previousValue = "";
    },
    Append(newValue) {
      if (this.operatorClicked) {
        this.operatorClicked = false;
        this.currentValue = "";
      }

      this.currentValue =
        this.currentValue === "0"
          ? (this.currentValue = `${this.currentValue.slice(1)}${
              this.newValue
            }`)
          : `${this.currentValue}${newValue}`;
    },
    DecimalPoint(newValue) {
      this.currentValue =
        this.currentValue.indexOf(".") === -1
          ? `${this.currentValue}${newValue}`
          : this.currentValue;
    },
    Delete() {
      this.currentValue = this.currentValue
        ? this.currentValue.slice(0, -1)
        : this.currentValue;
    },
    SignValue() {
      this.currentValue =
        this.currentValue.indexOf("-") === -1
          ? `-${this.currentValue}`
          : this.currentValue.slice(1);
    },
    // ======================= Operators========================================
    Addition() {
      this.operatorAction = (previousVal, newValue) => previousVal + newValue;
      this.OnOperatorClick();
      this.operatorSymbol = "+";
      Equal();
    },
    Subtraction() {
      this.operatorAction = (previousVal, newValue) => previousVal - newValue;
      this.OnOperatorClick();
      this.operatorSymbol = "-";
    },
    Multiplication() {
      this.operatorAction = (previousVal, newValue) => previousVal * newValue;
      this.OnOperatorClick();
      this.operatorSymbol = "x";
    },
    Division() {
      this.operatorAction = (previousVal, newValue) => previousVal / newValue;
      this.OnOperatorClick();
      this.operatorSymbol = "/";
    },
    OnOperatorClick() {
      this.previousValue = this.currentValue;
      // this.currentValue = "";
      this.operatorClicked = true;
      console.log("operator clicked");
    },
    Equal() {
      if (this.previousValue)
        this.currentValue = `${this.operatorAction(
          parseFloat(this.previousValue),
          parseFloat(this.currentValue)
        )}`;
      this.previousValue = "";
    }
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
.btn:active {
  background-color: rgb(108, 99, 255, 1);
}
.btn:hover {
  box-shadow: 1px 1px 3px rgba(108, 99, 255, 1);
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
  overflow: hidden;
}
.Operators {
  background-color: rgb(108, 99, 255, 1);
}
sup {
  vertical-align: super;
  font-size: 15px;
}
</style>
