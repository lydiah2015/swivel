<template>

<form>
     <div >
        <input type='text' placeholder="username" class="signup-text-input" v-model="auth.phone_number"/>
     </div>

     <div>
         <input type='password' placeholder='password' v-model="auth.password"/>
     </div>
    <button type='button' @click= 'onSubmit'>LOGIN</button>
 </form>
    
</template>

<script setup>
import {reactive} from 'vue'
import router from "../router/index"

const auth= reactive ({
    phone_number: "",
    password:""
})
async function onSubmit(){
    let response = await fetch( 'https://flexigigapi.herokuapp.com/api/v1/signin',{
        method:'POST',
        headers :{
            'Content-Type':'application/json;charset=utf-8'
        },
        body: JSON.stringify(auth)
    } );
    let result = await response.json()
    console.log(result)
    localStorage.setItem('token',result.token)
    router.push('/orders')
}

</script>


<style scoped>

*, *:before, *:after {
  box-sizing: border-box;
}
input[type=text]  {
  padding: 10px;
    margin:10px 0;
    box-shadow:0 0 15px 4px rgba(0,0,0,0.06);
}
input[type=password]  {
  padding: 10px;
    margin:10px 0;
    box-shadow:0 0 15px 4px rgba(0,0,0,0.06);
}


.border-bottom-input {
  border:0; 
  border-bottom:1px solid #eee;
}
.rounded-input {
  padding:10px;
  border-radius:10px;
}
input {
  width:25%;
}
input, textarea {
  font-family:inherit;
  font-size: inherit;
}
button {

  /* remove default behavior */
  appearance:none;
  -webkit-appearance:none;

  /* usual styles */
  padding:10px;
  border:none;
  background-color:green;
  color:#fff;
  font-weight:600;
  border-radius:5px;
  width:5%;

}

</style>