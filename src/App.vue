<template>
  <div id="app">
    <div class="container-fluid">
      <div class="container">
        <div class="row">
        <div class="col-sm-12">
            <router-view/>
          </div>
      </div>
      </div>
    </div>
    
  </div>
</template>
<script>
import SignUp from './views/SignUp.vue'
import appHeader from './components/Header.vue'
export default {
  components:{
    SignUp,
    appHeader,
  }
}
</script>
<style scoped>

</style>
