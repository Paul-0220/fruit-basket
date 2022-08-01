<!-- SignUp page -->

<template>
<fieldset>
    <legend><h2>SignUp</h2></legend>
    <form id="signUp">
     <input type="text" v-model='name' id="userName" name="name" placeholder="User Name"><br><br>
    <input type="email" v-model="email" id="email" name="name" placeholder="Email"><br><br>
    <input type="password" v-model="password" id="password" name="name" placeholder="password"><br><br>
    <button @click="signUp">signup</button>
    </form>
</fieldset>
</template>
<script>
import axios from 'axios'
export default {
    name:'signUp',
    data(){
        return {
            name:'',
            email:'',
            password:''
        }
    },
    methods:{
        async signUp(){
            console.log(this.name,this.email,this.password)
            let result=await axios.post('http://localhost:3001/',{
                name:this.name,
                email:this.email,
                password:this.password
            });
            console.log(result)
            if(result.status==201){
                console.log('signup done')
            }
        }
    }
}
</script>
<style>
#signUp input{
    width: 300px;
    height:40px;
    padding-left: 20px;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    border:1px solid skyblue

}
#signUp button{
    width: 320px;
    height:40px;
    border: 1px solid skyblue;
    color:#fff;
    background-color: skyblue;
    cursor: pointer;
}
</style>