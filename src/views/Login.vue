<template>
    <div class="container">
        <div class="row text-center mt-5" >
            <h2>Login Page</h2>
            
        </div>
        <div class="row">
            <div class="col-md-3"></div>
            <div class="col-md-6">
                <div class="alert alert-danger" role="alert" v-if="isAlert">
                    {{messages}}
                </div>
                <div class="form-group">
                    <label for="exampleInputEmail1">Email: </label>
                    <input type="email" class="form-control" v-model="email" placeholder="Enter Mail...">
                </div><br>
                <div class="form-group">
                    <label for="exampleInputPassword1">Password: </label>
                    <input type="password" class="form-control" v-model="password" placeholder="Enter Password...">
                </div>
                <br>
                <button type="submit" class="btn btn-primary" @click="Login">Login</button> 
                <router-link to="/sign-up" class="btn btn-danger ml-2">Sign Up</router-link>
            </div>
            <div class="col-md-3"></div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    name: 'Login',
    data(){
        return {
            name: '',
            email: '',
            password: '',
            isAlert: false,
            messages: ''
        }
    },
    methods:{
        async Login(){
            let result = await axios.get(
                `http://localhost:3000/users?email=${this.email}&password=${this.password}`,
            )
            if(result.status == 200 && result.data.length>0){
                localStorage.setItem("user-info", JSON.stringify(result.data[0]));
                this.$router.push({name: "Home"});
            }else{
                this.isAlert = true,
                this.messages = 'Thông tin tài khoản hoặc mật khẩu sai!!!'
            }
            console.log(result)
        }
    }
}
</script>

<style lang="">
    
</style>