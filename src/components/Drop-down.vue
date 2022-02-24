<template>
<div id="wrap">
  <form action="#">
    <div
    class="pick"> 

    <input
    @click.prevent="isActive=!isActive"
    type="text"
    v-model="valueName"
    placeholder="--- Chọn Thành Phố ---">

    <input type="hidden" name="thanhpho" id="" v-model="valueIndex">

     <button type="submit">Xác nhận </button>
     
    </div>

    <div> 

      <ul v-show="isActive">
        <li
        v-for="(city, index) in citys"
        :key="index"    
        :class="{selected: city.selected}"
        @click="pick(city, index)">

        {{city.name}}

        </li>
      </ul>
    </div>
    
     
  </form>
</div>
 
</template>

<script>
export default {
  data(){
    return{
      isActive: false,
      value: '',
      valueIndex: 0,
      citys: [
      {name: 'TP. Hải Phòng', selected: false},
      {name: 'TP. Hồ Chí Hinh', selected: false},
      {name: 'TP. Hà Nội', selected: false},
      {name: 'TP. NewYork', selected: false}
      ]
    }
  },
  methods:{
    pick(city, index){
      this.isActive=false;
      this.valueName = city.name;
      this.valueIndex = index;
      
    }

  }

}
</script>

<style>

*{
  box-sizing: border-box;
  padding-left: 0;
  margin: 0;
}
div#wrap{
  padding-left: 100px;
}
ul{
  width: 300px;
  background: chartreuse;
}
ul li{
  border: 1px solid black;
  padding: 5px 5px;
  font-size: 16px;
  font-weight: bold;
  
  list-style: none;
}
input{
  background-color: transparent;
  width: 300px;
  padding: 5px 5px;
  font-size: 16px;
}
button{
  padding: 5px 5px;
  font-size: 16px;
  background: greenyellow;
}
.selected{
  background: red;
}
</style>