<template>
	<view>
		<tui-skeleton v-if="skeletonShow" backgroundColor="#fafafa" borderRadius="10rpx"></tui-skeleton>
		<div class="profile">
			<div class="info">
				<image src="../../static/images/cui/avatar.jpg" mode="widthFix" class="avatar"></image>
				<p class="nickname">崔金榜</p>
			</div>
			<view>
				<tui-list-cell @tap="showResume" :arrow="true">
					<tui-icon name="order" size="18" color="#337ab7"></tui-icon>
					<span class="ml10">我的简历</span>
				</tui-list-cell>
			</view>
			<br>
			<view @tap="copyLink" data-link="1404165423">
				<tui-list-cell :arrow="true">
					<tui-icon name="qq" size="18" color="#337ab7"></tui-icon>
					<span class="ml10">QQ：1404165423</span>
				</tui-list-cell>
			</view>
			<view @tap="copyLink" data-link="cc14041">
				<tui-list-cell :arrow="true">
					<tui-icon name="wechat" size="18" color="#19be6b"></tui-icon>
					<span class="ml10">微信：cc14041</span>
				</tui-list-cell>
			</view>
			<view @tap="copyLink" data-link="jinbangi@163.com">
				<tui-list-cell :arrow="true">
					<tui-icon name="mail" size="18" color="#337ab7"></tui-icon>
					<span class="ml10">我的邮箱：jinbangi@163.com</span>
				</tui-list-cell>
			</view>
			<view @tap="copyLink" data-link="www.cuishushu.cn">
				<tui-list-cell :arrow="true">
					个人博客：www.cuishushu.cn
				</tui-list-cell>
			</view>
			<view @tap="sendLink">
				<tui-list-cell :arrow="true">
					<tui-icon name="mail" size="18" color="#337ab7"></tui-icon>
					<span class="ml10">分享</span>
				</tui-list-cell>
			</view>
		</div>
	</view>
</template>

<script>
	const thorui = require("@/components/common/tui-clipboard/tui-clipboard.js")
	export default {
		data() {
			return {
				skeletonShow: true
			}
		},
		onShow() {
			setTimeout(() => {
				this.skeletonShow = false
			}, 1000);
		},
		onHide(){
			this.skeletonShow = true
		},
		methods:{
			copyLink(e) {
				let link = e.currentTarget.dataset.link
				thorui.getClipboardData(link, (res) => {
					// #ifdef H5 || MP-ALIPAY
					if (res) {
						this.tui.toast("链接复制成功")
					} else {
						this.tui.toast("链接复制失败")
					}
					// #endif
				})
			},
			sendLink(){
				uni.share({
				    provider: "weixin",
				    scene: "WXSceneSession",
				    type: 1,
				    summary: "点击查看崔金榜的简历小程序",
				    success: function (res) {
				        console.log("success:" + JSON.stringify(res));
				    },
				    fail: function (err) {
				        console.log("fail:" + JSON.stringify(err));
				    }
				});
			}
		}
	}
</script>

<style scoped>
	.ml10{
		margin-left: 20rpx;
	}
	.profile{
		min-height: 100vh;
		background-color: #eeeeee;
	}
	.info{
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		height: 260rpx;
		background-color: #3f3f44;
	}
	.avatar{
		border-radius: 50%;
		width: 120rpx;
		height: 120rpx;
		padding: 0;
	} 
	.nickname{
		font-size: 40rpx;
		margin-top: 20rpx;
		color: #FFF;
	}
</style>
