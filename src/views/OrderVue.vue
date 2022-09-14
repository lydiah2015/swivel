<template>
<h3>ORDERS</h3>

<table>
    <tr>
        <th> Name </th>
        <th>Description</th>
        <th>Status</th>
        <th> action</th>

    </tr>
    <tr v-for='order in orders'>
        <td>{{order.attributes.name}}</td>
         <td>{{order.attributes.description}}</td>
          <td>{{order.attributes.status}}</td>
          <td @click='convertToProject(order.id)'>convert to project</td>
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
    orders.value=result.data
    console.log(result)
}
getOrders()
async function convertToProject(orderId){
      let response = await fetch ('https://flexigigapi.herokuapp.com/api/v1/orders',{
        method:'POST',
         headers :{
            'Content-Type':'application/json;charset=utf-8',
            Authorization: "bearer "+localStorage.getItem("token")
        },
         body: JSON.stringify({
             order_id: orderId, 
         })
    })
    let result = await response.json()

    console.log(result)


}

</script>


<style scoped>
h3{
    margin-top: 30px;
    margin-bottom: 30px;
}
table {
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
}
th, td {
  border: 1px solid black;
padding: 8px;

}
 th {
  width: 25%;
} 
h3{
    text-decoration-line: underline;
    
}
</style>