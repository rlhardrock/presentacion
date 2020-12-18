<template>
  <div class="container">
    <div class="row">
      <div class="col-lg-6 offset-lg-3 col-sm-10 offset-sm-1">
        <form
          class="text-center border border-primary p-5"
          style="margin-top: 70px; height: auto; padding-top: 100px !important"
          @submit.prevent="loginUser">
          <h1 class="h3 mb-3 font-weight-normal" style="textalign: center">
            Iniciar Sesión
          </h1>

          <div class="col-auto">
                
                <input 
                v-model="login.email"
                type="text" 
                class="form-control" 
                id="staticEmail2" 
                placeholder="email">
          </div>
         <br>
          <div class="col-auto">
                
                <input 
                v-model="login.password"
                type="password" 
                class="form-control" 
                id="inputPassword2" 
                placeholder="password">
            </div>
          <br>
          <center>
            <div class="col-auto">
                <button
                @click.prevent="loginUser"
                type="submit" 
                class="btn btn-success mb-3">Authenticate</button>
            </div>
          </center>
        </form>
      </div>
    </div>
  </div>
</template>
<script>
import Swal from "sweetalert2";
export default {
  data() {
    return {
      login: {
        email: "",
        password: "",
      },
    };
  },
  methods: {
    async loginUser() {
      try {
        let response = await this.$http.post("/api/auth/signin", this.login);
        console.log(response.data);
        let token = response.data.accessToken;
        localStorage.setItem("jwt", token);
        if (token) {
          Swal.fire({
                        icon: 'success',
                        title: 'Bienvenido !',
                        showConfirmButton: false,
                        timer: 1500,
                        backdrop: `rgba(0,250,0,0.6)`
                        });
                        this.$router.push('/home');
        }
      } catch (err) {
                Swal.fire({
                icon: 'error',
                title: 'Datos Incorrectos! Reintentalo!',
                width: 600,
                padding: '3em',
                timer: 2500,
                backdrop: `rgba(0,0,125,0.9)`
                });
            }
    },
  },
};
</script>