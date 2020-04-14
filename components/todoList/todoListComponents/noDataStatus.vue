<template>
	<view class="default">
		<view class="image-default">
			<image src="../../../static/default.png" mode="aspectFit" lazy-load></image>
		</view>
		<view class="default-info">
			<view class="default-info_text">
				您还没有创建任何待办事项
			</view>
			<view class="default-info_text">
				点击下方+号创建一个吧
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		}
	}
</script>

<style scoped>
	.image-default {
		display: flex;
		justify-content: center;
	}

	.image-default image {
		width: 100%;
	}

	.default {
		padding-top: 50px;
	}

	.default-info_text {
		text-align: center;
		font-size: 14px;
		color: #CCCCCC;
	}
</style>
