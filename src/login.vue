<template>
	<div>
		<h1>后台登录</h1>
		<div class="main">
		<mu-text-field label="请输入后台登录密码" type="password" labelFloat v-model="pwd"/><br/>
		<mu-raised-button @click="ok" label="进入后台" class="demo-raised-button" secondary/>
		</div>
	</div>
</template>
<script>

  export default{
 
      data () {
        return {        
           pwd:""
        }  
      },

      methods:{
	     ok(){
	     	if(this.pwd=='123456'){
	     		window.localStorage.setItem('pwd','123456');
	     		window.location="http://localhost:8080/#admin"
	     	}
	     	/*if(window.localStorage.getItem('pwd')=='123456'){//判断username是否存在
	     		console.log(111)
	     		window.location.href='#/admin'
            }else{
            	console.log(222)
             window.localStorage.setItem('pwd','123456');
             //window.location.href="#/admin/login"
             //console.log('--ddd')
            }*/
	     }
	  },

     mounted(){
   
      }
  }
</script>