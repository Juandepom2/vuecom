<template>
    <div class="rom">
  <div class="col-6 col-md-6" >
  <h1>
      APP. proyectos
    </h1>
  </div>
  <div class="col-12 col-md-6" >
  
    <img width="100"  :src="url" :alt="des"> 
  </div></div>
  <hr>
</template> 
  <script>
    export default {
      data:() => ({
        url: "https://cdn.svgporn.com/logos/vue.svg",
        des: "vue.js",
         
      }),
    
    };
  </script> 
  
  