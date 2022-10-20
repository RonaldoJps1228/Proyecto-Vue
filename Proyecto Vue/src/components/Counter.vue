<template>
  <h2>{{ customTitle }}</h2>
  <p> {{ counter }} <sup>2</sup> = {{ squareCounter }} </p>

  <div>
    <button @click="getIncrease">+1</button>
    <button @click="getDecrease">-1</button>
  </div>

</template>

<script>

export default {
    // props : ['title'],
    // name: 'Counter'
    props: { // Properties es util para las validaciones
      title: String,
      start: {
          type: Number,
          default: 100,
          // required: true
          validator(value) {
            return value >= 100
          }
      }
    },
    data() {
        return {
        // counter: 5 // Contador
        counter: this.start
        }
    },
    methods: {
      getSquareValue() {
        return this.counter * this.counter
      },
      getIncrease() {
        this.counter++
      },
      getDecrease() {
        this.counter--
      }
    },
    computed: { //Metodos computarizadas
      squareCounter() {
        return this.counter * this.counter
      },
      customTitle() {
        return this.title || 'Counter'
      }
    }
}
</script>

<style>
button{
  background-color: rgb(196, 78, 38);
  border-radius: 5px;
  border: 1px solid white;
  color: blue;
  cursor: pointer;
  margin: auto;
  padding: 5px 15px;
  transition: 0.3s ease-in-out;

}

button:hover{
  background-color: aquamarine;
  transition: 0.3s ease-in-out;
}

</style>