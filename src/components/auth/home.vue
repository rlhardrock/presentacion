<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-dark" style="background-color: #3DA6A0;">

      <div class="container">
        <a class="navbar-brand" href="#"> 
          
          <img src="https://www.flaticon.es/svg/static/icons/svg/1177/1177568.svg" width="30 " height="30 " class="d-inline-block align-top " alt=" " loading="lazy "> 
          Usuario</a>
        <button
          class="navbar-toggler"
          type="button"
          data-toggle="collapse"
          data-target="#navbarNav"
          aria-controls="navbarNav"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div
          class="collapse navbar-collapse justify-content-end"
          id="navbarNav"
        >
          <ul class="navbar-nav">
            <li class="nav-item active">
              <a class="nav-link" @click="logUserOut"> Cerrar Sesión</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
    <section>
      <div class="container mt-5">
        <div class="row">
          <div class="col-md-12">
            <ul class="list-group">
              <li class="list-group-item">Nombre : {{ user.name }}</li>
              <li class="list-group-item">Correo : {{ user.email }}</li>
            </ul>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
<script>
import VueJwtDecode from "vue-jwt-decode";
export default {
  data() {
    return {
      user: {},
    };
  },
  methods: {
    getUserDetails() {
      let token = localStorage.getItem("jwt");
      let decoded = VueJwtDecode.decode(token);
      console.log("hola decode", decoded);
      this.user = decoded;
    },
    logUserOut() {
      localStorage.removeItem("jwt");
      this.$router.push("/");
    },
  },
  created() {
    this.getUserDetails();
  },
};
</script>
<style scoped></style>