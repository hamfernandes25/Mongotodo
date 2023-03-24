<template>
  <div id="app">
    <form @submit.prevent >
   <input type="text" name="message" v-model="message" />  
    <button v-on:click="insertdata(message)" value="ADD">ADD
   </button>
   <br>
<ul>
  <li >{{message }}</li><br>
</ul>
  <table align="center" border="1px">
     
  

 <tr v-for="(postt,index) in posts" v-bind:key="postt.id">
   <td><div  class=index >
     <s v-if="postt.status=='finished'">{{ postt.id + "  "+postt.value+"  "+postt.status}}</s> 
   <p v-else>{{ postt.id + "  "+postt.value+"  "+postt.status}}</p> </div> </td>
   <td> <button v-on:click=" complete(index,postt.id,postt.value)" value="delete">COMPLETE </button> </td>
   <td> <button v-on:click=" deletedata(index)" value="delete">DELETE </button> </td>
  </tr>
 
  </table>


</form>
  </div>
</template>

<script>

export default {

  
    data() {
     return{
message:'hello',
check:false,
posts:[
  {id:1,value:'hi',status:'finished'},
  {id:2,value:'hello',status:'inprogress'},
]
    
     }},

  

 methods: {
    insertdata(inpn)
    {

this.posts.push({
   id: Date.now()
,value:inpn,status:'inprogress'}),console.log(inpn)
       console.log(this.posts)
    },
     deletedata(dnpn)
    {this.posts.splice(dnpn,1)
console.log(dnpn)

    },
      complete(dnpn,ii,pp)
    {this.posts.push( {  id: ii
,value:pp,status:'finished'})
      
     
console.log(dnpn)

    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

a{
  text-decoration:line-through;
}
</style>
