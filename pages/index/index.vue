<template>
	<view>
		<view class="yt-list">
			<view class="yt-list-cell b-b">
				<view class="cell-tit clamp"><text class="red_color">*</text>省市区</view>
				<text class="cell-tip" @click="toggleMaskLocation()">
					<text class="choose-text">{{addressByPcrs}}</text>
					<text class="iconfont icon-xiangxia"></text>
				</text>
			</view>
		</view>
		<gk-city
			:provincedata="provincedata"
			mode="cityPicker"
            ref="cityPicker"
            @funcvalue="getpickerParentValue"
            :pickerSize="4"></gk-city>
	</view>
</template>

<script>
	import provinceData from '@/common/city.data.js';
	export default {
		data() {
			return {
				provincedata:[{
					text:'请选择',
					value:'',
					selfData:provinceData,
				}],
				addressByPcrs:"请选择所在地"
			}
		},
		methods: {
			toggleMaskLocation(){
				this.$refs["cityPicker"].show();
			},
			getpickerParentValue(data){
				this.provincedata=data;
				this.addressByPcrs=data[0].text+" "+data[1].text+" "+data[2].text+" "+data[3].text; 
			},
		}
	}
</script>

<style lang="scss">
/* 头条小程序组件内不能引入字体 */
.yt-list {
		background: #fff;
	}
	.yt-list-cell-warnning{
		display: flex;
		padding: 10rpx 30rpx 10rpx 40rpx;
		color: red;
	}
	.yt-list-cell {
		display: flex;
		align-items: center;
		padding: 6px 12px 6px 17px;
		line-height: 70rpx;
		position: relative;
		&.cell-hover {
			background: #fafafa;
		}

		&.b-b:after {
			left: 30rpx;
			right: 30rpx;
			
		}
		.gray{
			flex: 1;
			font-size: 28rpx;
			margin-right: 10rpx;
			height: 25px;
			line-height: 20px;
			color: gray;
		}
		.cell-icon {
			height: 32rpx;
			width: 32rpx;
			font-size: 28rpx;
			color: #fff;
			text-align: center;
			line-height: 32rpx;
			background: #f85e52;
			border-radius: 4rpx;
			margin-right: 12rpx;

			&.hb {
				background: #ffaa0e;
			}

			&.lpk {
				background: #3ab54a;
			}

		}

		.cell-more {
			align-self: center;
			font-size: 28rpx;
			color: $uni-text-color;
			margin-left: 8rpx;
			margin-right: -10rpx;
		}

		.cell-tit {
			flex: 1;
			font-size: 14px;
			color: $uni-text-color;
			margin-right: 10rpx;
		}
		.money{
			
			color: $uni-text-color-danger;
			font-weight: bold;
			margin-left: 10px;
		}
		.picker-class{
			display: inline-block;
		}
		.cell-tip {
			font-size: 14px;
			color: $uni-text-color;
			flex-direction: column;
			&.disabled {
				color: $uni-text-color;
			}

			&.active {
				color: $base-color;
			}
			&.red{
				color: $uni-text-color-danger;
			}
		}

		&.desc-cell {
			.cell-tit {
				max-width: 90rpx;
			}
		}

		.desc {
			flex: 1;
			font-size: 14px;
			color: $uni-text-color;
		}
	}
	.b-b:after, .b-t:after {
	    position: absolute;
	    z-index: 3;
		bottom: 0;
	    left: 0;
	    right: 0;
	    height: 0;
	    content: '';
	    -webkit-transform: scaleY(0.5);
	    -ms-transform: scaleY(0.5);
	    transform: scaleY(0.5);
	    border-bottom: 1px solid #E4E7ED;
	}
	.red_color{
		color: red;
		display: inline-flex;
		padding-right: 6px;
	}
</style>