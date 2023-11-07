<template>
 
 <ul class="row searchResult py-4">
  <List v-for="v in lists" :key="v.id" :list="v" @@click="onClick"/>
 </ul>


</template>

<script>

//@@click >> v:on이 두번 쓰인 것. 자식이 클릭했을 때 라는 의미 

 import List from "./ListCp.vue";

 
 export default{
 
  name : "ListWrap",
  components : { List },
  props : ["lists"],
  methods : {
  
   onClick(v){
   
      this.$emit('@click' , v) //$emit -> 자식의 공간에 클릭을 시도할 수 있도록 구성 > 자식 컴포넌트에서 사용자지정 이벤트를 만들어 부모 컴포넌트에게 전달

    }
  } 
 
 
 }

</script>
