<template>
	<view class="container">
		<image src="../../static/banner2.jpg" mode="widthFix" class="banner2"></image>
		<view class="main1">
			<image src="../../static/title3.png" mode="widthFix" class="title1"></image>

			<view class="survey box1">
				<view class="topic">
					<view class="title">进食</view>
					<view class="option" v-for="(item, index) in topic1" @click="radioChange(index, item.type)">
						<image src="../../static/activeicon.png" mode="" v-if="item.isActive" class="radioicon"></image>
						<image src="../../static/icon.png" mode="" class="radioicon" v-else></image>
						<text class="text">{{ item.text }}</text>
					</view>
				</view>
			</view>
			<view class="survey box1">
				<view class="topic">
					<view class="title">穿衣</view>
					<view class="option" v-for="(item, index) in topic2" @click="radioChange(index, item.type)">
						<image src="../../static/activeicon.png" mode="" v-if="item.isActive" class="radioicon"></image>
						<image src="../../static/icon.png" mode="" class="radioicon" v-else></image>
						<text class="text">{{ item.text }}</text>
					</view>
				</view>
			</view>
			<view class="survey box1">
				<view class="topic">
					<view class="title">大小便控制</view>
					<view class="option" v-for="(item, index) in topic3" @click="radioChange(index, item.type)">
						<image src="../../static/activeicon.png" mode="" v-if="item.isActive" class="radioicon"></image>
						<image src="../../static/icon.png" mode="" class="radioicon" v-else></image>
						<text class="text">{{ item.text }}</text>
					</view>
				</view>
			</view>

			<view class="survey box1">
				<view class="topic">
					<view class="title">用厕</view>
					<view class="option" v-for="(item, index) in topic4" @click="radioChange(index, item.type)">
						<image src="../../static/activeicon.png" mode="" v-if="item.isActive" class="radioicon"></image>
						<image src="../../static/icon.png" mode="" class="radioicon" v-else></image>
						<text class="text">{{ item.text }}</text>
					</view>
				</view>
			</view>

			<view class="survey box1">
				<view class="topic">
					<view class="title">洗澡</view>
					<view class="option" v-for="(item, index) in topic5" @click="radioChange(index, item.type)">
						<image src="../../static/activeicon.png" mode="" v-if="item.isActive" class="radioicon"></image>
						<image src="../../static/icon.png" mode="" class="radioicon" v-else></image>
						<text class="text">{{ item.text }}</text>
					</view>
				</view>
			</view>

			<view class="survey box1">
				<view class="topic">
					<view class="title">床椅转移</view>
					<view class="option" v-for="(item, index) in topic6" @click="radioChange(index, item.type)">
						<image src="../../static/activeicon.png" mode="" v-if="item.isActive" class="radioicon"></image>
						<image src="../../static/icon.png" mode="" class="radioicon" v-else></image>
						<text class="text">{{ item.text }}</text>
					</view>
				</view>
			</view>

			<image src="../../static/submit.png" mode="widthFix" class="submit" @click="submit()"></image>
		</view>

		<!-- 提交成功模态框 -->
		<uni-popup ref="popup">

			<view class="popupbox">
				<image src="../../static/submitreminder.png" class="bannericon"></image>
				<view class="content">
					<view class="tit">
						资料提交成功
					</view>
					<view class="text">
						您的评估结果为:{{grade1}}
					</view>
					<view class="text char1" v-if="isPass">
						请等候工作人员联系您
					</view>
					<view class="text char2" v-else>
						未通过长护险评估
					</view>
					<view class="mybutton" @click="close()">我知道了</view>
				</view>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				isPass: null,
				grade1: null,
				form: {
					eat: 2,
					dress: 2,
					defecateControl: 2,
					toilet: 2,
					takeashower: 2,
					bedchairMove: 2
				},
				topic1: [{
						type: 1,
						text: '独立，无需帮助',
						isActive: true
					},
					{
						type: 1,
						text: '部分独立，自己能吃，但需辅助',
						isActive: false
					},
					{
						type: 1,
						text: '不能独立完成，部分或全部靠喂食或鼻饲',
						isActive: false
					}
				],
				topic2: [{
						type: 2,
						text: '独立，无需帮助，能独立拿取衣服，穿上并扣好',
						isActive: true
					},
					{
						type: 2,
						text: '部分独立，能独立拿取衣服及穿上，需帮助系鞋带',
						isActive: false
					},
					{
						type: 2,
						text: '不能独立完成，完全不能穿，要靠他人拿衣穿衣或自己穿上部分',
						isActive: false
					}
				],
				topic3: [{
						type: 3,
						text: '独立，自己能够完全控制',
						isActive: true
					},
					{
						type: 3,
						text: '部分独立，偶尔失控',
						isActive: false
					},
					{
						type: 3,
						text: '不能自控，失控，需帮助处理大小便，如导尿，灌肠等',
						isActive: false
					}
				],
				topic4: [{
						type: 4,
						text: '独立，无需帮助，能独立用厕、便后拭净及整理衣裤，可用手杖、助步器或轮椅，能处理便盆，尿壶',
						isActive: true
					},
					{
						type: 4,
						text: '不能独立完成，需要帮助入厕、做便后处理，清洁、整理衣裤及处理便盆、尿壶',
						isActive: false
					},
					{
						type: 4,
						text: '不能独立完成，不能用厕',
						isActive: false
					}
				],
				topic5: [{
						type: 5,
						text: '独立，无需帮助，自己能进出浴室，淋浴、浴盆，独立洗澡',
						isActive: true
					},
					{
						type: 5,
						text: '部分独立，需帮助洗一部分，背部或腿',
						isActive: false
					},
					{
						type: 5,
						text: '不能独立完成，不能洗澡、或大部分需要帮助洗',
						isActive: false
					}
				],
				topic6: [{
						type: 6,
						text: '独立，无需帮助，能自己下场，坐上及离开椅，凳，可用手杖、助步器',
						isActive: true
					},
					{
						type: 6,
						text: '不能独立完成，需帮助上、下床椅',
						isActive: false
					},
					{
						type: 6,
						text: '不能独立完成，卧床不起',
						isActive: false
					}
				]
			}
		},
		methods: {

			// 自定义单选
			radioChange(index, type) {
				let score // 表示选项的得分
				if (index == 0) {
					score = 2
				}
				if (index == 1) {
					score = 1
				}
				if (index == 2) {
					score = 0
				}
				console.log(score)
				if (type == 1) {
					console.log(type, index)
					this.topic1.forEach(item => {
						item.isActive = false
					}) // 先把所有的单选状态变为false
					this.topic1[index].isActive = true // 勾选状态变为true
					this.form.eat = score //赋值到data
				}
				if (type == 2) {
					console.log(type, index)
					this.topic2.forEach(item => {
						item.isActive = false
					})
					this.topic2[index].isActive = true
					this.form.dress = score //赋值到data
				}
				if (type == 3) {
					console.log(type, index)
					this.topic3.forEach(item => {
						item.isActive = false
					})
					this.topic3[index].isActive = true
					this.form.defecateControl = score //赋值到data
				}
				if (type == 4) {
					console.log(type, index)
					this.topic4.forEach(item => {
						item.isActive = false
					})
					this.topic4[index].isActive = true
					this.form.toilet = score //赋值到data
				}
				if (type == 5) {
					console.log(type, index)
					this.topic5.forEach(item => {
						item.isActive = false
					})
					this.topic5[index].isActive = true
					this.form.takeashower = score //赋值到data
				}
				if (type == 6) {
					console.log(type, index)
					this.topic6.forEach(item => {
						item.isActive = false
					})
					this.topic6[index].isActive = true
					this.form.bedchairMove = score //赋值到data
				}
			},
			// 提交表单
			submit() {
				console.log(this.form)
				// //表单非空验证
				// let flag = Object.values(this.form).every(function(item) {
				// 	return item != 0 | 1 | 2
				// })
				// console.log(flag)
				// if (flag == false) {
				// 	uni.showToast({
				// 		title: '有未填选项',
				// 		icon: 'none'
				// 	})
				// 	return
				// }
				uni.request({
					method: "POST",
					url: 'https://www.qycloud.com.cn/bee/open-72810619931328627/xhll/Level/numberTwo',
					data: {
						id: 666,
						eat: this.form.eat,
						dress: this.form.dress,
						defecateControl: this.form.defecateControl,
						toilet: this.form.toilet,
						takeashower: this.form.takeashower,
						bedchairMove: this.form.bedchairMove
					},
					success: (res) => {
						console.log(res)
						console.log(res.data.data.grade)
						// 赋值评级
						this.grade1 = res.data.data.grade
						console.log(this.grade1)
						// 判断是否通过评估
						this.isPassWay()
						// 弹出成功提示框
						this.open()
					}
				})

			},
			// 判断是否通过评估
			isPassWay() {
				console.log('等级：', this.grade1)
				if (this.grade1 == 'A' || 'B' || 'C' || 'D') {

					this.isPass = false
					console.log('未通过')
					return
				} else {
					this.isPass = true
					console.log('通过评估')
					return
				}
			},
			// 提交成功提示框
			open() {
				// 通过组件定义的ref调用uni-popup方法 ,如果传入参数 ，type 属性将失效 ，仅支持 ['top','left','bottom','right','center']
				this.$refs.popup.open('center')
			},
			close() {
				this.$refs.popup.close()
			}
		}
	}
