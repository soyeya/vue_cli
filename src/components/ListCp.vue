<template>
  
  <!--해당 상품 리스트만 구축 -->

   <li class="col-6 col-sm col-md-4" >
    <div class="wrap">
        <img @click=onClick :src="list.src" :alt="list.title" class="w-100">
        <h2>{{list.title}}</h2>
    </div>
   </li>
</template>

<script>
 
  export default{
  
     name : "List",
     props : ["list"],
     methods : {
     
      onClick(e){
      
         this.$emit("@click", {src : e.target.src, title:e.target.alt});

         }
      }
  }
</script>