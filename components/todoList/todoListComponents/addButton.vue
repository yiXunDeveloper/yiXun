<template>
	<view>
		<!-- 创建按钮 -->
		<view class="create-todo" @click="sonCreate">
			<text class="iconfont icon-add" :class="{'create-todo-activate':textShow}"></text>
		</view>
		<!-- 输入框 -->
		<view v-if="activate" class="create-content" :class="{'create-show':textShow}">
			<view class="create-content-box">
				<!-- input输入 -->
				<view class="create-input">
					<input type="text" v-model="value" placeholder="速记你的所思所想…" />
				</view>
				<!-- 发布按钮 -->
				<view class="create-button" @click="sonAdd">
					创建
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: [],
		data() {
			return {
				value: '',
				activate: false,
				textShow: false,
			};
		},
		methods: {
			sonCreate() {
				if (this.activate) {
					this.close()
				} else {
					this.open()
				}
			},
			//打开动画
			open() {
				this.activate = true
				this.$nextTick(() => {
					setTimeout(() => {
						this.textShow = true
					}, 50)
				})
			},
			//关闭动画
			close() {
				this.textShow = false
				this.$nextTick(() => {
					setTimeout(() => {
						this.activate = false
					}, 350)
				})
			},
			sonAdd() {
				if (this.value === '') {
					uni.showToast({
						title: "请输入具体内容",
						icon: "none"
					})
					return
				}
				let sonData = {
					id: 'id' + new Date().getTime(),
					content: this.value,
					checked: false,
				}
				this.$emit('sonAdd', sonData)
				this.value = ''
				this.close()
			},
		}
	}
</script>

<style scoped>
	@import '../../../common/icon.css';

	.create-todo {
		display: flex;
		justify-content: center;
		align-items: center;
		position: fixed;
		margin: 0 auto;
		bottom: 20px;
		left: 0;
		right: 0;
		width: 50px;
		height: 50px;
		border-radius: 50%;
		background: #BDEFF5;
		box-shadow: -1px 1px 5px 2px rgba(0, 0, 0, 0.1), -1px 1px 1px 0 rgb(255, 255, 255) inset;
	}

	.icon-add {
		font-size: 30px;
		color: #ADD8E6;
	}

	.create-content {
		position: fixed;
		bottom: 95px;
		left: 20px;
		right: 20px;
		transition: all 0.3s;
		opacity: 0;
		transform: scale(0) translateY(200%);
	}

	.create-show {
		opacity: 1;
		transform: scale(1) translateY(0);
	}

	.create-content-box {
		display: flex;
		align-items: center;
		padding: 0 15px;
		padding-right: 0;
		border-radius: 50px;
		background: #DEEFF5;
		box-shadow: -1px 1px 5px 2px rgba(0, 0, 0, 0.1), -1px 1px 1px 0 rgba(255, 255, 255) inset;
		z-index: 2;
	}

	.create-input {
		width: 100%;
		padding-right: 15px;
		color: #ADD8E6;
	}

	.create-button {
		display: flex;
		justify-content: center;
		align-items: center;
		flex-shrink: 0;
		width: 80px;
		height: 50px;
		border-radius: 50px;
		font-size: 16px;
		color: #88D4EC;
		box-shadow: -2px 0px 2px 1px rgba(0, 0, 0, 0.1);
	}

	.create-content:after {
		content: '';
		position: absolute;
		right: 0;
		left: 0;
		bottom: -8px;
		margin: 0 auto;
		width: 20px;
		height: 20px;
		background: #DEEFF5;
		transform: rotate(45deg);
		box-shadow: 1px 1px 5px 2px rgba(0, 0, 0, 0.1);
		z-index: -1;
	}

	.create-content-box:after {
		content: '';
		position: absolute;
		right: 0;
		left: 0;
		bottom: -8px;
		margin: 0 auto;
		width: 20px;
		height: 20px;
		background: #DEEFF5;
		transform: rotate(45deg);
	}

	.icon-add {
		transition: transform 0.3s;
	}

	.create-todo-activate {
		transform: rotate(135deg);
	}
</style>
