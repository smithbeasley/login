<template>
<section class="flex items-center justify-center text-center bg-neutral text-neutral-content mt-24 max-w-2xl mx-auto rounded-xl">

		<form @submit.prevent action="" class="flex flex-col w-full max-w-lg p-12 rounded shadow-lg">
			<label for="username" class="self-start text-xs font-semibold text-content-200">Username</label>
			
			<input id="username" type="text" class="flex items-center h-12 px-4 mt-2 rounded focus:outline-none focus:ring-2 text-coolGray-900" v-model="email">
			
			<label for="password" class="self-start mt-3 text-xs font-semibold text-content-200">Password</label>
			
			<input id="password" type="password" class="flex items-center h-12 px-4 mt-2 rounded focus:outline-none focus:ring-2 text-coolGray-900" v-model="password">
			
			<button type="submit" @click="login" class="btn btn-primary mt-7">Login</button>

			<button type="submit" @click="newUser" class="btn btn-primary mt-7">Sign Up</button>

			
			
		</form>

	</section>
</template>

<script setup>
import {ref} from 'vue'
import {useRouter} from 'vue-router'
import {signIn} from '../helpers/useAuth'
import {signUp} from '../helpers/useAuth'
const router = useRouter()
const login= async() => {
	try {
		await signIn(email.value,password.value)
	router.push('/')
	} catch (error) {
	console.log(error)	
	}
	}
const newUser= async() => {
	try {
		signUp(email.value,password.value)
	router.push('/')
	} catch (error) {
	console.log(error)	
	}
	}
const email = ref('')
const password = ref('')
</script>