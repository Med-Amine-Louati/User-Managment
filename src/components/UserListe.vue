<template>
    <div class="hello">
        <h1>User Liste</h1>
      <table border="1" id ="table">
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
              <td><button class = "edit"><router-link :to="'/update/'+user.id">Update</router-link></button>
              <button class = "delete" v-on:click="deleteuser(user.id)">Delete</button>
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
    //delete user by id
async deleteuser(id){
 const result = await axios.delete("http://localhost:3000/user/"+id);
 if(result.status == 200){
     //reload page after dalete user
     this.$router.go()
 }

},


},
//get all the user from the database
async mounted(){
    let result =await axios.get('http://localhost:3000/user')
    console.warn(result.data)
    this.users=result.data
}
}
</script>
<style>
#table{
    display: center;
}
td {
    width:160px;
    height:40px;
}
.delete {
  background-color: #f44336; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
}
.edit {
  background-color: #4CAF50; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
}


</style>