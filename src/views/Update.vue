<template>
    <div>
        <form>
                <input type="text" name="firstName" placeholder="Enter Name" v-model="user.firstName"/>
         <input type="text" name="lastame" placeholder="Enter Last Name" v-model="user.lastname"/>
          <input type="email" name="email" placeholder="Enter email" v-model="user.email"/>
          <button v-on:click="updateuser">Update user</button>
        </form>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name:'Update',
    data(){
        return{
             user:{
                firstName: '',
                lastname:'',
                email: ''
             }
        }
    },
    async mounted(){
         const result = await axios.get('http://localhost:3000/user/'+this.$route.params.id)
         console.log(result.data)
            this.user=result.data;

    },
methods:{
    async updateuser(){
        let result= await axios.put('http://localhost:3000/user/'+this.$route.params.id,{
            firstName:this.user.firstName,
            lastname:this.user.lastname,
            email:this.user.lastname
        });
        if(result.status == 200){
            this.$router.push({name:'Home'})
        }
    }
}

}


</script>
