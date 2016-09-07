<template>
	<div class="msg">
		<p>{{ message }}</p>
		<input v-model="message" name="">
	</div>
</template>
<script>
	export default {
		data(){
			return {
				message:'Hello Vue.js!'
			}
		}
	}
</script>