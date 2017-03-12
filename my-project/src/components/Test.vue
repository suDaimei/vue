<template>
	<div class="test">
		<h1>{{title}}</h1>
		<input v-model="newItem" v-on:keyup.enter="addNew">
		<ul>
			<li v-for='item in items' v-bind:class="{finished: item.isFinished}" v-on:click="toggleFinished(item)">
				{{item.label}}
			</li>
		</ul>
	</div>
	
</template>

<script>
import Store from './store'

	export default{
		name:'test',
		data(){
			return {
				title:'this is a todo list2',
				items:Store.fetch(),
				//[
					// {
					// 	label:'coding',
					// 	isFinished:false
					// },
					// {
					// 	label:'walking',
					// 	isFinished:true
					// },
					// {
					// 	label:'running',
					// 	isFinished:false
					// }
				//],
				newItem:''
			}
		},
		watch:{
			items:{
				handler: function(items){
					Store.save(items)
				},
				deep:true
			}
		},
		methods:{
			toggleFinished:function(item){
				item.isFinished=!item.isFinished
			},
			addNew:function(){
				this.items.push({
					label:this.newItem,
					isFinished:false
				})
				this.newItem=''
			}
		}
	}
</script>
<style>
.finished{color:red;}
li{list-style: none;
	padding:10px;}
</style>
