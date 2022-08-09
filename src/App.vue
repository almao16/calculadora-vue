<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" width="80px" height="80px" />
    <HelloWorld msg="Calculadora Vue.js" />

    <article>
      <!-- numero 1 -->
      <label for="">Número 1: </label>
      <input type="number" v-model="numero1" name="" id="" required />
      <br />
      <br />

      <!-- numero 1 -->
      <label for="">Número 2: </label>
      <input type="number" v-model="numero2" name="" id="" required />
      <br />
      <br />

      <!-- Operacion-->
      <label for="">Operación: </label>
      <select  v-model="operacionSelec" id="operacion">
        <option
          v-for="operacion in operaciones"
          :value="operacion"
          :key="operacion.id"
        >
          {{ operacion.nombre }}
        </option>
      </select>
      <br />
      <br />

       
      <!-- Respuesta  -->
      <label for="">Resultado: </label>
      <input type="number" v-model="resultado" name="" id="" />
      <br />
      <br />

      <!-- Boton Calcular -->
      <button  @click="realizarOperacion()">Calcular</button>
      <br />
      <br />
    </article>

    <TablaOperaciones operaciones="operacionesRealizadas"/>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import TablaOperaciones from './components/TablaOperaciones.vue';

export default {
  name: "App",
  components: {
    HelloWorld,
    TablaOperaciones,
  },
   data: () =>({
    numero1: '',
    numero2: '',
    resultado: '',
    operaciones: [
      { id: 1, nombre: 'Suma'},
      { id: 2, nombre: 'Resta'},
      { id: 3, nombre: 'Multiplicación'},
      { id: 4, nombre: 'División'},
    ],
    operacionSelec: {},
    operacionesRealizadas: []

  }),
  methods: {

    realizarOperacion(){
             if(this.operacionSelec.id === 1){
          this.resultado = Number(this.numero1) + Number(this.numero2);
       }
       else {
        if(this.operacionSelec.id === 2){
          this.resultado =  Number(this.numero1) -  Number(this.numero2);
          }else{
            if(this.operacionSelec.id === 3){
          this.resultado =  Number(this.numero1) *  Number(this.numero2);
            }
            else{
          this.resultado =  Number(this.numero1) /  Number(this.numero2);
              }
          }
       }
    

       let operacion =''
      switch(this.operacionSelec.id)
      {
        case 1:
          operacion = "Suma"
          break;
          case 2:
             operacion = "Resta"
          break;
          case 3:
             operacion = "Multiplicación"
          break;
          default:
             operacion = "División"
      }

      this.operacionesRealizadas.push(operacion,this.numero1,this.numero2,this.resultado);
    },

    
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
