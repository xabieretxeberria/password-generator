<template>
	<div id="password-generator-app">
		<form>
			<label for="pass-length">Password length: </label>
			<input id="pass-length" type="number" v-model="passwordLength" min="4" max="12" @change="removePassword" />
			<br/>
			<label for="pass-uppercase">Include uppercase letters: </label>
			<input id="pass-uppercase" type="checkbox" v-model="options.passwordUppercase" @change="removePassword" />
			<br/>
			<label for="pass-lowercase">Include lowercase letters: </label>
			<input id="pass-lowercase" type="checkbox" v-model="options.passwordLowercase" @change="removePassword" />
			<br/>
			<label for="pass-numbers">Include numbers: </label>
			<input id="pass-numbers" type="checkbox" v-model="options.passwordNumbers" @change="removePassword" />
			<br/>
			<label for="pass-symbols">Include symbols: </label>
			<input id="pass-symbols" type="checkbox" v-model="options.passwordSymbols" @change="removePassword" />
			<br/>
			<div id="generated-password" v-if="generatedPassword">
				Your password: {{ generatedPassword }}
			</div>
			<div class="error" v-if="error.hasError">
				{{ error.errorMsg }}
			</div>
			<button type="button" @click="generatePassword">Generate password</button>
		</form>
	</div>
</template>

<script>
export default {
	data() {
		return {
			passwordLength: 4,
			options: {
				passwordUppercase: false,
				passwordLowercase: false,
				passwordNumbers: false,
				passwordSymbols: false,
			},
			generatedPassword: '',
			error: {
				hasError: false,
				errorMsg: '',
			},
		}
	},
	methods: {
		generatePassword() {
			if (this.noOptionsSelected()) {
				this.error.hasError = true;
				this.error.errorMsg = 'No options selected!'
				return;
			}
			this.error.hasError = false;
			this.removePassword();

			let possibleCharacters = '';

			if (this.options.passwordUppercase) possibleCharacters += 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
			if (this.options.passwordLowercase) possibleCharacters += 'abcdefghijklmnopqrstuvwxyz';
			if (this.options.passwordNumbers) possibleCharacters += '0123456789';
			if (this.options.passwordSymbols) possibleCharacters += '!#$%&()*+,-./:;<=>?@[\\]^_{|}~';

			while (this.generatedPassword.length < this.passwordLength) {
				this.generatedPassword += possibleCharacters.charAt(Math.floor(possibleCharacters.length * Math.random()));
			}
		},
		removePassword() {
			this.generatedPassword = '';
		},
		noOptionsSelected() {
			return Object.values(this.options).every(x => x === false);
		}
	}
}
</script>

<style scoped>

</style>