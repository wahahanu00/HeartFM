<template>
	<view>
		<audio :src=url controls="controls"></audio>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				url:""
			}
		},
		onLoad(e){
			console.log("1111")
			console.log(e)
			this.url='http://yiapi.xinli001.com/fm/media-url.mp3?id='+e.id
			console.log(this.url)
		},
		
		methods: {
			
		}
	}
</script>

<style>

</style>
