<template>
  <div id="app">
	  <Header></Header>
	<router-view></router-view>
  </div>
</template>

<script>
	import Header from './components/Header.vue'
	export default {
		created(){
			console.log(this.$route.path)
		},
		components:{
			Header
		}
	}
</script>

<style lang="less">
  @import url("assets/css/global.css");
  @import  url("assets/css/iconfont.css");
</style>
