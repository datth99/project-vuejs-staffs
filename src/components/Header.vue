<template>
    <div>
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <div class="container-fluid">
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                    <li class="nav-item">
                        <router-link to="/" class="nav-link active">Trang chủ</router-link> 
                    </li>
                    <li class="nav-item">
                        <router-link to="/user" class="nav-link">Nhân viên</router-link> 
                    </li>
                     <li class="nav-item">
                        <router-link to="/about" class="nav-link">Hỗ trợ</router-link> 
                    </li>
                    <li class="nav-item">
                        <form class="d-flex">
                            <input class="form-control me-2" type="search" placeholder="Tìm kiếm..." aria-label="Search">
                            <button class="btn btn-outline-success" type="submit"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-search" viewBox="0 0 16 16">
                            <path d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"/>
                            </svg></button>
                        </form>
                    </li>
                </ul>
                
                <div>
                    <button @click="Logout" class="nav-link btn btn-danger text-white" >Đăng xuất</button>
                </div>
                </div>
            </div>
        </nav>
    </div>
</template>
<script>
export default {
    name: "Header",
    methods:{
        Logout(){
            localStorage.clear();
            this.$router.push({name: "Login"});
        }
    }
}
</script>
<style lang="">
    
</style>