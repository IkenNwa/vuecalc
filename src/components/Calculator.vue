<script>
export default {
  name: 'Calculator',
    data() {
        return {
            prev: "",
            curr: "",
            operation: null,
            input: 0,
            total: false,
            calc: ""
        }
    },
    methods: {
        inputNum(e) {
            if (this.curr.includes(".") && e.target.innerText === ".") {
                {
                    this.input = ""
                    return
                }
            }
            if (this.total === true) {
                this.prev = ""
                this.curr = ""
            }
            if (this.curr) {
                this.curr = this.curr + e.target.innerText
            } else {
                this.curr = e.target.innerText
            }
            this.total = false

        },
        equals(e) {
            if (e?.target.innerText === ".") {
                this.total = true
            }
            switch (this.operation) {
                case "/":
                    this.calc = String(parseFloat(this.prev) / parseFloat(this.curr));
                    break;
                case "+":
                    this.calc = String(parseFloat(this.prev) + parseFloat(this.curr));
                    break;
                case "-":
                    this.calc = String(parseFloat(this.prev) - parseFloat(this.curr));
                    break;
                case "x":
                    this.calc = String(parseFloat(this.prev) * parseFloat(this.curr));
                    break;
                default:
                    return;
            }
            this.input = this.calc
            this.prev = this.prev + " " + this.operation + " " + this.curr
            this.curr = this.calc
            this.operation = null
        },
        clear() {
            if (this.curr === "") {
                this.prev = this.prev.substring(0, this.curr.length - 1)
            } else {
                this.curr = this.curr.substring(0, this.curr.length - 1)
            }
        },
        negative() {
            this.curr = -this.curr
        },
        operator(e) {
            this.total = false
            this.operation = e.target.innerText;
            if (this.curr === "") {
                return;
            }
            if (this.prev !== "") {
                this.equals
            }
            this.prev = this.curr
            this.curr = ""
        },
        reset() {
            this.prev = ""
            this.curr = ""
            this.operation = null
            this.inpu = 0
            this.total = false
        }
    },
}

</script>
<template>
    <div class="container">
        <h2 class="title">IKENNAM</h2>
        <div class="screen">
            <div class="prev">{{ prev }}</div>
            <div class="input">{{ curr }}</div>
        </div>
        <div class="buttons">
            <div class="button-row">
                <button @click="reset">CE</button>
                <button @click="clear">C</button>
                <button @click="negative">+/-</button>
                <button @click="operator">/</button>
            </div>
            <div class="button-row">
                <button @click="inputNum">7</button>
                <button @click="inputNum">8</button>
                <button @click="inputNum">9</button>
                <button @click="operator">-</button>
            </div>
            <div class="button-row">
                <button @click="inputNum">4</button>
                <button @click="inputNum">5</button>
                <button @click="inputNum">6</button>
                <button @click="operator">+</button>
            </div>
            <div class="button-row">
                <button @click="inputNum">1</button>
                <button @click="inputNum">2</button>
                <button @click="inputNum">3</button>
                <button @click="operator">x</button>
            </div>
            <div class="button-row">
                <button @click="inputNum
                ">0</button>
                <button @click="inputNum">.</button>
                <button class="equals" @click="equals">=</button>
            </div>
        </div>
        <small>This is a Vue Calculator by Ikenna Nwachukwu</small>
    </div>

</template>

<style scoped>
.container {
    width: 300px;
    border: 1px solid #282a4b;
    padding: 1em;
    border-radius: 20px;
    background-color: white;
    /* box-shadow: 0px 10px 5px #282a4b66; */
}

.title {
    font-weight: 100;
}

small {
    font-weight: 100;
    font-size: 12.5px;
}

.screen {
    background-color: white;
    border: 1px solid #282a4b;
    border-radius: 10px;
    height: 120px;
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    justify-content: center;
    padding: 10px;
    color: #282a4b;
    margin-block: 10px;
}

.prev {
    font-size: 20px;
    font-weight: 100;
}

.input {
    font-size: 38px;
    display: flex;
    align-items: center;
    height: 67px;
    font-weight: 100;
}

.button-row {
    display: flex;
    flex-direction: row;
}

button {
    height: 40px;
    width: 100%;
    margin: 1.5px;
    background-color: white;
    border: 1px solid #282a4b;
    border-radius: 10px;
    cursor: pointer;
}

button:hover {
    background-color: #e6e7fc;
}

button:active {
    background-color: #282a4b;
    color: white;
}

.equals {
    width: 210%;
}
</style>
