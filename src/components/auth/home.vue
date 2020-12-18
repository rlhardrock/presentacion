<template class="homing">
	<div >
		<nav
			class="navbar navbar-expand-lg navbar-dark"
			style="background-color: black"
		>
			<div class="container">
				<a class="navbar-brand" href="#">
					<img
						src="https://www.flaticon.es/svg/static/icons/svg/1177/1177568.svg"
						width="30 "
						height="30 "
						class="d-inline-block align-top"
						alt=" "
						loading="lazy "
					/>
					Usuario</a
				>
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
					<form class="d-flex">
						<button
							@click.prevent="logUserOut"
							class="btn btn-warning btn-lg"
							type="buttom"
						>
							Log Out
						</button>
					</form>
				</div>
			</div>
		</nav>
		<section>
			<div class="card mb-3">
				<div class="row g-0">
					<div class="col-md-4">
						<img src=	"@/assets/neonlights/future02.jpeg" width="450px" height="450px"/>
					</div>
					<div class="col-md-8">
						<div class="card-body">
							<h5 class="card-title">{{ user.name }}</h5>
							<p class="card-text">
								Lorem ipsum dolor sit amet consectetur adipisicing elit. Sapiente quibusdam voluptate adipisci quo amet doloremque asperiores at qui ipsam in ad ullam illo tempora quos, officiis porro neque, fugit quae commodi nemo ipsum blanditiis! Sapiente debitis accusamus iure commodi, reiciendis eveniet quaerat laudantium, porro repudiandae, deleniti quo error necessitatibus veniam! Nemo, eaque nisi eum temporibus fugiat iusto animi nihil, fuga perferendis deserunt nam beatae in eveniet eos corrupti perspiciatis debitis aliquam exercitationem. Assumenda cumque hic culpa blanditiis veritatis nihil minus?
							</p><br>
              <h5 class="card-title">{{ user.email }}</h5>
						</div>
            <div class="card-body">
					    <a href="#" class="card-link">GIT HUB</a>
					    <a href="#" class="card-link">LINKEDIN</a>
				    </div>
					</div>
				</div>
			</div>
		</section>
    <section>
      <seccion-banners></seccion-banners>
    </section>
	</div>
  
</template>
<script>
import VueJwtDecode from "vue-jwt-decode";
import SeccionBanner from './SeccionBanners.vue';
export default {
	components: { SeccionBanner },
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
<style scoped>
.col-md-8 { background: #E6DADA;  /* fallback for old browsers */
background: -webkit-linear-gradient(to bottom, #274046, #E6DADA);  /* Chrome 10-25, Safari 5.1-6 */
background: linear-gradient(to bottom, #274046, #E6DADA); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

}

.homing{
  background: #16BFFD;
background: -webkit-linear-gradient(to left, #CB3066, #16BFFD);
background: linear-gradient(to left, #CB3066, #16BFFD);
}

.card-title{
  text-transform: uppercase;
  font-family:Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
}
</style>