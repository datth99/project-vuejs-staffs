<template>
  <div>
    <app-header></app-header>
        <div class="row">
          <div class="col-sm-12">
          <h1>Hello {{name}}? Welcome on Home Page!</h1>
          <img alt="Vue logo" src="../assets/logo.png">
        </div>
    </div>
  </div>
</template>

<script>
import appHeader from '../components/Header.vue';

export default {
  name: 'Home',
  data() {
    return {
      name: 'YOU'
    }
  },
  components: {
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
