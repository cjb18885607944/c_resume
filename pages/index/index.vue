<template>
	<view class="index">
		<tui-skeleton v-if="skeletonShow" backgroundColor="#fafafa" borderRadius="10rpx"></tui-skeleton>
		<div class="head">
			<div class="info">
				<p class="name">
					<tui-icon name="card-fill" size="40" color="#337ab7"></tui-icon>
					<span>崔金榜</span>
				</p>
				<div class="contact">
					<span>
						<tui-icon name="computer" size="12" color="#666"></tui-icon>
						<span>两年工作经验</span>
					</span>|
					<span>
						<tui-icon name="strategy" size="12" color="#666"></tui-icon>
						<span>本科学历</span>
					</span>|
					<span>
						<tui-icon name="addressbook" size="12" color="#666"></tui-icon>
						<span>17685366134</span>
					</span>
				</div>
			</div>
			<image class="avatar" src="../../static/images/cui/avatar.jpg" mode="widthFix"></image>
		</div>
		<!-- 擅长 -->
		<view class="tui-progress-box" v-if="!skeletonShow">
			<tui-circular-progress percentText="H5C3" progressColor="#5677fc" color="#5677fc" :percentage="85"></tui-circular-progress>
			<tui-circular-progress percentText="JS" progressColor="#5677fc" color="#5677fc" :percentage="80"></tui-circular-progress>
			<tui-circular-progress percentText="Vue" progressColor="#5677fc" color="#5677fc" :percentage="80"></tui-circular-progress>
			<tui-circular-progress percentText="小程序" progressColor="#5677fc" color="#5677fc" :percentage="75"></tui-circular-progress>
		</view>
		<!-- 九宫格技能 -->
		<tui-divider dividerColor="#5677fc" color="#5677fc">技能点</tui-divider>
		<tui-grid>
			<block v-for="(item,index) in dataList" :key="index">
				<tui-grid-item :cell="4">
					<text class="tui-grid-label">{{item.name}}</text>
				</tui-grid-item>
			</block>
		</tui-grid>
		
		<!-- 工作经验 -->
		<tui-divider dividerColor="#5677fc" color="#5677fc">工作经历</tui-divider>
		<tui-card :title="card[0].title" :tag="card[0].tag">
			<template v-slot:body>
				<view class="tui-default">
					对智能终端软件的前端模块开发与维护（angularJs）、重构
					;“上海交通大学资产管理系统”模块的开发(Vue)、根据需求开发不同功能模块。
				</view>
			</template>
			<template v-slot:footer>
				<view class="tui-default">
					angularJs、Vue、axios、webpack、ElementUI
				</view>
			</template>
		</tui-card>
		<tui-card :title="card[1].title" :tag="card[1].tag">
			<template v-slot:body>
				<view class="tui-default">
					负责PC端Web产品和移动Web产品的HTML/CSS/JS代码编写，解决web端和移动端适配问题，通过ajax进行前后端交互。
				</view>
			</template>
			<template v-slot:footer>
				<view class="tui-default">
					JavaScript、JQuery、Swiper、Zepto、Photoshop
				</view>
			</template>
		</tui-card>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				skeletonShow: true,
				card: [{
						title: {
							text: "上海万达信息股份有限公司"
						},
						tag: {
							text: "2019/7-2020/5"
						}
					},
					{
						title: {
							text: "贵州惠智电子技术有限责任公司",
						},
						tag: {
							text: "2018/6-2019/5",
						}
					}],
					dataList: [{
						name: "H5C3",
						size: 30
					}, {
						name: "JavaScript",
						size: 30
					}, {
						name: "jQuery",
						size: 30
					}, {
						name: "Vue",
						size: 30
					}, {
						name: "ElementUI",
						size: 30
					}, {
						name: "小程序",
						size: 30
					}, {
						name: "uniapp",
						size: 30
					}, {
						name: "Photoshop",
						size: 30
					}]
			}
		},
		onShow() {
			setTimeout(() => {
				this.skeletonShow = false
			}, 1000);
		}
	}
</script>

<style scoped>
	.h20{
		height: 20rpx;
	}
	.index{
		min-height: 100vh;
		background-color: #fff;
	}
	.head{
		display: flex;
		justify-content: space-between;
		align-items: center;
		height: 220rpx;
		padding: 10rpx;
	}
	.avatar{
		width: 120rpx;
		height: 120rpx;
		border-radius: 50%;
	}
	.info{
		font-size: 50rpx;
		color: #333333;
		font-weight: 300;
		margin-left: 20rpx;
	}
	.name{
		display: flex;
		align-items: center;
	}
	.contact{
		font-size: 20rpx;
		color: #999;
	}
	.contact>span{
		padding: 0 15rpx;
	}
	.contact>span>span{
		margin-left: 10rpx;
	}
	.tui-progress-box{
		display: flex;
		justify-content: space-evenly;
		align-items: center;
	}
	.tui-default {
		padding: 20rpx 30rpx;
	}
	.tui-grid-icon {
		width: 64rpx;
		height: 64rpx;
		margin: 0 auto;
		text-align: center;
		vertical-align: middle;
	}
	.tui-grid-label {
		display: block;
		text-align: center;
		font-weight: 400;
		color: #333;
		font-size: 28rpx;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
		margin-top: 10rpx;
	}
</style>
