<template>
	<view class="content">
		<status-bar :barText="text" 
		:listLen="list.length" 
		:newListlength = "newLen"
		:activateBarIndex="activateIndex" 
		v-if="list.length !== 0" 
		@barTab="tab()">
		</status-bar>
		<!-- 没有数据的状态 -->
		<no-data-status v-if="list.length === 0"></no-data-status>
		<!-- 内容 -->
		<view v-else class="todo-content">
			<list-data 
			:content="item.content"
			:checkOrNot="item.checked"
			:dataId="item.id"
			v-for="(item, index) in listData" :key="index" 
			@handleFinish="finish()">
			</list-data>
		</view>
		<add-button @sonAdd="add()"></add-button>
	</view>
</template>

<script>
	import statusBar from './todoListComponents/statusBar.vue'
	import noDataStatus from './todoListComponents/noDataStatus.vue'
	import addButton from './todoListComponents/addButton.vue'
	import listData from './todoListComponents/listData.vue'
	export default {
		components: {
			statusBar: statusBar,
			noDataStatus: noDataStatus,
			listData: listData,
			addButton: addButton
		},
		data() {
			return {
				value: '',
				list: [],
				activateIndex: 0,
				text: '全部',
				newLen: 0
			}
		},
		onLoad() {

		},
		computed: {
			listData() {
				let list = JSON.parse(JSON.stringify(this.list))
				let newList = []
				//点击 全部
				if (this.activateIndex === 0) {
					this.text = "全部"
					console.log(list.length)
					return list
				}
				//点击 待办事项
				if (this.activateIndex === 1) {
					//checked  false
					list.forEach((item) => {
						if (!item.checked) {
							newList.push(item)
						}
					})
					this.text = "待办"
					this.newLen = newList.length
					return newList
				}
				//点击 已完成
				if (this.activateIndex === 2) {
					//checked  true
					list.forEach((item) => {
						if (item.checked) {
							newList.push(item)
						}
					})
					this.text = "已完成"
					this.newLen = newList.length
					return newList
				}
			}
		},
		methods: {
			add(sonData) {
				this.list.unshift({
					id: sonData.id,
					content: sonData.content,
					checked: sonData.checked
				})
			},
			//点击列表触发
			finish(dataId) {
				let index = this.list.findIndex((item) => item.id === dataId)
				this.list[index].checked = !this.list[index].checked
			},
			tab(e) {
				this.activateIndex = e
			}
		}
	}
</script>

<style scoped>
	.todo-content {
		position: relative;
		padding-top: 45px;
		padding-bottom: 60px;
	}
</style>
