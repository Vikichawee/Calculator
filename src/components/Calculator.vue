<template>
    
    <div :class="`containter`">
    
    <div :class="`buttonsDiv`">
        
    
    <div>
        <div :class="'border'">
        <div :class="`Secondscreen`">{{ secondScreen }}</div>
        <div :class="`screen`">{{ screen }}</div>
        </div>
        <button @click="c()">C</button>
        <button @click="clear()">AC</button>
        
        <button @click="divide()">/</button>
        <button @click="substract()">-</button>
    </div>
        
    <div>
        <button @click="appendToScreen(1)">1</button>
        <button @click="appendToScreen(2)">2</button>
        <button @click="appendToScreen(3)">3</button>
        <button @click="multiply()">*</button>
    </div>
        <button @click="appendToScreen(4)">4</button>
        <button @click="appendToScreen(5)">5</button>
        <button @click="appendToScreen(6)">6</button>
        <button @click="plus()">+</button>
    <div>
        <button @click="appendToScreen(7)">7</button>
        <button @click="appendToScreen(8)">8</button>
        <button @click="appendToScreen(9)">9</button>
        <button @click="operate(); deleteEverything();">=</button>
    </div>
    <button @click="appendToScreen(0)">0</button>

    </div>
    </div>

</template>

<script>


    export default{
        name: `Calculator`,
        data(){
            return{
                screen: '',
                firstNumber: 0,
                operator: '',
                counter: 0,
                counter1: 0,
                secondScreen: ''
            }
        },
        methods: {
            appendToScreen(button){
                this.screen+=button;
            },
            clear(){
                this.screen = ''
                this.secondScreen = ''
                this.firstNumber = 0
                this.counter = 0
            },
            plus(){
                
                if (this.counter >= 1) {
                    this.operate('plus',this.firstNumber, Number(this.screen))
                    this.counter = 0
                }
                this.firstNumber = Number(this.screen)
                this.secondScreen = this.screen + `+`
                this.screen = ''
                this.operator = 'plus'
                this.counter++
            },
            
            divide(){
                if (this.counter >= 1) {
                    this.operate('divide',this.firstNumber, Number(this.screen))
                    this.counter = 0
                }
                this.firstNumber = Number(this.screen)
                this.secondScreen = this.screen + `/`
                this.screen = ''
                this.operator = 'divide'
                this.counter++
            },
            multiply(){
                if (this.counter >= 1) {
                    this.operate('multiply',this.firstNumber, Number(this.screen))
                    this.counter = 0
                }
                this.firstNumber = Number(this.screen)
                this.secondScreen = this.screen + `*`
                this.screen = ''
                this.operator = 'multiply'
                this.counter++
            },
            substract(){
                if (this.counter >= 1) {
                    this.operate('substract',this.firstNumber, Number(this.screen))
                    this.counter = 0
                }
                this.firstNumber = Number(this.screen)
                this.secondScreen = this.screen + `-`
                this.screen = ''
                this.operator = 'substract'
                this.counter++
            },
            operate(sign,num1,num2){
                this.secondScreen = ''
                sign = this.operator
                num1 = this.firstNumber
                num2 = Number(this.screen)
                if(sign === 'plus'){
                    this.screen = num1 + num2
                }
                if(sign === 'divide'){
                    this.screen = num1 / num2
                }
                if(sign === 'multiply'){
                    this.screen = num1 * num2
                }
                if(sign === 'substract'){
                    this.screen = num1 - num2
                }

                
            },
            deleteEverything(){
                this.firstNumber = 0
                this.counter = 0
            },
            c(){
                this.screen = this.screen.slice(0 ,-1)
            }


        },
        computed: {
            
        }
    }
</script>

<style scoped>
    button{
        width: 100px;
        height: 50px;
        margin: 2px;
        background-color:beige
    }
    .Secondscreen{
        font-size: 19px;
        display: flex;
        justify-content: end;
        align-items: center;
        
        margin: 10px;
        height: 30px;
    }
    
    .screen{
        font-size: 30px;
        font-weight: bold;
        display: flex;
        align-items: center;
        justify-content: end;
        
        margin: 10px;
        height: 30px;
    }
    .buttonsDiv{
        border: 4px solid black;
        background-color: bisque;
        padding: 10px;
    }
    .containter{
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .border{
        border: 2px solid lightcoral;
        background-color: antiquewhite;
        margin: 10px;
    }
    

    
    

</style>