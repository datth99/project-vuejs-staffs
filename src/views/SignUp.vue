<template>
    <div class="container">
        <div class="row text-center mt-5" >
            <h2>Sign Up</h2>
            
        </div>
        <div class="row">
            <div class="col-md-3"></div>
            <div class="col-md-6">
                <div class="alert alert-danger" role="alert" v-if="isAlert">
                    {{messages}}
                </div>
                <div class="form-group">
                    <label for="exampleInputEmail1">Name: </label>
                    <input type="text" class="form-control" v-model="name" placeholder="Enter Name...">
                    
                </div><br>
                <div class="form-group">
                    <label for="exampleInputEmail1">Email: </label>
                    <input type="email" class="form-control" v-model="email" placeholder="Enter Mail...">
                    
                </div><br>
                <div class="form-group">
                    <label for="exampleInputPassword1">Password: </label>
                    <input type="password" class="form-control" v-model="password" placeholder="Enter Password...">
                </div>
                <br>
             
                <button type="submit" class="btn btn-primary" @click="SignUp">Sign Up</button>
                <router-link to="/login" class="btn btn-danger ml-2">Login</router-link>
            </div>
            <div class="col-md-3"></div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    name: 'SignUp',
    data(){
        return {
            name: '',
            email: '',
            password: '',
            messages: '',
            isAlert: false
        }
    },
    methods:{
        async SignUp(){
            let result = await axios.post("http://localhost:3000/users", {
                    name: this.name,
                    email: this.email,
                    password: this.password,
            });
            if(result.status == 201 && this.name != '' && this.email != '' && this.password != ''){
                localStorage.setItem("user-info", JSON.stringify(result.data));
                this.$router.push({name: "Login"});
            }else{
                this.isAlert = true,
                this.messages = 'Bạn không được để trống bất kỳ trường nào!!!'
            };
        },
    },
    mounted() {
        let user = localStorage.getItem('user-info');
        if(user){
            this.$router.push({name: 'Home'});
        }
    },
}
</script>

<style lang="">
    
</style>