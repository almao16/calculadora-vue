<template>
  <div id="app">
    

    <article align="center">
      <img alt="Vue logo" src="./assets/logo.png" width="80px" height="80px" />
    <HelloWorld msg="Calculadora Vue.js" />
      <!-- numero 1 -->
      <label for="">Número 1: </label>
      <input type="number" v-model="numero1" name="" id="" required />
      <br>
      <br>

      <!-- numero 1 -->
      <label for="">Número 2: </label>
      <input type="number" v-model="numero2" name="" id="" required />
      <br>
      <br>

      <!-- Operacion-->
      <label for="">Operación: </label>
      <select v-model="operacionSelec" id="operacion">
        <option :value="{}" disabled hidden>Seleccione una operación</option>
        <option
          v-for="operacion in operaciones"
          :value="operacion"
          :key="operacion.id"
        >
          {{ operacion.nombre }}
        </option>
      </select>
      <br>
      <br>

      <!-- Respuesta  -->
      <label for="">Resultado: </label>
      <input type="number" v-model="resultado" name="" id="" disabled/>
      <br>
      <br>

      <!-- Boton Calcular -->
      <button @click="validarCampos()">Calcular</button>
      <br>
    </article>
<br>
    <TablaOperaciones :operaciones="operacionesRealizadas" />

  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import TablaOperaciones from "./components/TablaOperaciones.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
    TablaOperaciones,
  },
  data: () => ({
    numero1: "",
    numero2: "",
    resultado: "",
    operaciones: [
      { id: 1, nombre: "Suma" },
      { id: 2, nombre: "Resta" },
      { id: 3, nombre: "Multiplicación" },
      { id: 4, nombre: "División" },
    ],
    operacionSelec: {},
    operacionesRealizadas: [],
  }),
  methods: {
    realizarOperacion() {
      if (this.operacionSelec.id === 1) {
          this.resultado = Number(this.numero1) + Number(this.numero2);
        } else {
          if (this.operacionSelec.id === 2) {
            this.resultado = Number(this.numero1) - Number(this.numero2);
          } else {
            if (this.operacionSelec.id === 3) {
              this.resultado = Number(this.numero1) * Number(this.numero2);
            } else {
              this.resultado = Number(this.numero1) / Number(this.numero2);
            }
          }
        }
     
    },
    registrarOperaciones() {
      let operacion = "";
      switch (this.operacionSelec.id) {
        case 1:
          operacion = "Suma";
          break;
        case 2:
          operacion = "Resta";
          break;
        case 3:
          operacion = "Multiplicación";
          break;
        default:
          operacion = "División";
      }

      this.operacionesRealizadas.push({
        oper: operacion,
        num1: this.numero1,
        num2: this.numero2,
        result: this.resultado,
      });
    },
    validarCampos(){
      if (this.numero1 != "" && this.numero2 != "") {
        this.realizarOperacion();
        this.registrarOperaciones();
        // this.limpiarCampos();
      } else {
        alert("Debe llenar los 2 campos");
      }
    },
    limpiarCampos(){
      this.numero1 = '';
      this.numero2 = '';
      this.resultado = '';
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
  margin-top: 60px;
  display: flex;
  justify-content: space-around;
  padding: 50px;
  flex-wrap: wrap;
}

input {
  border-radius: 20px;
  background-color: rgb(59, 252, 123);
}

article {
  border-radius: 20px;
  background-color: rgb(78, 255, 231);
 
}

button {
  border-radius: 20px;
  font-size: 20px;
  font-family: sans-serif;
  background-color: rgb(62, 103, 236);
}

select {
  border-radius: 20px;
  font-size: 15px;
  background-color: rgb(59, 252, 123);
}

label {
  color: black;
}
</style>
