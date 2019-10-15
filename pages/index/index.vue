<template>
	<view>
		<view class="tuijian">Today</view>
	<view class="content" v-for="item in items">
		
		<view class="box" @tap="play" :data-id="item.id">
			<image class="img" :src="item.cover">
			<view class="title-back"><view class="title">{{item.title}}</view></view>
			</image>
			
		</view>
		
	</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				items:[]
				
			}
		},
		
		onLoad() {
			uni.showLoading({
				title: '努力加载中。。',
				mask: false
			});
			var me=this;
			uni.request({
				url: 'http://bapi.xinli001.com/fm2/broadcast_list.json/?offset=0&rows=20',
				method: 'GET',
				data: {},
				success: res => {
					
					me.items=res.data.data
					console.log(me.items)
					uni.hideLoading();
				},
				fail: () => {},
				complete: () => {}
			});
			
		},
		methods: {
			play(e){
				console.log(e);
				var id=e.currentTarget.dataset.id;
				
				uni.navigateTo({
					url: '../play/play?id='+id,
					
					
				});
				
				
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction:column;
		align-items: center;
		}
	.tuijian{
		position: relative;
		top:30px;
		left: 30px;
		padding-bottom: 10px;
		
		font-size: 30px;
		font-weight: 2000;
	}
	
	.box{
		
		background-color: #ffffff;
		width: 650upx;
		height:fix;
		
		border-radius: 10px;
		margin-top: 40px;
		padding: 0px 0px 0px 0px;
		overflow: hidden;
		}
	.img{
			width: 650upx;
			height: fix;
			
		}
	.title-back{
		position: relative;
		
		
		width: 100%;
		height: 60px;
		  background: linear-gradient( to right,rgb(70, 120, 190), rgb(212, 203, 203), rgb(192, 172, 172), rgb(168, 192, 168), rgb(182, 182, 207), rgb(173, 157, 184), rgb(190, 156, 190));
		opacity: 0.6;
		top: -5px;
		border-radius:0px 0px 10px 10px;
	}
	.title{
		text-align: center;
		font-size: 18px;
		line-height: 60px;
		font-weight: bolder;
		opacity: 1;
		
		
	
		}
</style>
