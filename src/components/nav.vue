<template>
  <div class="nav" >
  	<ul>
  		<li @click.stop="helloShow" v-text="msg"></li>
  		<li><input type="text" v-model="banner" @input="bannerI" /></li>
  	</ul>
  </div>
</template>

<script type="text/ecmascript-6">
 import {mapGetters, mapActions} from 'vuex'
	export default {
		name: 'nav',
		data() {
			return {
				msg:"点击",
				banner:'Welcome to Your Vue.js App'
			}
		},
		methods: {
			...mapActions([
				'helloShow' 
			]),
			bannerI() {
				// 传递带参数的 vuex
				this.$store.dispatch('bannerInput',this.banner);
			}
		}
	}
</script>

<style >
  .nav {
  	height: 50px;
  	width: 100%;
  	font-size: 14px;
  	background-color: #FAFAFA;
  }
  .nav li {
  	height: 50px;
  	width: 50px;
  	line-height: 50px;
  	display: inline-block;
  	text-align: center;
  	color: #292E35;
  	cursor: pointer;
  	-webkit-user-select: none;  /*谷歌禁止选择*/
  }
  .nav li:hover {
  	color: red;
  }
</style>