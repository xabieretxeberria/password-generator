<template>
	<div id="password-generator-app">
		<form>
			<label for="pass-length">Password length: </label>
			<input id="pass-length" type="number" v-model="passwordLength" min="4" max="12" />
		</form>
	</div>
</template>

<script>
export default {
	data() {
		return {
			passwordLength: 4
		}
	}
}
</script>

<style scoped>

</style>