<template>
    <div>
        <form>
                <input type="text" name="firstName" placeholder="Enter Name" v-model="user.firstName"/>
         <input type="text" name="lastame" placeholder="Enter Last Name" v-model="user.lastname"/>
          <input type="email" name="email" placeholder="Enter email" v-model="user.email"/>
          <button v-on:click="adduser">Add new user</button>
        </form>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name:'AddUser',
    data(){
        return{
            user :{
                firstName:'',
                lastname:'',
                email: ''
            }
        }
    },
    methods:{
      async adduser(){
      axios.post('http://localhost:3000/user',{
                firstName:this.user.firstName,
                lastname:this.user.lastname,
                email:this.user.email
            })
           
        }
    },

}


</script>
