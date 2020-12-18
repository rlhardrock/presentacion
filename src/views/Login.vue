<template>
  <div class="login">
    
    <login />
    <seccion-banners/>
  </div>
</template>

<script>
// @ is an alias to /src

import Login from '../components/auth/login.vue';
import SeccionBanners from '../components/auth/SeccionBanners.vue';

export default {
//   name: 'Home',
  components: {
    Login,
    SeccionBanners
  }
};
</script>

<style scoped>
.login{
  background: #780206;  /* fallback for old browsers */
background: -webkit-linear-gradient(to bottom, #061161, #780206);  /* Chrome 10-25, Safari 5.1-6 */
background: linear-gradient(to bottom, #061161, #780206); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

}
</style>
