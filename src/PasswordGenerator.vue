<template>
	<div id="password-generator-app">
		<form>
			<label for="pass-length">Password length: </label>
			<input id="pass-length" type="number" v-model="passwordLength" min="4" max="12" />
			<br/>
			<label for="pass-uppercase">Include uppercase letters: </label>
			<input id="pass-uppercase" type="checkbox" v-model="passwordUppercase" />
			<br/>
			<label for="pass-lowercase">Include lowercase letters: </label>
			<input id="pass-lowercase" type="checkbox" v-model="passwordLowercase" />
			<br/>
			<label for="pass-numbers">Include numbers: </label>
			<input id="pass-numbers" type="checkbox" v-model="passwordNumbers" />
			<br/>
			<label for="pass-symbols">Include symbols: </label>
			<input id="pass-symbols" type="checkbox" v-model="passwordSymbols" />
		</form>
	</div>
</template>

<script>
export default {
	data() {
		return {
			passwordLength: 4,
			passwordUppercase: false,
			passwordLowercase: false,
			passwordNumbers: false,
			passwordSymbols: false
		}
	}
}
</script>

<style scoped>

</style>