<template>
<div>
 <div class="outer1">
   <header>调查表</header>
   
   <fx-form ref='form'>
     <div class="input">
        <fx-input 
          v-model="form.input_el"
          prop="form.input_el"
          placeholder="请输入姓名"
          >
          <span slot="label">姓名</span>
        </fx-input>
        <fx-input
          placeholder="请输入内容"
          label="个人tag"
          v-model="tagInput"
          :collapse-tags="true"
          @change="onChange"
        >
        </fx-input>
     </div>
     <div class="radio">
      <fx-radio-group label="性别 "
          v-model="form.radioGroup_el" 
          prop="form.radioGroup_el"
          ref="form.radioGroup_el"
          @change="radioGroup_change"> 
        <fx-radio :label="radioGroup.label1" ></fx-radio>
        <fx-radio :label="radioGroup.label2"></fx-radio>
      </fx-radio-group>
     </div>
    <div class="checkbox">
      <fx-checkbox-group label="请选择喜好"
          v-model="form.checkboxGroup_el"
          ref="form.checkboxGroup_el"
          prop="form.checkboxGroup_el"
          @change="checkboxGroup_change">
        <fx-checkbox v-for="item in like" :label="like" :key="item" > {{item}} </fx-checkbox>
      </fx-checkbox-group>
    </div>
    
    
    <div class="select">
      <fx-select label="请选择所在地" :options="options"
          v-model="form.select_el" 
          prop="select_el"
          ref="select_el"
          ></fx-select>
    </div>
    <div class="time">
      <fx-time-select
        v-model="form.timeSelect_el"
        ref="timeSelect_el"
        prop="timeSelect_el"
        label="time:"
        placeholder="请选择时间"
        :picker-options="{
        start: '08:30',
        step: '00:30',
        end: '19:30'
      }"
      >
      </fx-time-select>
      <fx-date-picker
        v-model="form.datePicker_el"
        ref="form.datePicker_el"
        prop="form.datePicker_el"
        label="date:"
        placeholder="请选择日期"
        type="date"
        ></fx-date-picker>
    </div>
    <div class="country">
      <fx-cascader
        v-model="form.cascader_el"
        ref="form.cascader_el"
        prop="form.cascader_el"
        label="国家/省/市"
        placeholder="国家/省/市"
      >
      </fx-cascader>
      <fx-select-area
        v-model="form.select_area_el"
        prop="form.select_area_el"
        ref="form.select_area_el"
        label="国家/省/市"
        level="4"
        
      
      ></fx-select-area> 
    </div>
    
    
    </fx-form>
    <div class="button">
      <fx-button type="primary" @click="subForm">提交一下</fx-button>
    </div>

  </div>

 <div class="outer2">
   <header>数据统计</header>
   <fx-table :data="tableData" 
      :row-class-name="tableRowClassName"
      height="200"
      border="true"
      >
      <fx-table-column 
        type="selection"
        width="50"
        ></fx-table-column>
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
  <div style="margin-top: 20px">
    <fx-button @click="toggleSelection([tableData[1], tableData[2]])">切换第二、第三行的选中状态</fx-button>
    <fx-button @click="toggleSelection()">取消选择</fx-button>
  </div>
 </div>
  <div class="outer3">
    
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
  padding: 10px;
}
.time{
  padding:10px;
  display: flex;
  justify-content:space-between;
}
.button{
    border-top: 1px solid orange;
    padding: 20px;
    text-align: center;   
}
.el-table .warning-row {
    background: oldlace;
  }
.el-table .success-row {
    background: #f0f9eb;
  }


</style>

<script>
export default {
  data() {
    return {
      form:{
        input_el: '',
        radioGroup_el:'',
        checkboxGroup_el:'',
        select_el:'',
        cascader_el:[],
      },
      script:"true",
      tagInput:[],
      like:[
          '1','2','3','4'
          
      ],
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
          },{
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
      },
      

      
  };
},
  methods:{
    radioGroup_change(val){
      console.log('radioGroup_change:',val,this.form.radioGroup_el)
    },
    checkboxGroup_change(val){
      console.log('checkoboxGroup_change:',val,this.form.checkboxGroup_el)
    },
    subForm(e) {
        var p = this.$refs.form.validate();
        p.then(function(d){
          console.log('success');
        },function(d){
          console.log('fail');
        })
      },
    onChange(val){
      console.log('onChange...',val,this.tagInput)
    },
    cascader_onChange(val) {
        console.log('cascader_onChange', val);
      },
    tableRowClassName({row, rowIndex}) {
        if (rowIndex === 1) {
          return 'warning-row';
        } else if (rowIndex === 3) {
          return 'success-row';
        }
        return '';
      },
      toggleSelection(rows){
        if(rows){
          rows.forEach(row =>{ this.$refs.multipTable.toggleRowSelection(row)});

        }else {
          this.$refs.multipTable.clearSelection();
        }
      }
  }
}

</script>
