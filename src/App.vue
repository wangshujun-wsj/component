<template>
  <div id="app">
    <v-nav></v-nav>
    <Hello></Hello>
  </div>
</template>

<script type="text/ecmascript-6">
	
 
	import nav from './components/nav.vue';
	import Hello from './components/Hello.vue';
	export default {
	  name: 'app',
	  data() {
	  	return {
	  	}
	  },
	 	components: {
	    'v-nav': nav,
	    Hello
	  }
	}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
li {
  	text-decoration: none;
  	list-style-type: none;
}
* {
	margin: 0;
	padding: 0;
}
</style>
