<template>
 <form>
     <div>
        <input type='text' placeholder="username" v-model="auth.phone_number"/>
     </div>

     <div>
         <input type='password' placeholder='password' v-model="auth.password"/>
     </div>
    <button type='button' @click= 'onSubmit'>LOGIN</button>
 </form>
    
</template>

<script setup>
import {reactive} from 'vue'

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
}

</script>