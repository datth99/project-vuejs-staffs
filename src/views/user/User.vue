<template>
  <div>
    <app-header></app-header>
    <div class="mt-3 mb-3">
         <router-link to='/user/add' class="btn btn-primary">Thêm nhân viên</router-link>
    </div>
   
    <table class="table table-hover" style="border: 1px solid #000">
        <thead>
            <tr>
                <th scope="col">ID</th>
                <th scope="col">Tên </th>
                <th scope="col">Giới tính</th>
                <th scope="col">Email </th>
                <th scope="col">Số điện thoại</th>
                <th scope="col">Quê quán</th>
                <th scope="col">Chỉnh sửa</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="item in staffs" :key="item">
                <th scope="row">{{item.id}}</th>
                <td>{{item.name}}</td>
                <td>{{item.gender}}</td>
                <td>{{item.email}}</td>
                <td>{{item.phone}}</td>
                <td>{{item.country}}</td>
                <td>
                    <router-link :to="'/user/edit/'+item.id" class="btn btn-primary">Sửa</router-link>
                    <button @click="deleteItem(item.id)" class="btn btn-danger">Xóa</button>
                </td>
            </tr>
            
        </tbody>
        </table>
  </div>
</template>
<script>
import appHeader from '../../components/Header.vue'
import axios from 'axios'
export default {
  name: 'Staff',
  data() {
      return {
          name: '',
          staffs: []
      }
  },
  methods:{
       async deleteItem(id){
          let result = await axios.delete("http://localhost:3000/staffs/"+id);
          if(result.status==200){
              this.loadData()
          }
      },
      async loadData(){
            let user = localStorage.getItem('user-info')
            if(user==null){
                this.$router.push({name: 'Login'})
            }
            let result = await axios.get("http://localhost:3000/staffs")
            this.staffs = result.data;
      } 
  },
  components:{
    appHeader,
  },
  async mounted() {
      this.loadData();
  },
}
</script>
<style lang="">
    
</style>