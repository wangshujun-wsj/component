<template>
  <div class="hello">
  	
    <div style="margin-left: 20px;" v-show="visible">
    	
    	<h1>{{ banner }}</h1>
    	
	    <div style="width: 200px;">
	    
	  	  <v-menu :menu="menu" @addMenu = "add" @listenOpen = "open" @listenDel = "del"></v-menu>
	    	<br />
	    	<combobox @change="change" :placeholder="placeholder" :text="text" :options="options" ></combobox>
	    </div>
	  </div>
  </div>
</template>

<script>
	import combobox from './combobox.vue'
	import menu from './menu.vue'
	import {mapGetters, mapActions} from 'vuex'
export default {
  name: 'hello',
  data () {
    return {
    	menu: [{
						id: 1,
						title: '导航一',
						menuItem: [{
								id: 2,
								name: "分组一",
								menuOptions: [{
									id: 3,
									name: '选项一'
								}, {
									id: 4,
									name: '选项二'
								}]
							},
							{
								id: 5,
								name: "分组二",
								menuOptions: [{
									id: 6,
									name: '选项一'
								}, {
									id: 7,
									name: '选项二'
								}]
							}
						]
					},
					{
						id: 8,
						title: '导航二',
						menuItem: [{
								id: 9,
								name: "分组三",
								menuOptions: [{
									id: 10,
									name: '选项一'
								}, {
									id: 11,
									name: '选项二'
								}]
							},
							{
								id: 12,
								name: "分组四",
								menuOptions: [{
									id: 13,
									name: '选项一'
								}, {
									id: 14,
									name: '选项二'
								}]
							}
						]
					}
				],
    	
    	
    	placeholder: "请选择内容",
    	text: '电气1',
    	options: [
				{id:1,name:'电气1'},
				{id:2,name:'电气2'},
				{id:3,name:'电气3'},
				{id:4,name:'电气4'}
			],
			menu: [
					{id:1,title:'导航一',menuItem:[
						{id:2,name:"分组一",menuOptions:[{id:3,name:'选项一'},{id:4,name:'选项二'}]},
						{id:5,name:"分组二",menuOptions:[{id:6,name:'选项一'},{id:7,name:'选项二'}]}]
					},
					{id:8,title:'导航二',menuItem:[
						{id:9,name:"分组三",menuOptions:[{id:10,name:'选项一'},{id:11,name:'选项二'}]},
						{id:12,name:"分组四",menuOptions:[{id:13,name:'选项一'},{id:14,name:'选项二'}]}]
					}
				]
    }
  },
  computed: {
  	...mapGetters([
      'banner','visible' // 和 其他计算属性一样使用
    ])
  },
  components: {
  	combobox,
  	"v-menu" :menu
  },
  methods: {
  	change(val) {
  		console.log(val)
  		this.text = val;
  	},
  	open(val) {
  		alert(val)
  	},
  	del(val) {
  		let del = confirm("确定要删除吗!");
  		if(del) {
  			this.menu[val[0]].menuItem[val[1]].menuOptions.splice(val[2],1);
  		}
  	},
  	add(val) {
  		if(val[2]==="") {
  			alert("不能为空");
  			return ;
  		}
  		console.log(this.menu[val[0]].menuItem[val[1]])
  		this.menu[val[0]].menuItem[val[1]].menuOptions.push({name:val[2]});
  	},
  	handleNodeClick(data) {
        console.log(data);
      }
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	
</style>
