<template>
    <div>
        <app-header></app-header>
        <h2 class="mt-3 mb-3">Thêm nhân viên</h2>
        <div class="mb-3 row">
            <label class="col-sm-2 col-form-label">Tên</label>
            <div class="col-sm-10">
                <input type="text" class="form-control" v-model="staffs.name">
            </div>
        </div>
        <div class="mb-3 row">
            <label class="col-sm-2 col-form-label">Giới tính</label>
            <div class="col-sm-10">
                <input class="form-check-input" type="radio" name="flexRadioDefault" value="Nam" id="Nam" v-model="staffs.gender" >
                <label class="form-check-label" >
                    Nam
                </label>
                
                <input class="form-check-input" type="radio" name="flexRadioDefault" value="Nữ"  id="Nữ" v-model="staffs.gender" checked>
                <label class="form-check-label" >
                    Nữ
                </label>
            </div>
        </div>
        <div class="mb-3 row">
            <label class="col-sm-2 col-form-label">Email</label>
            <div class="col-sm-10">
                <input type="email" class="form-control" v-model="staffs.email">
            </div>
        </div>
        <div class="mb-3 row">
            <label class="col-sm-2 col-form-label">Số điện thoại</label>
            <div class="col-sm-10">
                <input type="number" class="form-control" v-model="staffs.phone">
            </div>
        </div>
        <div class="mb-3 row">
            <label class="col-sm-2 col-form-label">Quê quán</label>
            <div class="col-sm-10">
                <input type="text" class="form-control" v-model="staffs.address">
            </div>
        </div>
        <button @click="addStaff" class="btn btn-primary">Thêm</button>
    </div>
</template>
<script>
import axios from 'axios';
import appHeader from '../../components/Header.vue'
export default {
    name: 'UserAdd',
    data(){
        return{
            staffs: {
                name: '',
                gender: '',
                email: '',
                phone: '',
                address: ''
            }
        }
    },
    methods:{
        async addStaff(){
             
            const result = await axios.post("http://localhost:3000/staffs",{
                name: this.staffs.name,
                gender: this.staffs.gender,
                email: this.staffs.email,
                phone: this.staffs.phone,
                address: this.staffs.address
            });
            if(result.status == 201 ){
                this.$router.push({name: "User"});
            }
            
        }
    },
    components:{
        appHeader,
    },
    mounted() {
        let user = localStorage.getItem('user-info')
        if(user==null){
            this.$router.push({name: 'Login'})
        }
    },
}
</script>
<style lang="">
    
</style>