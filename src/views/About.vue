<template>
  <div class="about">
    <app-header></app-header>
    <h1>This is an about page</h1>
  </div>
</template>
<script>
import appHeader from '../components/Header.vue'
export default {
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