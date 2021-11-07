<template>
    <div class="hello">
        <h1>User Liste</h1>
      <table border="1">
          <tr>
              <td>ID</td>
              <td>First Name</td>
              <td>Last Name</td>
              <td>Email</td>
              <td>Action</td>
          </tr>
          <tr v-for="user in users" :key="user.id">
             <td>{{user.id}}</td>
             <td>{{user.firstName}}</td>
             <td>{{user.lastname}}</td>
              <td>{{user.email}}</td>
              <td><router-link :to="'/update/'+user.id">Update</router-link>
              <button v-on:click="deleteuser(user.id)">Delete</button>
              </td>

             </tr>
      </table>

    </div>
</template>
<script>
import axios from 'axios';

export default {
name:'UserListe',
data(){
    return {
        users:[],
    
    }

},

methods:{
async deleteuser(id){
 const result = await axios.delete("http://localhost:3000/user/"+id);
 if(result.status == 200){
     this.$router.go()
 }

},
async loadData(){
     let result =await axios.get('http://localhost:3000/user')
    console.warn(result.data)
    this.users=result.data
}

},
async mounted(){
    let result =await axios.get('http://localhost:3000/user')
    console.warn(result.data)
    this.users=result.data
}
}
</script>
<style>
td {
    width:160px;
    height:40px;
}

</style>