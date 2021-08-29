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
            <!-- 自评失能等级单选 -->
            <view class="myRadio">
                <view class="title">自评失能等级</view>
                <radio-group @change="myRadio" class="radios">
                    <label class="relation">
                        <radio value="A" />
                        <text>A</text>
                    </label>
                    <label class="relation">
                        <radio value="B" />
                        <text>B</text>
                    </label>
                    <label class="relation">
                        <radio value="C" />
                        <text>C</text>
                    </label>
                    <label class="relation">
                        <radio value="D" />
                        <text>D</text>
                    </label>
                    <label class="relation">
                        <radio value="E" />
                        <text>E</text>
                    </label>
                    <label class="relation">
                        <radio value="F" />
                        <text>F</text>
                    </label>
                    <label class="relation">
                        <radio value="G" />
                        <text>G</text>
                    </label>
                </radio-group>
            </view>
            <image src="../../static/submit.png" mode="widthFix" class="submit" @click="submit()"></image>
        </view>
    </view>
</template>

<script>
export default {
    data() {
        return {
            form: {
                topic1: '独立，无需帮助',
                topic2: '独立，无需帮助，能独立拿取衣服，穿上并扣好',
                topic3: '独立，自己能够完全控制',
                topic4: '独立，无需帮助，能独立用厕、便后拭净及整理衣裤，可用手杖、助步器或轮椅，能处理便盆，尿壶',
                topic5: '独立，无需帮助，自己能进出浴室，淋浴、浴盆，独立洗澡',
                topic6: '独立，无需帮助，能自己下场，坐上及离开椅，凳，可用手杖、助步器',
                grade: ''
            },
            topic1: [
                {
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
            topic2: [
                {
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
            topic3: [
                {
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
            topic4: [
                {
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
            topic5: [
                {
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
            topic6: [
                {
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
            if (type == 1) {
                console.log(type, index)
                this.topic1.forEach(item => {
                    item.isActive = false
                }) // 先把所有的单选状态变为false
                this.topic1[index].isActive = true // 勾选状态变为true
                this.form.topic1 = this.topic1[index].text //赋值到data
                console.log(this.topic1)
            }
            if (type == 2) {
                console.log(type, index)
                this.topic2.forEach(item => {
                    item.isActive = false
                })
                this.topic2[index].isActive = true
                this.form.topic2 = this.topic2[index].text //赋值到data
                console.log(this.topic1)
            }
            if (type == 3) {
                console.log(type, index)
                this.topic3.forEach(item => {
                    item.isActive = false
                })
                this.topic3[index].isActive = true
                this.form.topic3 = this.topic3[index].text //赋值到data
                console.log(this.topic1)
            }
            if (type == 4) {
                console.log(type, index)
                this.topic4.forEach(item => {
                    item.isActive = false
                })
                this.topic4[index].isActive = true
                this.form.topic4 = this.topic4[index].text //赋值到data
                console.log(this.topic1)
            }
            if (type == 5) {
                console.log(type, index)
                this.topic5.forEach(item => {
                    item.isActive = false
                })
                this.topic5[index].isActive = true
                this.form.topic5 = this.topic5[index].text //赋值到data
                console.log(this.topic1)
            }
            if (type == 6) {
                console.log(type, index)
                this.topic6.forEach(item => {
                    item.isActive = false
                })
                this.topic6[index].isActive = true
                this.form.topic6 = this.topic6[index].text //赋值到data
                console.log(this.topic1)
            }
        },
        // 自评单选
        myRadio(e) {
            this.form.grade = e.detail.value
            console.log(this.form.grade)
        },
        // 提交表单
        submit() {
            //表单非空验证
            let flag = Object.values(this.form).every(function(item) {
                return item != ''
            })
            if (flag == false) {
                uni.showToast({
                    title: '有未填选项',
                    icon: 'none'
                })
                return
            }
            uni.showToast({
                title: '提交成功',
                icon: 'success'
            })
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
        bottom: -50rpx;
        left: 50%;
        transform: translateX(-50%);
        width: 300rpx;
        height: 80rpx;
    }
}
</style>
