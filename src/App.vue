<template>
<div id="app">
  <div  v-if="autenticado === false" class="alert alert-danger" role="alert"><span v-if="autenticado === false">senha ou login errados</span></div>
    <div   v-else class="alert alert-success" role="alert" ><div v-show="autenticado">Sucesso</div></div>
    
   <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-9 col-lg-12 col-xl-10">
                <div class="card shadow-lg o-hidden border-0 my-5">
                    <div class="card-body p-0">
                        <div class="row">
                            <div class="col-lg-6 d-none d-lg-flex">
                                <div class="flex-grow-1 bg-login-image" style=""></div>
                            </div>
                            <div class="col-lg-6">
                                <div class="p-5">
                                    <div class="text-center">
                                        <h4 class="text-dark mb-4">Welcome Back!</h4>
                                    </div>
                                    <div class="user">
                                        <div class="mb-3"><input class="form-control form-control-user" type="email" id="exampleInputEmail" aria-describedby="emailHelp" placeholder="Enter Email Address..." name="email" v-model="email"></div>
                                        <div class="mb-3"><input class="form-control form-control-user" type="password" id="exampleInputPassword" placeholder="Password" name="password" v-model="senha"></div>
                                        <div class="mb-3">
                                            <div class="custom-control custom-checkbox small">
                                                <div class="form-check"><input class="form-check-input custom-control-input" disabled type="checkbox" id="formCheck-1" v-model="senha"><label class="form-check-label custom-control-label" for="formCheck-1" >Remember Me</label></div>
                                            </div>
                                        </div><button class="btn btn-primary d-block btn-user w-100" @click="login">Login</button>
                                        <hr><button class="btn btn-primary d-block btn-google btn-user w-100 mb-2" disabled role="button"><i class="fab fa-google"></i>&nbsp; Login with Google</button><button class="btn btn-primary d-block btn-facebook btn-user w-100" disabled  role="button"><i class="fab fa-facebook-f"></i>&nbsp; Login with Facebook</button>
                                        <hr>
                                    </div>
                                    <div class="text-center"><a class="small" href="forgot-password.html">Forgot Password?</a></div>
                                    <div class="text-center"><a class="small" href="register.html">Create an Account!</a></div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {

  },
  data() {
    return {
      email: '',
      senha: '',
      autenticado: false,
    }
  },
  methods: {
    login(){
      fetch('http://localhost:9007/').then(response => response.json()).then(response =>{
        if(this.email == response[0].email && this.senha == response[0].senha){
          this.autenticado = true;
          // location.href = 'http://localhost:9007/home';
        }else{
          this.autenticado = false;
        }
      // console.log(response);
      })
      console.log(this.autenticado);
    }
  },
  mounted() {

  },
  created() {

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
