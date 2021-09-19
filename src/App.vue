<template>
  <div id="app">
    <div class="d-flex">
      <selectCategory v-on:select-category="setParentSelectedCategory"></selectCategory>
      <sortBox v-on:select-sort="setSelectedSortMethod"></sortBox>
    </div>
    <div class="d-flex flex-wrap pt-4">
      <itemCard v-for="item in displaySelectedCategory" :key="item.title" v-bind="item"></itemCard>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue';
import itemCard from './components/itemCard.vue';
import selectCategory from './components/selectCategory.vue';
import sortBox from './components/sortBox.vue';
import carInfo from './carDataBase.json';

// let cars = [];
// let carsJson = JSON.parse(carInfo);

export default {
  name: 'App',
  components: {
    // HelloWorld,
    itemCard,
    selectCategory,
    sortBox
  },
  data(){
    return {
      init: carInfo,
      items:carInfo,
      select:"",
      sort:"",
      message:""
    }
  },
  methods:{
      setParentSelectedCategory:function(value){
          this.$data.select = value;
      },
      setSelectedSortMethod:function(value){
        this.$data.sort = value;
      },
      convertStrMoneyToInteger: function(str){
        return parseInt(str.replace(/[^0-9]/g, ''));
      },
      convertStrDateToDate: function(str){
        return new Date(str);
      },
  },
  computed:{
    displaySelectedCategory:function(){
      let result = [];
      if (this.$data.select != ""){
        const target = this.$data.select;
        result = this.$data.init.filter(x=>x.category === target);
      } else{
        result = this.$data.init;
      }

      if(this.$data.sort === "Low to High") result = result.sort((x,y)=> this.convertStrMoneyToInteger(x.price) - this.convertStrMoneyToInteger(y.price));
      else if(this.$data.sort === "High to Low") result = result.sort((x,y)=> this.convertStrMoneyToInteger(y.price) - this.convertStrMoneyToInteger(x.price));
      else if(this.$data.sort === "Newest Arrivals") result = result.sort((x,y)=> this.convertStrDateToDate(y.date) - this.convertStrDateToDate(x.date));
      return result;
    },
  }
}
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
