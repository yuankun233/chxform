<template>
	<view class="box">
		<image src="../../static/banner1.jpg" mode="widthFix"></image>
		<!-- 表单1 -->
		<view class="index_1">
			<image src="../../static/title1.png" mode="widthFix"></image>
			<view class="form111">
				<view class="index_1_text_3">
					<view>姓名</view>
					<view><input type="text" placeholder="请输入" v-model="form1.name" /></view>
				</view>
				<view class="index_1_text_3">
					<view>身份证号码:</view>
					<view><input type="text" placeholder="请输入" v-model="form1.ID" @blur="regExp($event,2,form1.ID,1)" />
					</view>
				</view>
				<view class="index_1_text_666">
					<view class="relation_1">性别：</view>
					<radio-group @change="radioChange($event, 1)" class="radios">
						<label class="relation">
							<radio value="男" />
							<text>男</text>
						</label>
						<label class="relation">
							<radio value="女" />
							<text>女</text>
						</label>
					</radio-group>
				</view>
				<view class="index_1_text_3">
					<view>年龄:</view>
					<view><input type="text" placeholder="请输入" v-model="form1.age" /></view>
				</view>
				<view class="index_1_text_3">
					<view>民族:</view>
					<view><input type="text" placeholder="请输入" v-model="form1.nation" /></view>
				</view>
				<view class="index_1_text_3">
					<view>参保地:</view>
					<view><input type="text" placeholder="请输入" v-model="form1.canbaodi" /></view>
				</view>
				<!-- 失能时间选择器 -->
				<view class="shinengTime">
					<view class="uni-title uni-common-pl title">失能时间:</view>
					<view class="uni-list select">
						<view class="uni-list-cell">

							<view class="uni-list-cell-db">
								<picker mode="date" :value="date" :start="startDate" :end="endDate"
									@change="bindDateChange">
									<view class="uni-input">{{date}}</view>
								</picker>
							</view>
						</view>
					</view>
				</view>

				<!-- <view class="index_1_text_3">
					<view>失能时间:</view>
					<view><input type="text" placeholder="请输入" v-model="form1.shinengTime" /></view>
				</view> -->
				<view class="index_1_text_666">
					<view class="relation_1">是否经过康复治疗：</view>
					<radio-group @change="radioChange($event, 2)" class="radios">
						<label class="relation">
							<radio value="是" />
							<text>是</text>
						</label>
						<label class="relation">
							<radio value="否" />
							<text>否</text>
						</label>
					</radio-group>
				</view>
				<!-- 治疗月数隐藏输入框 -->
				<view class="index_1_text_3" v-show="form1.isTreat=='是'">
					<view>治疗月数:</view>
					<view><input type="text" placeholder="请输入" v-model="treatMonth" /></view>
				</view>
				<view class="index_1_text_666">
					<view class="relation_1">是否首次申请：</view>
					<radio-group @change="radioChange($event, 3)" class="radios">
						<label class="relation">
							<radio value="是" />
							<text>是</text>
						</label>
						<label class="relation">
							<radio value="否" />
							<text>否</text>
						</label>
					</radio-group>
				</view>
				<view class="index_1_text_3">
					<view>联系电话:</view>
					<view><input type="text" placeholder="请输入" v-model="form1.phone"
							@blur="regExp($event,1,form1.phone,1)" />
					</view>
				</view>
				<view class="index_1_text_2">
					<view class="relation_1">保障方式：</view>
					<radio-group @change="radioChange($event, 4)" class="radios">
						<label class="relation">
							<radio value="职工基本医疗保险" />
							<text>职工基本医疗保险</text>
						</label>
						<label class="relation">
							<radio value="城乡居民基本医疗保险" />
							<text>城乡居民基本医疗保险</text>
						</label>
						<label class="relation">
							<radio value="特困供养" />
							<text>特困供养</text>
						</label>
						<label class="relation">
							<radio value="最低生活保障" />
							<text>最低生活保障</text>
						</label>
						<label class="relation">
							<radio value="其他" />
							<text>其他</text>
						</label>
					</radio-group>
				</view>

				<view class="index_1_text_2">
					<view class="relation_1">文化程度：</view>
					<radio-group @change="radioChange($event, 5)" class="radios">
						<label class="relation">
							<radio value="文盲" />
							<text>文盲</text>
						</label>
						<label class="relation">
							<radio value="小学" />
							<text>小学</text>
						</label>
						<label class="relation">
							<radio value="中学(含中专)" />
							<text>中学（含中专）</text>
						</label>
						<label class="relation">
							<radio value="大学(含大专)及以上" />
							<text>大学(含大专)及以上</text>
						</label>
					</radio-group>
				</view>
				<view class="index_1_text_2">
					<view class="relation_1">居住情况：</view>
					<radio-group @change="radioChange($event, 6)" class="radios">
						<label class="relation">
							<radio value="独居" />
							<text>独居</text>
						</label>
						<label class="relation">
							<radio value="与配偶/伴侣居住" />
							<text>与配偶/伴侣居住</text>
						</label>
						<label class="relation">
							<radio value="与子女居住" />
							<text>与子女居住</text>
						</label>
						<label class="relation">
							<radio value="与父母居住" />
							<text>与父母居住</text>
						</label>
						<label class="relation">
							<radio value="与兄弟姐妹居住" />
							<text>与兄弟姐妹居住</text>
						</label>
						<label class="relation">
							<radio value="与非亲属关系的人居住" />
							<text>与非亲属关系的人居住</text>
						</label>
					</radio-group>
				</view>
				<view class="index_1_text_3">
					<view>居住地:</view>
					<view><input type="text" placeholder="请输入" v-model="form1.livePlace" /></view>
				</view>
				<view class="index_1_text_2">
					<view class="relation_1">照护者：</view>
					<radio-group @change="radioChange($event, 7)" class="radios">
						<label class="relation">
							<radio value="配偶" />
							<text>配偶</text>
						</label>
						<label class="relation">
							<radio value="子女" />
							<text>子女</text>
						</label>
						<label class="relation">
							<radio value="亲友" />
							<text>亲友</text>
						</label>
						<label class="relation">
							<radio value="保姆" />
							<text>保姆</text>
						</label>
						<label class="relation">
							<radio value="护工" />
							<text>护工</text>
						</label>
						<label class="relation">
							<radio value="医疗人员" />
							<text>医疗人员</text>
						</label>
						<label class="relation">
							<radio value="没有任何人" />
							<text>没有任何人</text>
						</label>
						<label class="relation">
							<radio value="其他" />
							<text>其他</text>
						</label>
					</radio-group>
				</view>
			</view>
		</view>

		<!-- 表单2 -->
		<view class="index_2">
			<image src="../../static/title2.png" class="title2"></image>
			<view>
				<view class="index_1_text_1">
					<view>
						<text>姓</text>
						<text>名:</text>
					</view>
					<view><input type="text" placeholder="请输入" v-model="form2.name" /></view>
				</view>

				<view class="index_1_text_2">
					<view class="relation_1">与评估对象关系：</view>
					<radio-group @change="radioChange($event, 8)" class="radios">
						<label class="relation">
							<radio value="配偶" />
							<text>配偶</text>
						</label>
						<label class="relation">
							<radio value="子女" />
							<text>子女</text>
						</label>
						<label class="relation">
							<radio value="其他亲属" />
							<text>其他亲属</text>
						</label>
						<label class="relation">
							<radio value="雇佣照护者" />
							<text>雇佣照护者</text>
						</label>
						<label class="relation">
							<radio value="本人" />
							<text>本人</text>
						</label>
						<label class="relation">
							<radio value="其他" />
							<text>其他</text>
						</label>
					</radio-group>
				</view>

				<view class="index_1_text_3">
					<view>联系电话:</view>
					<view><input type="text" placeholder="请输入" v-model="form2.phone"
							@blur="regExp($event,1,form2.phone,2)" />
					</view>
				</view>
				<view class="index_1_text_3">
					<view>身份证号码:</view>
					<view><input type="text" placeholder="请输入" v-model="form2.ID" @blur="regExp($event,2,form2.ID,2)" />
					</view>
				</view>
				<view class="index_1_text_3">
					<view>联系地址:</view>
					<view><input type="text" placeholder="请输入" v-model="form2.site" /></view>
				</view>
			</view>
			<image src="../../static/nextBtn.png" class="nextBtn" mode="widthFix" @click="submit"></image>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			// const currentDate = this.getDate({
			// 	format: true
			// })
			return {
				date: '请选择',
				form1: {
					name: 'yaoyuan', //姓名
					ID: '410782200111080011', //身份证
					sex: '男', //性别
					age: '19', //年龄
					nation: '汉', //民族
					canbaodi: '辉县市', //参保地
					shinengTime: '', //失能时间
					isTreat: '否', //是否经过康复治疗
					isApply: '是', // 是否首次申请
					phone: '17634298437', // 联系电话
					safeWay: '', //保障方式
					education: '', // 文化程度
					liveStatus: '', // 居住情况
					livePlace: '河南', // 居住地
					caregivers: '' //照护者
				},
				treatMonth: "", //治疗月数，非必填，isTreat为是时需要填
				form2: {
					name: '', //姓名
					phone: '17634298437', //练习电话
					ID: '410782200111080011', // 身份证
					site: '河南省辉县市', //联系地址
					relation: '' //关系
				}
			}
		},
		computed: {
			// 日期级联选择器相关计算属性
			startDate() {
				return this.getDate('start');
			},
			endDate() {
				return this.getDate('end');
			}
		},
		methods: {
			// 日期级联选择器相关方法
			bindDateChange: function(e) {
				this.date = e.target.value
				this.form1.shinengTime = this.date
				console.log('失能时间', this.form1.shinengTime)
			},
			getDate(type) {
				const date = new Date();
				let year = date.getFullYear();
				let month = date.getMonth() + 1;
				let day = date.getDate();

				if (type === 'start') {
					year = year - 60;
				} else if (type === 'end') {
					year = year + 2;
				}
				month = month > 9 ? month : '0' + month;
				day = day > 9 ? day : '0' + day;
				return `${year}-${month}-${day}`;
			},
			// 表单二相关方法
			// 单选切换
			radioChange(e, key) {
				console.log(e)
				console.log(key)
				console.log(e.detail.value)

				// 表单1
				// 性别
				if (key == 1) {
					this.form1.sex = e.detail.value
				}
				// 是否经过康复治疗
				if (key == 2) {
					this.form1.isTreat = e.detail.value
				}
				// 是否首次申请
				if (key == 3) {
					this.form1.isApply = e.detail.value
				}
				// 保障方式
				if (key == 4) {
					this.form1.safeWay = e.detail.value
				}

				// 文化程度
				if (key == 5) {
					this.form1.education = e.detail.value
				}

				// 居住情况
				if (key == 6) {
					this.form1.liveStatus = e.detail.value
				}

				// 照护者
				if (key == 7) {
					this.form1.caregivers = e.detail.value
				}

				// 更改表单2的relation属性
				if (key == 8) {
					this.form2.relation = e.detail.value
				}
			},
			// 手机号和身份证正则验证
			regExp(e, type, value, sequence) {
				console.log(value)
				console.log(e)
				// 手机号正则
				const regExp1 = /^((13[0-9])|(14[0-9])|(15[0-9])|(17[0-9])|(18[0-9]))\d{8}$/
				// 身份证号正则
				const regExp2 = /(^\d{15}$)|(^\d{18}$)|(^\d{17}(\d|X|x)$)/
				if (type == 1) {
					const flag = regExp1.test(value.trim()) // 验证手机号
					if (flag == false) {
						uni.showToast({
							title: "手机号格式错误，请重新输入",
							icon: 'none'
						})
						// 清除输入框
						if (sequence == 1) {
							this.form1.phone = ''
						}
						if (sequence == 2) {
							this.form2.phone = ''
						}
						return
					}
					console.log(flag)
				}
				if (type == 2) {
					console.log(sequence)
					const flag = regExp2.test(value.trim()) // 验证身份证号码
					if (flag == false) {
						uni.showToast({
							title: "身份证号码格式错误，请重新输入",
							icon: 'none'
						})
						// 清除输入框
						if (sequence == 1) {
							this.form1.ID = ''
						}
						if (sequence == 2) {
							this.form2.ID = ''
						}
						return
					}


				}

			},
			// 提交按钮
			submit() {

				console.log(this.form1, this.form2)

				//表单非空验证
				let flag = Object.values(this.form1).every(function(item) {
					return item != ''
				})
				let flag2 = Object.values(this.form2).every(function(item) {
					return item != ''
				})
				console.log(flag, flag2)

				if (flag && flag2) {
					// 判断是否需要填写治疗月数
					if (this.form1.isTreat == '是') {
						if (this.treatMonth == '') {
							uni.showToast({
								title: '请填写治疗月数',
								icon: 'none'
							})
							// 未填写治疗月数，跳出方法
							return
						}
						// 发送ajax提交表单
						this.submitAjax()
						// 治疗月数已填写，正常跳转
						// uni.navigateTo({
						// 	url: '../page2/page2'
						// })
						return
					}
					// 发送ajax提交表单
					this.submitAjax()
					// uni.navigateTo({
					// 	url: '../page2/page2'
					// })
					return
				}
				uni.showToast({
					title: '有未填选项',
					icon: 'none'
				})
			},
			submitAjax() {
				const form1 = JSON.parse(JSON.stringify(this.form1))
				const mouth = this.treatMonth
				form1.mouth = mouth
				const form2 = this.form2
				console.log(form1, form2)
				// 提交两个表单
				uni.request({
					method: "POST",
					url: 'http://v5kwxp.natappfree.cc/ApplicationDate/getLongTermCareRiskAssessment',
					data: {
						form1,
						form2
					},
					success(res) {
						console.log(res)
					}
				})
			}
		}
	}
