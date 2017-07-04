<template>
  <div>
    <router-view></router-view>
   <br>   
   <br>   
   <br>      
  <mu-paper class="fixed">
     <mu-bottom-nav :value="bottomNav" @change="handleChange">
     <mu-bottom-nav-item value="首页" title="首页" icon="favorite" href="#/index"/>

      <mu-bottom-nav-item value="报名详情" title="报名详情" icon="info" href="#/xq"/>
      <div @click="login">
      <mu-bottom-nav-item value="后台" title="后台" icon="home"/>
      </div>
     </mu-bottom-nav>
  </mu-paper>

 </div>
</template>

<script>

  export default{
 
      data () {
        return {        
          bottomNav: 'recents'      
        }  
      },

      methods:{
	     handleChange (val) {
	      this.bottomNav = val
	         },

      login(){
         if(window.localStorage.getItem('pwd')=='123456'){
          console.log(111111111)
          window.location="http://localhost:8080/#admin"
             
        }else{
          console.log(222)
          window.location="http://localhost:8080/#login"
        }  
        // console.log(111)
      }
	  },

     mounted(){
   
      }
  }
</script>

<style>
	
.fixed{
    position: fixed;
    bottom: 0px;
    left: 0px;
    width: 100%;
  }
</style>