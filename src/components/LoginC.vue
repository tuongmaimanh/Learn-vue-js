<template>
  <main class="login">
		<section class="forms">
			<form class="login" @submit.prevent="login">
				<h2>Login</h2>
				<input 
					type="email" 
					placeholder="Email address"
					v-model="login_form.email" />
				<input 
					type="password" 
					placeholder="Password" 
					v-model="login_form.password" />
				<input 
					type="submit" 
					value="Login" />
		<router-link to="/register" style="text-decoration:none;color:black">Register -></router-link> 
		<hr>
		<i>Account admin</i><br>
		<i>email: admin@gmail.com</i><br>
		<i>password: admin1234</i>
			</form>
		</section>
	</main>
</template>
<script>
import { ref } from "vue";
import { useStore } from "vuex";
export default {
  name: "LoginC",
  setup() {
    const login_form = ref({});
    const store = useStore();
    const login = () => {
      store.dispatch("login", login_form.value);
    };

    return {
      login_form,
      login,
    };
  },
};
</script>
<style>
.forms {
	display: flex;
	min-height: 100vh;
}

section form {
	flex: 1 1 0%;
	padding: 8rem 1rem 1rem;
}

h2 {
	font-size: 2rem;
	text-transform: uppercase;
	margin-bottom: 2rem;
}

input {
	appearance: none;
	border: none;
	outline: none;
	background: none;

	display: block;
	width: 100%;
	max-width: 400px;
	margin: 0 auto;
	font-size: 1.5rem;
	margin-bottom: 2rem;
	padding: 0.5rem 0rem;
}

input:not([type="submit"]) {
	opacity: 0.8;
	transition: 0.4s;
	border-bottom: 2px solid #090909;

}

input:focus:not([type="submit"]) {
	opacity: 1;
	border-bottom: 2px solid #090909;

}

input::placeholder {
	color: inherit;
} 


section form.login {
	color: #FFF;
	background-color: linear-gradient(to right, #d943bb, #40d9f1);
	background-image: linear-gradient(
		to bottom right,
			rgb(245, 66, 101) 0%,
		rgb(16, 227, 234) 100%
	);
} 

form.login input:not([type="submit"]) {
	color: #2c3e50;
	border-bottom: 2px solid #e8ebed;
}

form.login input[type="submit"] {
	background-color: rgb(245, 66, 101);
	color: #FFF;
	font-weight: 700;
	padding: 1rem 2rem;
	border-radius: 0.5rem;
	cursor: pointer;
	text-transform: uppercase;
}



</style>
