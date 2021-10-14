<script>
  import Navbar from "./Navbar.svelte";
  let firstNum = [];
  let secondNum = [];
  let sum = 0;
  let isAddClicked = false;
  const addToFirst = (val) => (firstNum = [...firstNum, val]);
  const addToSecond = (val) => (secondNum = [...secondNum, val]);
  const calculate = () =>
    float32(firstNum, toString()) + float32(secondNum.toString());
  const appendNum = (val) => {
    if (!!isAddClicked) {
      addToFirst(val);
    } else {
      addToSecond(val);
    }
  };

</script>

<Navbar />
<main>
  <div class="calculator-grid">
    <div class="output">
      <div class="previous-operand">{firstNum.toString()}</div>
      <div class="current-operand">{secondNum.toString()}</div>
    </div>
    <button class="span-two">AC</button>
    <button>DEL</button>
    <button on:click={() => appendNum(1)}>1</button>
    <button on:click={() => appendNum(2)}>2</button>
    <button on:click={() => appendNum(3)}>3</button>
    <button on:click={() => appendNum(4)}>4</button>
    <button on:click={() => appendNum(5)}>5</button>
    <button on:click={() => appendNum(6)}>6</button>
    <button on:click={(isAddClicked = false)}>+</button>
    <button on:click={() => appendNum(7)}>7</button>
    <button on:click={() => appendNum(8)}>8</button>
    <button on:click={() => appendNum(9)}>9</button>
    <button>.</button>
    <button on:click={() => appendNum(0)}>0</button>
    <button on:click={() => calculate()} class="span-two">=</button>
  </div>
</main>

<style>
  *,
  *::before,
  *::after {
    box-sizing: border-box;
    font-family: Gotham Rounded, sans-serif;
    font-weight: normal;
  }
  main {
    margin: 0;
    padding: 0;
    background: linear-gradient(to right, #cbce91ff, #ea738dff);
  }
  .calculator-grid {
    display: grid;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    grid-template-columns: repeat(4, 100px);
    grid-template-rows: minmax(120px, auto) repeat(5, 100px);
  }
  .calculator-grid > button {
    cursor: pointer;
    font-size: 2rem;
    border: 1px, solid #ffffff;
    outline: none;
    background-color: rbga(255, 255, 255, 0.75);
  }

  .calculator-grid > button:hover {
    background-color: #a9a9a9;
  }
  *,
  *::before,
  *::after {
    box-sizing: border-box;
    font-family: Gotham Rounded, sans-serif;
    font-weight: normal;
  }

  body {
    margin: 0;
    padding: 0;
    background: linear-gradient(to right, #cbce91ff, #ea738dff);
  }

  .calculator-grid {
    display: grid;
    justify-content: center;
    align-content: center;
    min-height: 100vh;
    grid-template-columns: repeat(4, 100px);
    grid-template-rows: minmax(120px, auto) repeat(5, 100px);
  }

  .calculator-grid > button {
    cursor: pointer;
    font-size: 2rem;
    border: 1px, solid #ffffff;
    outline: none;
    background-color: rbga(255, 255, 255, 0.75);
  }

  .calculator-grid > button:hover {
    background-color: #a9a9a9;
  }

  .span-two {
    grid-column: span 2;
    color: #adf802;
    background-color: rgba(139, 0, 139, 0.8);
  }

  .output {
    grid-column: 1 / -1;
    background-color: rgba(0, 0, 0, 0.75);
    display: flex;
    align-items: flex-end;
    justify-content: space-around;
    flex-direction: column;
    padding: 10px;
    word-wrap: break-word;
    word-break: break-all;
  }

  .output .previous-operand {
    color: rgba(255, 255, 255, 0.75);
    font-size: 1.5rem;
  }

  .output .current-operand {
    color: white;
    font-size: 2.5rem;
  }
</style>
