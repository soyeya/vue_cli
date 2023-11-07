<template>
 <div class="container my-3" id="app">
  <Title :title="mainTitle"  />
  <Search @@change ="onChangeQuery" />
  <ListWrap @@click ="onChangeList" :lists="searchFoods" /> 
 </div>
</template>

  <script>
   // async ~ await 비동기 처리방식 : 예약어 -> 정보를 일정한 속도로 보낼 것을 요구하지 않는 데이터 전송 방법이다.

   import axios from "axios" ; //비동기 처리 방식(검색어를 눌렀을 때 바로 호출하는 방식)
   import Title from "./components/TitleCp.vue";
   import Search from "./components/SearchCp.vue";
   import ListWrap from "./components/ListWrapCp.vue";
   import Modal from "./components/ModalCp.vue";


   export default {

      name : "App",
      components : {

       Title , 
       Search,
       ListWrap,
       Modal

   },

   data(){

      return {
      
            mainTitle : "Food House",
            foods : [],
            food : {},
            searchFoods : []
       }
     },

      async created(){

        const {data} = await axios.get("/json/Food.json");
        console.log(data);
        this.foods = data;
        console.log(this.foods);
        this.searchFoods = data;
        
      },

      methods : {
      
      onChangeQuery(query){
       
        console.log(query);
        this.searchFoods = this.foods.filter((v) => {
        console.log(v);
          const result = v.title.toLowerCase().includes(query.toLowerCase()) || v.description.toLowerCase().includes(query.toLowerCase()) || v.price.toLowerCase().includes(query.toLowerCase());

           return result;

        })

      },

      onChangeList(w){
      
         console.log(w);
         this.food = w;
         this.isSelected = true;

      }
      
      }

  }

  </script>

<style>

 #app{
 
  font-family:Arial, sans-serif;
  text-align:center;
  color:#2c3e50;
  margin-top:60px;

 }
</style>

<style>
@import url(../public/css/common.css);
</style>
