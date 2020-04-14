<template>
	<!-- todo-finish -->
	<view class="todo-list" :class="{'todo-finish':checkOrNot}" @click="handleFinish()">
		<view class="todo-list_checkbox">
			<view class="checkbox"></view>
		</view>
		<view class="tood-list_content">
			{{content}}
		</view>
	</view>
</template>

<script>
	export default {
		props: ['content', 'dataId', 'checkOrNot'],
		data() {
			return {

			};
		},
		methods: {
			handleFinish() {
				this.$emit('handleFinish', this.dataId)
			}
		}
	}
</script>

<style scoped>
	.todo-list {
		position: relative;
		display: flex;
		align-items: center;
		padding: 15px;
		margin: 15px;
		color: #0C3854;
		font-size: 14px;
		border-radius: 10px;
		background: #CFEBFD;
		box-shadow: -1px 1px 5px 1px rgba(0, 0, 0, 0.1), -1px 2px 1px 0 rgba(255, 255, 255) inset;
		overflow: hidden;
	}

	.todo-list::after {
		position: absolute;
		content: '';
		top: 0;
		bottom: 0;
		left: 0;
		width: 5px;
		background-color: #91D1E8;
	}

	.todo-list_checkbox {
		padding-right: 15px;
	}

	.checkbox {
		width: 20px;
		height: 20px;
		border-radius: 50%;
		background: #FFFFFF;
		box-shadow: 0 0 5px 1px rgba(0, 0, 0, 0.1);
	}

	.todo-finish .checkbox {
		position: relative;
		background: #EEE;
	}

	.todo-finish .checkbox:after {
		content: '';
		position: absolute;
		width: 10px;
		height: 10px;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		margin: auto;
		border-radius: 50%;
		background: #CFEBFD;
		box-shadow: 0 0 2px 0px rgba(0, 0, 0, 0.2) inset;
	}

	.todo-finish .tood-list_content {
		color: #99999;
	}

	.todo-finish.todo-list:before {
		content: '';
		position: absolute;
		top: 0;
		bottom: 0;
		left: 40px;
		right: 10px;
		height: 2px;
		margin: auto 0;
		background-color: #BDCDD8;
	}

	.todo-finish.todo-list:after {
		background: #CCCCCC;
	}
</style>
