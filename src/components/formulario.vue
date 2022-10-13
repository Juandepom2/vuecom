 
  <template>
  <!--te falttaron cositas del formulario-->
 
         
      
   <div class="row">
    <div class="col-12 col-md-4">{{}}
      <h3 class="text-center">progreso{{porcentaje}}%</h3>
    <div class="progress" >
      <div class="progress-bar progress-bar-striped 
      progress-bar-animated bg-success" role ="progressbar"
      :aria-valuenow="porcentaje"
      aria-valuemin="0"
      aria-valuemax="100"
      :style=" 'width: $(porcentaje)%    '"
      >

      </div>
    </div>
      <form @submit.prevent="registroProyecto"> <!--lo escribiste mal ya que tiene que coincidir con lo que declaras en el scrip-->
        <div class="mb-3">
            <label class="form-label">Proyecto</label>
            <input v-model.trim="proyecto" type="text" class="form-control" required />
        </div>



  <div class="mb-3">
    <label  class="form-label"  >Actividad</label>
<select v-model.trin="tipo" class="form-select" required>
<option disabled selected value="">seleccione tipo de actividad....</option>
<option >aplicaciones web con vue.js</option>
<option  >backend service con node.js</option>
<option  >app movil con react native</option>

</select>
  </div>
  <br>
  <div class="mb-3">
    <input v-model.trin="urgente" type="checkbox" class="form-check-input" id="exampleCheck1">
    <label class="form-check-label" >Urgente</label>

  </div>
  <button type="submit" class="btn btn-primary">Guardar</button>
</form>
    </div>
    <div class="col-12 col-md-8" >
       <Totaldeproyecto :numeroProyectos="numeroProyectos"
        :proyectos="proyectos" :CambiarEstado="CambiarEstado"/>
    </div>

   </div >
  </template> 
  <script>
    import Totaldeproyecto from "./totaldeproyecto.vue";
  
    export default{
      data:()=> ({
        proyecto:"",
        tipo:"",
        urgentr:false,
    proyectos:[],
    numeroproyecto:0,
      }),
      methods:{
        registroProyecto(){
    const proyecto ={
    proyecto: this.proyecto,
    tipo: this.tipo,
    urgente:this.urgente,
    completado: false,   //te falto
    };
    this.proyectos.push(proyecto);
    this.proyecto="";
    this.tipo="";
    this.urgente=false;
        },
        CambiarEstado(id){ //va en mayusculas
    
          this.proyectos[id].urgente = !this.proyectos[id].urgente; //te falto
        }
      },
      computed:{
        numeroProyectos(){
          return this.proyectos.length;
        },
        porcentaje (){
          let completados =0;
          this.proyectos.map(proyecto =>{
            if (proyecto.completado) 
              completados++;
         
          } );
          return(completados * 100)/ this.numeroProyectos || 0;
        }
      },
      components:{Totaldeproyecto}
    };
    </script>