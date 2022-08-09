<template>
  <div class="">
   <article>
     <table class="default" align="center">
      <tr>
        <th>Operación</th>
        <th>Número 1</th>
        <th>Número 2</th>
        <th>Respuesta</th>
      </tr>

      
        <tr>
                          
 
                            <td>{{this.operaciones.i}}</td>
                            <td>{{item.cantidadc}}</td>
                            <td>{{item.precioc}}</td>
                            <td>{{item.cantidadc*item.precioc}}</td>
  </tr>
      
    </table>
   </article>
  </div>
</template>

<script>
export default {
  name: "TablaOperaciones",
  props: {
    operaciones: [{
      operacion : '',
      num1 : '',
      num2 : '',
      

    }
    ]
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
table {
  background-color: rgb(30, 233, 206);
  color: black;
}


</style>
