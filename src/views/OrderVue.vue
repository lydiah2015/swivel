<template>
<h1>ORDERS</h1>
<table>
    <tr>
        <th> Name </th>
        <th>Description</th>
        <th>Satus</th>

    </tr>
    <tr v-for=order in orders'>
        <td>{{order.attributes.name}}</td>
         <td>{{order.attributes.Description}}</td>
          <td>{{order.attributes.status}}</td>
    </tr>



 </table>

</template>
<script setup> 
import {ref} from 'vue'
const orders =  ref([])
async function getOrders(){
    let response = await fetch ('https://flexigigapi.herokuapp.com/api/v1/orders',{
        method:'GET',
         headers :{
            'Content-Type':'application/json;charset=utf-8',
            Authorization: "bearer "+localStorage.getItem("token")
        },
    })
    let result = await response.json()
    orders.value=response.data
    console.log(result)
}
getOrders()


</script>