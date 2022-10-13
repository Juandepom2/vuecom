<template>
  <h3>
    Total de proyectos: {{ numeroProyectos }}<!--lo escribiste mal ya que tiene que coincidir con lo que declaras en el scrip-->
   </h3>
<div class="table-responsive">
<table class="table table-dark table-hover">
<thead>
<tr>
<th>#</th>
<th>proyecto</th>
<th>tipo</th>
<th>urgente</th>
</tr>
</thead>

<tbody>
<tr v-for="(proyecto,index) in proyectos" :key="index">
<td>{{ index+1 }}</td>
<td>{{ proyecto.proyecto }}</td>
<td>{{proyecto.tipo }}</td>
<td @click="CambiarEstado(index)" :class="proyecto.urgente ? 
'bg-success' : 'bg-danger'">{{ proyecto.urgente ? "Si" : "No"}}</td>
<!-- <td @click="CambiarEstado(index)" :class="proyecto.completado ? -->
<!-- 'bg-success' : 'bg-danger'">{{ proyecto.completado ? "Completo" : "Incompleto"}}</td> -->
</tr>
</tbody>
</table>
</div>
</template> 
 
 <script>

    export default{
      props: ['numeroProyectos', 'proyectos', 'CambiarEstado'],
        } 
      </script>
      <style>
    </style>
