<template>
	<!-- 列表样式 -->
	<view class="p-2">
		<!-- 头像昵称|关注按钮 -->
		<view class="flex align-center justify-between">
			<view class="flex align-center">
				<!-- 头像 -->
				<image class="rounded-circle mr-2" :src="item.userpic" style="width: 65rpx;
					height: 65rpx;" lazy-load @click="openSpace"></image>
				<!-- 昵称发布时间 -->
				<view class="">
					<view class="font" style="line-height: 1.5;">
						{{item.username}}
					</view>
					<text class="font-sm text-light-muted" style="line-height: 1.5;">
						{{item.newstime}}
					</text>
				</view>
			</view>

			<!-- 按钮 -->
			<view @click="follow" class="flex align-center justify-center rounded bg-main text-white animated faster"
			 hover-class="rubberBand" :class="{'bg-main1': isfollowAct}" style="width: 90rpx;height: 50rpx;">
				关注
			</view>
		</view>
		<!-- 标题 -->
		<view class="font my-1" @click="openDetail">
			{{item.title}}
		</view>
		<!-- 图片 -->
		<image @click="openDetail" v-if="item.titlepic" :src="item.titlepic" style="height: 350rpx;" class="rounded w-100"></image>
		<!-- 图标按钮 -->
		<view class="flex align-center">
			<view class="flex flex-1 justify-center align-center animated faster" hover-class="jello text-main1" @click="doSupport('support')">
				<text class="iconfont icon-ziyuan1 mr-2"></text>
				<text>{{item.support.support_count}}</text>
			</view>
			<view class="flex flex-1 justify-center align-center animated faster" hover-class="jello text-main" @click="doSupport('unsupport')">
				<text class="iconfont icon-tubiao_diancai mr-2"></text>
				<text>{{item.support.unsupport_count}}</text>
			</view>
			<view class="flex flex-1 justify-center align-center animated faster" hover-class="jello text-main" @click="openDetail">
				<text class="iconfont icon-ziyuan mr-2"></text>
				<text>{{item.comment_count}}</text>
			</view>
			<view class="flex flex-1 justify-center align-center mr-2 animated faster" hover-class="jello text-main" @click="openDetail">
				<text class="iconfont icon-fenxiang"></text>
				<text>{{item.share_num}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			item: Object,
			index: Number
		},
		data() {
			return {
				isfollowAct: false,
			};
		},
		methods: {
			// 打开个人空间
			openSpace() {
				console.log("打开个人空间")
			},
			// 关注
			follow() {
				console.log("关注与否")
				this.isfollowAct = !this.isfollowAct
			},
			// 进入详情页
			openDetail() {
				console.log("进入详情页")
			},
			// 顶踩操作
			doSupport(type) {
				console.log(type)
			}

		}
	}
</script>

<style>
</style>
