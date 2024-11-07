<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
	</view>
	<div>
			<button type="primary" @click="testAsyncFunc">testAsyncFunc</button>
			<button type="primary" @click="testSyncFunc">testSyncFunc</button>
		</div>
</template>

<script>
	
	// export class FileUtils {
	// 	public static chooseImage(num: number, useCamera: boolean): Promise<string[] | string> {
	// 		    return new Promise((resolve, reject) => {
	// 		        console.log("chooseImage");
	// 		        uni.chooseImage({
	// 		            count: num,
	// 		            sizeType: ["compressed"],
	// 		            camera: "front",
	// 		            sourceType: !useCamera ? ["album"] : ["camera"],
	// 		            success(res) {
	// 		                console.log("chooseImage: count:" + res.tempFilePaths.length);
	// 		                resolve(res.tempFilePaths);
	// 		            },
	// 		            fail(res) {
	// 		                reject(new Error("选择图片失败"));
	// 		                console.log("chooseImage:" + res);
	// 		            },
	// 		        });
	// 		    });
	// 		}
	// }
	
	
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {
				testAsyncFunc() {
					// FileUtils.chooseImage(1, false)
					uni.chooseImage({
					    count: 1,
					    sizeType: ["compressed"],
					    camera: "front",
					    sourceType: ["album"],
					    success(res) {
					        console.log("chooseImage: count:" + res.tempFilePaths[0]);
					    },
					    fail(res) {
					        console.log("chooseImage:" + res);
					    },
					});
				},
				testSyncFunc() {
					uni.chooseImage({
					    count: 1,
					    sizeType: ["compressed"],
					    camera: "front",
					    sourceType: ["camera"],
					    success(res) {
					        console.log("chooseImage: count:" + res.tempFilePaths[0]);
					    },
					    fail(res) {
					        console.log("chooseImage:" + res);
					    },
					});
				}
		}
	}
	
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