</script>

<style lang="less">
	.box {
		position: relative;
	}

	image {
		position: absolute;
		width: 750rpx;
		height: 3053rpx;
		z-index: -999;
	}

	.index_1 {
		width: 686rpx;
		height: 2300rpx;
		background: #ffffff;
		border-radius: 10rpx;
		margin-left: 32rpx;
		position: absolute;
		top: 612rpx;
	}

	.index_1 image {
		width: 607rpx;
		height: 173rpx;
		z-index: 999;
		position: absolute;
		top: -57rpx;
		left: 42rpx;
	}

	.index_2 {
		width: 686rpx;
		height: 850rpx;
		background: #ffffff;
		border-radius: 10rpx;
		margin-left: 32rpx;
		position: absolute;
		top: 3100rpx;
	}

	.index_2 .title2 {
		width: 607rpx;
		height: 173rpx;
		z-index: 999;
		position: absolute;
		top: -57rpx;
		left: 42rpx;
	}

	.index_2>view {
		width: 629rpx;
		margin: 100rpx auto;
	}

	.index_1_text_1 {
		height: 84rpx;
		display: flex;
		font-size: 28rpx;
		border-bottom: 2rpx solid #f6f6f6;
	}

	.index_1_text_1 view:nth-child(1) {
		width: 118rpx;
		font-weight: 400;
		color: #6b7072;
		line-height: 84rpx;
	}

	.index_1_text_1 view input {
		height: 84rpx;
		line-height: 84rpx;
		margin-left: 40rpx;
	}

	.index_1_text_1 view:nth-child(1) text:nth-child(1) {
		float: left;
	}

	.index_1_text_1 view:nth-child(1) text:nth-child(2) {
		float: right;
	}

	.cc {
		color: #c9c9ce;
	}

	.index_1_text_2 {
		height: 200rpx;
		font-size: 28rpx;
		border-bottom: 2rpx solid #f6f6f6;
	}

	.index_1_text_666 {
		height: 140rpx;
		font-size: 28rpx;
		border-bottom: 2rpx solid #f6f6f6;
	}

	.relation_1 {
		font-weight: 400;
		color: #6b7072;
		margin-top: 25rpx;
	}

	.relation {
		font-weight: 400;
		color: #6b7072;
		margin-left: 5rpx;
	}

	.radios {
		margin-top: 25rpx;
		display: flex;
		flex-wrap: wrap;
		height: 125rpx;
	}

	.relation text {
		margin-left: 10rpx;
	}

	.index_1_text_3 {
		height: 84rpx;
		display: flex;
		font-size: 28rpx;
		border-bottom: 2rpx solid #f6f6f6;
	}

	.index_1_text_3 view:nth-child(1) {
		font-weight: 400;
		color: #6b7072;
		line-height: 84rpx;
	}

	.index_1_text_3 view input {
		height: 84rpx;
		line-height: 84rpx;
		margin-left: 40rpx;
	}

	// 表单1

	.form111 {
		width: 629rpx;
		margin: 100rpx auto;
	}

	//下一步按钮
	.nextBtn {
		position: absolute;
		bottom: 54rpx;
		left: 50%;
		transform: translateX(-50%);
		z-index: 99;
		width: 300rpx;
		height: 80rpx;
	}

	// 失能时间级联选择框样式
	.shinengTime {
		display: flex;

		.title {
			height: 84rpx;
			font-size: 28rpx;
			border-bottom: 2rpx solid #f6f6f6;
			font-weight: 400;
			color: #6b7072;
			line-height: 84rpx;
		}

		.select {
			margin-left: 20rpx;
			height: 84rpx;
			font-size: 32rpx;
			border-bottom: 2rpx solid #f6f6f6;
			font-weight: 400;
			color: #6b7072;
			line-height: 84rpx;
		}
	}
</style>
