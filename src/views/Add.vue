<template>
    <div>
     
        <div class="form-div">
<h1 id="title">Add new user</h1>

<form id="survey-form">
  <label for="name" id="name-label">First Name </label><br>
  <input type="text" id="name" name="name" placeholder="Enter your First name" required v-model="user.firstName"><br>
  <label for="name" id="name-label">Last Name </label><br>
  <input type="text" id="name" name="name" placeholder="Enter your Last name" required v-model="user.lastname"><br>
  <label for="email" id="email-label">Email</label><br>
  <input type="email" id="email" name="email" placeholder="Enter your Email" required v-model="user.email"><br>
 
  <input v-on:click="adduser" type="submit" id="submit" value="Add new user">
  
</form>
</div>
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
        //Post request to add user to the json data base
      async adduser(){
     let result = await axios.post('http://localhost:3000/user',{
                firstName:this.user.firstName,
                lastname:this.user.lastname,
                email:this.user.email
            })
            console.log(result.status)
            //when then response is done navigate to the Home page
              if(result.status == 200){
            this.$router.push({name:'Home'})
        }
           
        }
    },

}


</script>
<style>

html,body {
  min-height: 100%;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}
.form-div {
  height: 100%;
  background-image: linear-gradient(rgba(10,80,200,0.5), rgba(0,255,255,0.4)), url("https://www.jotform.com/uploads/ZIGRAM/form_files/eeeee.5eeb483b076531.72239553.jpg");
  background-size: 100%;
}
.form-div {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
#survey-form {
  background: rgba(0, 0, 0, 0.31);
  padding: 3% 10%;
  border-radius: 2px;
  display: flex;
  flex-direction: column;
  font-size: 3vmin;
  letter-spacing: 1px;
}
label {
  color: #fcfcfc;
}
h1, p {
  color: #fcfcfc;
  letter-spacing: 1px;
}
p {
  margin-top: 0px;
  text-shadow: 3px 3px 8px #005ab3;
}
input, select, textarea {
  padding: 3% 8%;
  border-radius: 4px;
  border-color: #fff;
  border-style: none;
}
input[type="submit"] {
  background-color: #37af65;
  color: #fff;
  font-size: 4vmin;
  letter-spacing: 0px;
}
input[type="submit"]:hover {
  background-color: #2b884f;
}

</style>