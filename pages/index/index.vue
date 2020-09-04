<template>
    <view class="content">
        <view class="row b-b">
            <text class="tit">播放时长/分钟</text>
            <input class="input" type="number" v-model="playData.time" placeholder="请输入播放时长(minutes)" placeholder-class="placeholder" />
        </view>        

        <button class="add-btn" @click="setTime">确定</button>
		<!-- <button class="add-btn" @click="reset">重新设定时间</button> -->
		
		
    </view>
</template>

<script>
    export default {
        data() {
            return {
                playData: {
                    time: ''
                }
            }
        },
        onLoad(option) {},
        methods: {
            //设置时间
            setTime() {
                let data = this.playData.time;
				if (data == null){
					return;
				}
				document.getElementsByClassName("add-btn")[0].setAttribute("disabled","true");
				let ac = uni.createInnerAudioContext();
				ac.src = "https://img-cdn-qiniu.dcloud.net.cn/uniapp/audio/music.mp3";
				ac.loop = true;
				ac.play();
				
				
                
				setTimeout(function(){
					console.log(data);
					ac.pause();
					ac.loop = false;
				},data*1000*60)
            },
			/* reset(){
				document.getElementsByClassName("add-btn")[0].setAttribute("disabled","false");
				ac.pause();
				ac.loop = false;
			}, */
        }
    }
</script>

<style lang="scss">
    page {
        padding-top: 16upx;
    }

    .row {
        display: flex;
        align-items: center;
        position: relative;
        padding: 0 30upx;
        height: 110upx;
        background: #fff;

        .tit {
            flex-shrink: 0;
            width: 120upx;
            font-size: 30upx;

        }

        .input {
            flex: 1;
            font-size: 30upx;

        }

        .icon-shouhuodizhi {
            font-size: 36upx;

        }
    }

    .add-btn {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 690upx;
        height: 80upx;
        margin: 60upx auto;
        background-color: rgb(28, 42, 134);
        color: #fff;

        border-radius: 10upx;
        box-shadow: 1px 2px 5px rgba(28, 42, 134, 0.4);
    }
</style>
