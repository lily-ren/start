<template>
<div>
 <div class="outer1">
   <header>调查表</header>
   <fx-form  >
     <div class="input">
        <fx-input v-model="form.input_el">
          <span slot="label">姓名</span>
        </fx-input>
     </div>
     <div class="radio">
      <fx-radio-group label="性别" > 
        <fx-radio :label="radioGroup.label1"></fx-radio>
        <fx-radio :label="radioGroup.label2"></fx-radio>
      </fx-radio-group>
     </div>
    <div class="checkbox">
      <fx-checkbox-group label="请选择喜好">
        <fx-checkbox v-for="item in like" :label="like" :key="item.id">{{item}}</fx-checkbox>
      </fx-checkbox-group>
    </div>
    
    
    <div class="select">
      <fx-select label="请选择所在地" :options="options" ></fx-select>
    </div>
    
    </fx-form>
    <div class="button">
      <fx-button type="primary" @click="subForm">Submit</fx-button>
    </div>

  </div>

 <div class="outer2">
   <header>数据统计</header>
   <fx-table :data="tableData">
       <fx-table-column 
        prop="name"
        label="姓名"
        >
      </fx-table-column>
      <fx-table-column
        prop="sex"
        label="性别"
        >
      </fx-table-column>
      <fx-table-column
        prop="favorite"
        label="喜好">
      </fx-table-column>
      <fx-table-column
        prop="addr"
        label="所在地">
      </fx-table-column>
      
    </fx-table>
 </div>


</div>


 </template>

<style >
.outer1{
  margin:10px auto;
  border: 2px solid orange ;
  width: 60%;
  box-shadow: 30px black;
  padding: 5%;
  border-radius: 5px;
  
  
}
.outer2{
  margin:10px auto;
  border: 2px solid orange ;
  width: 60%;
  box-shadow: 30px black;
  padding: 5%;
  border-radius: 5px;
}
header{
  text-align: center;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  font-size: 30px;
  border-bottom: 1px solid orange;
}
.input{
  padding: 10px;
}
.radio{
  padding: 10px;
}
.checkbox{
  padding: 10px;
}
.select{
  border-bottom: 1px solid orange;
  padding: 10px;
}
.button{
    padding: 20px;
    text-align: center;
    
}

</style>

<script>
export default {
  data() {
    return {
      form:{
        input_el: '',
      },
      like:['1','2','3','4'],
      options: [
          {
            value: 'Beijing',
            label: '北京',
          },
          {
            value: 'Shanghai',
            label: '上海',
          },
          {
            value: 'Nanjing',
            label: '南京',
          },
          {
            value: 'Chengdu',
            label: '成都',
          },
          {
            value: 'Shenzhen',
            label: '深圳',
          },
          {
            value: 'Guangzhou',
            label: '广州',
          },
        ],
      tableData: [{
            sex:'男',
            name: '王小虎',
            favorite: '1',
            addr:'北京'
          }, {
            sex:'女',
            name: '小虎',
            favorite: '2，3',
            addr:'北京'
          }, {
           sex:'男',
            name: '王虎',
            favorite: '4',
            addr:'北京'
          }],
      radioGroup:{
            label1:'男',
            label2:'女'
      }

    }
  },
  methods:{
    
  }
}
</script>
