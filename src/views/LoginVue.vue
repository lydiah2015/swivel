<template>
 <form>
     <div>
        <input type='text' placeholder="username" v-model="auth.phone_number"/>
     </div>

     <div>
         <input type='password' placeholder='password' v-model="auth.password"/>
     </div>

 </form>
    
</template>

<script setup>
import {reactive} from 'vue'

const auth= reactive ({
    phone_number: "",
    password:""
})
function onSubmit(){
    
}
</script>