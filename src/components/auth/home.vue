<template>
  <div>
    <!-- <nav class="navbar navbar-expand-lg navbar-dark" ;"> -->
    <nav class="navbar navbar-light bg-dark" style="background-color: #3DA6A0">
            <div class="container-fluid">
         
                <div class="d-grid gap-2 d-md-flex justify-content-md-end">
                    <button class="btn btn-dark" type="button"> </button>
                </div>
                <form class="d-flex">
                <button 
                @click.prevent="logout"
                class="btn btn-warning btn-lg"
                type="buttom">Log Out</button>

                </form>
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