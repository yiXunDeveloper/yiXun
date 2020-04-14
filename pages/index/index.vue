<template>
	<view>
		<block v-for="(item, index) in list" :key="index">
			<!-- 列表 -->
			<common-list :item="item" :index="index"></common-list>
			<!-- 全局分割线 -->
			<divider></divider>
		</block>
	</view>
</template>

<script>
	import commonList from '@/components/common/common-list.vue'
	export default {
		components: {
			commonList
		},
		data() {
			return {
				list: [{
						username: "昵称",
						userpic: "/static/common/headerico.png",
						newstime: "2019-10-29 下午 4:30",
						isFollow: false,
						title: "我是标题",
						titlepic: "/static/common/hunye.png",
						support: {
							type: "support",
							support_count: 1,
							unsupport_count: 2
						},
						comment_count: 2,
						share_num: 2
					},
					{
						username: "昵称",
						userpic: "/static/common/headerico.png",
						newstime: "2019-10-29 下午 4:30",
						isFollow: false,
						title: "我是标题",
						titlepic: "",
						support: {
							type: "support",
							support_count: 1,
							unsupport_count: 2
						},
						comment_count: 2,
						share_num: 2
					}
				]
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>

</style>