</script>

<style lang="less">
	.container {
		position: relative;

		.banner2 {
			width: 750rpx;
			height: 4000rpx;
			z-index: -99;
		}

		// 表单区域
		.main1 {
			position: absolute;
			top: 84rpx;
			left: 45rpx;
			height: 3700rpx;
			width: 658rpx;
			background-color: #ffffff;
			border-radius: 10rpx;

			.title1 {
				position: absolute;
				top: -50rpx;
				left: 50%;
				transform: translateX(-50%);
			}

			.survey {
				overflow: hidden;
				padding: 0 48rpx 0 30rpx;
				width: 629rpx;
				height: 422rpx;
				background: #fdf8f6;
				border-radius: 16rpx;
				margin: 50rpx auto;

				.title {
					margin: 35rpx 0 39rpx;
					text-align: center;
					font-size: 32rpx;
					font-family: PingFang SC;
					font-weight: 500;
					color: #e9635d;
				}

				// 题目选项
				.option {
					display: flex;
					align-items: center;
					margin-bottom: 54rpx;
					height: 50rpx;

					.radioicon {
						width: 53rpx;
						height: 47rpx;
						margin-right: 33rpx;
					}

					.text {
						width: 500rpx;
						font-size: 24rpx;
						font-family: PingFang SC;
						font-weight: 400;
						color: #463738;
					}
				}
			}

			.box1 {
				margin: 122rpx auto;
			}
		}

		.myRadio {
			padding: 20rpx 48rpx 0 30rpx;
			width: 629rpx;
			height: 250rpx;
			background: #fdf8f6;
			border-radius: 16rpx;
			margin: 50rpx auto;

			.title {
				margin: 35rpx 0 39rpx;
				text-align: center;
				font-size: 32rpx;
				font-family: PingFang SC;
				font-weight: 500;
				color: #e9635d;
			}
		}

		.submit {
			position: absolute;
			bottom: 170rpx;
			left: 50%;
			transform: translateX(-50%);
			width: 300rpx;
			height: 80rpx;
		}

		.popupbox {
			position: relative;
			background-color: #FFFFFF;
			width: 400rpx;
			height: 450rpx;
			border-radius: 40rpx;

			.bannericon {
				position: absolute;
				top: -7%;
				left: 50%;
				transform: translateX(-50%);
				width: 203rpx;
				height: 198rpx;
			}

			.content {
				padding-top: 190rpx;
				text-align: center;

				.tit {
					font-size: 32rpx;
					font-family: PingFang SC;
					font-weight: 400;
					color: #333333;
					margin-bottom: 17rpx;
				}

				.text {
					font-size: 28rpx;
					font-family: PingFang SC;
					font-weight: 400;
					color: #999999;
				}

				.mybutton {
					width: 280rpx;
					height: 100rpx;
					margin: 22rpx auto 0;
					background: url(../../static/mybutton.png) no-repeat;
					background-size: 100%;
					line-height: 100rpx;
					color: #FFFFFF;
					font-size: 32rpx;
					font-family: PingFang SC;
				}
			}
		}

	}
</style>
