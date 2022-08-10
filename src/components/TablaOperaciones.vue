<template>
  <div class="">
    <br>
     <br>
       <br>
      <strong><label>Lista de Resultados</label></strong>
       <br>
       <br>
     <table class="default" align="center">
      <thead>
         <th>Operación</th>
        <th>Número 1</th>
        <th>Número 2</th>
        <th>Respuesta</th>
      </thead>
    
       <tbody  v-for="operacion in operaciones"
          :value="operacion"
          :key="operacion.id"> 
        <th>{{operacion.oper}}</th>
        <th>{{operacion.num1}}</th>
        <th>{{operacion.num2}}</th>
        <th>{{operacion.result}}</th>
        </tbody>          
  
    </table>
    
   
  </div>
</template>

<script>
export default {
  name: "TablaOperaciones",
  props: {
    operaciones: []
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
thead {
  background-color: rgb(59, 252, 123);
  color: black;
}


tbody {
  background-color: rgb(204, 123, 224);
  color: black;
}

div{
   border-radius: 20px;
  background-color: rgb(92, 185, 173);

}
label{
  color: black;
}
</style>
