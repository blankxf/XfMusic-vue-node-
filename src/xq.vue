<template>
  <div>
    <h1>当前总人数：{{zong}}</h1>  
    <mu-table :showCheckbox="false">
        <mu-thead slot="header" >
          <mu-tr>
            <mu-th tooltip="序号">序号</mu-th>
            <mu-th tooltip="名称">昵称</mu-th>
            <mu-th tooltip="状态">报名人数</mu-th>
          </mu-tr>
        </mu-thead>
        <mu-tbody>
          <mu-tr v-for="item,index in datas"  :key="index" :selected="item.selected">
            <mu-td>{{index + 1+ (newIndex-1)*10}}</mu-td>
            <mu-td>{{item.name}}</mu-td>
            <mu-td>{{item.num}}</mu-td>
          </mu-tr>
        </mu-tbody>
    </mu-table>

    <mu-pagination :total="total" :current="current" @pageChange="handleClick">
  </mu-pagination>
 </div>
</template>
<script>
  import axios from 'axios';
  export default{
 
      data () {
        return {
          _id:'',
          datas:{},
          zong:0,
          total: 70,
          current: 1,
          newIndex:1,
      
        }  
      }, 
      methods: {
         handleClick (newIndex) {
              this.newIndex=newIndex
              axios.get(`http://localhost:3000/all/?page=${newIndex}`).then((data)=>{
                       this.datas=data.data;                             
                    },(err)=>{

                })
        }
      },
     mounted(){        
         axios.get("http://localhost:3000/all").then((data)=>{
           this.datas=data.data;
           for(var i=0;i<data.data.length;i++){
             this.zong+=Number(data.data[i].num)
           }
         },(err)=>{
          
         }) 

     //获取total
         axios.get("http://localhost:3000/myCount").then((data)=>{
                       this.total=data.data.length;                             
                    },(err)=>{

                }) 
      }
  }
</script>

<style>
   h1{
      width: 100%;
      text-align: center;
   }




</style>