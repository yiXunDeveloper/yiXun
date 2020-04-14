<template>
	<!-- 状态栏 -->
	<view class="todo-header">
		<!-- 状态栏的左侧 -->
		<view class="todo-header_left">
			<text class="activate-text">{{barText}}</text>
			<text>{{dataLen}}条</text>
		</view>
		<!-- 状态栏的右侧 -->
		<view class="todo-header_right">
			<view class="todo-header_right-item" :class="{'activate-tab':activateBarIndex === 0}" @click="barTab(0)">
				全部
			</view>
			<view class="todo-header_right-item" :class="{'activate-tab':activateBarIndex === 1}" @click="barTab(1)">
				待办
			</view>
			<view class="todo-header_right-item" :class="{'activate-tab':activateBarIndex === 2}" @click="barTab(2)">
				已完成
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: ['barText', 'listLen', 'newListlength', 'activateBarIndex'],
		data() {
			return {
				dataLen: 0
			};
		},
		watch: {
			activateBarIndex: function() {
				if (this.activateBarIndex === 0) {
					this.dataLen = this.listLen
				} else {
					console.log(this.listLen)
					this.dataLen = this.newListlength
				}
			}
		},
		methods: {
			barTab(e) {
				this.$emit('barTab', e)
			}
		},
		beforeMount: function() {
			this.dataLen = this.listLen
		}
	}
</script>

<style scoped>
	.activate-text {
		font-size: 14px;
		color: #279ABF;
		padding-right: 10px;
	}

	.todo-header_right {
		flex-shrink: 0;
		display: flex;
	}

	.todo-header_right-item {
		padding: 0 5px;
	}

	.activate-tab {
		color: #279ABF;
	}

	.todo-header {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		display: flex;
		align-items: center;
		padding: 0 15px;
		font-size: 12px;
		color: #333333;
		height: 45px;
		box-sizing: border-box;
		box-shadow: -1px 1px 5px 0 rgba(0, 0, 0, 0.1);
		background-color: #FFFFFF;
		z-index: 10;
	}

	.todo-header_left {
		width: 100%;
	}

	.activate-text {
		font-size: 14px;
		color: #279ABF;
		padding-right: 10px;
	}

	.todo-header_right {
		flex-shrink: 0;
		display: flex;
	}

	.todo-header_right-item {
		padding: 0 5px;
	}

	.activate-tab {
		color: #279ABF;
	}
</style>
