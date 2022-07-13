<template>
  <div class="detail">
	<div>
		<div class="back" :class="{'backShow':backShow}">
			<image @click="btnPath('./homePage')" src="../static/icon/FeatherIconSet/Feather_Arrow/arrow-left.png"></image>
		</div>
	</div>
	<div class="header">
		<swiper class="swiper" @change="changeCurrent" :autoplay="autoplay" :interval="interval" :duration="duration">
			<swiper-item>
				<view class="swiper-item">
					<image mode="widthFix" src="../static/images/FullSizePicture.png"></image>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item">
					<image mode="widthFix" src="../static/images/FullSizePicture.png"></image>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item">
					<image mode="widthFix" src="../static/images/FullSizePicture.png"></image>
				</view>
			</swiper-item>
		</swiper>
		<div class="indicator">
			<div class="items">
				<div class="item" :class="current==0?'itemActive':''"></div>
				<div class="item" :class="current==1?'itemActive':''"></div>
				<div class="item" :class="current==2?'itemActive':''"></div>
			</div>
		</div>
	</div>
	<div class="productDetails" :style="{'margin-top':marginTop+'px'}">
		<!--  style="{'margintop':}" -->
		<div class="detailclothes">
		<div class="name">
			<span>Cotton-blend Hoodie</span>
			<image :src="like?'../static/icon/导航_收藏_已收藏.png':'../static/icon/爱心.png'" @click="like=!like"></image>
		</div>
		<image src="../static/images/RateNumber_w_Star.png"></image>
		<div class="size detailItem">
			<span>Size</span>
			<!-- <picker @change="changeSize" range-key="name" :value="sizeIndex" :range="size" @click="changingSize=true">
				<div class="picker">
					<input type="text" v-model="size[sizeIndex].name" placeholder="Detail" placeholder-style="color:rgb(196, 52, 52);">
					<image src="../static/icon/FeatherIconSet/Feather_Chevron/chevron-down.png"></image>
				</div>
			</picker> -->
			<div class="picker" @click="changingSize=true">
				<input type="text" v-model="finaSize" placeholder="Detail" placeholder-style="color:rgb(196, 52, 52);">
				<image src="../static/icon/FeatherIconSet/Feather_Chevron/chevron-down.png"></image>
			</div>
		</div>
		<div class="color detailItem">
			<span>Color</span>
			<!-- <picker @change="changeColor" range-key="name" :value="colorIndex" :range="color">
				<div class="picker">
					<input type="text" v-model="color[colorIndex].name" placeholder="Detail" placeholder-style="color:rgb(196, 52, 52);">
				</div>
			</picker> -->
			<div class="picker" @click="changingColor=true">
				<input type="text" v-model="finaColor" placeholder="Detail" placeholder-style="color:rgb(196, 52, 52);">
				<image src="../static/icon/FeatherIconSet/Feather_Chevron/chevron-down.png"></image>
			</div>
		</div>
		<div class="pay">
			Estimated Delivery：<span>28 October</span>
		</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
		<div class="1">1</div>
	</div>
	</div>
	<div class="footer">
		<div class="price">
			<span>Total</span><text>\n$39,90</text>
		</div>
		<div class="addBag" @click="duplicateProduct()">
			<span>ADD TO BAG</span>
		</div>
	</div>
	<div class="changingSize changing" v-if="changingSize">
		<div class="content">
			<div class="title">
				<span>Size</span>
			</div>
			<radio-group @change="radioChange">
				<label class="lan" v-for="(item,index) in sizes" :key="item.value">
					<div class="lanItem">{{item}}</div>
					<div class="radio" @click="btnCheckSize(index)">
						<div :class="{'radio-active':index === sizeIndex}"></div>
						<!-- <radio color="blue" :value="item.value" :checked="item=='English'"></radio> -->
					</div>
				</label>
			</radio-group>
			<button @click="changingSize=false">DONE</button>
		</div>
	</div>
	<div class="changingColor changing" v-if="changingColor">
		<div class="content">
			<div class="title">
				<span>Size</span>
			</div>
			<radio-group @change="radioChange">
				<label class="lan" v-for="(item,index) in colors" :key="item.value">
					<div class="lanItem" style="display:flex;align-items:center;">
						<!-- <div class="color" :style="item ? `background-color:${item}` : ''"> -->
						<div class="color" :style="{'background-color':item}">
						</div>
						{{item}}
					</div>
					<div class="radio" @click="btnCheckColor(index)">
						<div :class="{'radio-active':index === colorIndex}"></div>
						<!-- <radio color="blue" :value="item.value" :checked="item=='English'"></radio> -->
					</div>
				</label>
			</radio-group>
			<button @click="changingColor=false">DONE</button>
		</div>
	</div>
	<div class="message" :class="duplicate?'activeMessage':''">
		<div class="messageTips">
			<span>The Product has been added to your favorites list.</span>
		</div>
	</div>
  </div>
</template>

<script>
export default {
    name:'detail',
    data() {
        return {
            indicatorDots: true,  //是否显示面板指示点
            autoplay: true, //是否自动切换
            interval: 2000, //自动切换时间间隔
            duration: 500,   //滑动动画时长
            current:0, //当前所在滑块的index
            sizeIndex:-1,
            sizes:['X Small','Small','Medium','Large','XLarge','XX Large','Oversize'],
            colorIndex:-1,
            color:[
                {id:1,name:'Black'},
                {id:2,name:'Yellow'},
                {id:3,name:'Red'},
                {id:4,name:'Grey'},
                {id:5,name:'White'},
                {id:6,name:'Blue'},
            ],
            colors:['Black','Pink','Red','Grey'],
            changingSize:false,
            changingColor:false,
            finaSize:'',
            finaColor:'',
            // 
            like:false,
            duplicate:false,
			backShow:false, //返回条是否高亮
			productHeight:0,
			productTop:0,
			payBottom:0,
			footerHeight:0,
			marginTop:0,
			a:0
        }
    },
    methods: {
        changeSize(e){
            console.log(e);
            this.sizeIndex = e.detail.value
        },
        btnCheckSize(index) {
            this.sizeIndex = index
            this.finaSize=this.sizes[index]
        },
        btnCheckColor(index) {
            this.colorIndex = index
            this.finaColor=this.colors[index]
        },
        duplicateProduct(){
            this.duplicate=true
            setTimeout(() => {
                this.duplicate=false
            }, 1500);
        },
        changeCurrent(e){
            this.current=e.detail.current
        },
        btnPath(a){
            wx.redirectTo({url:a})
        },
	},
	//监控屏幕滚动距离
	onPageScroll(e){
		var scrollTop = e.scrollTop
		console.log("滚动距离" + scrollTop);
		if(scrollTop>260){
			this.backShow=true
		}else{
			this.backShow=false
		}
	},
	onShow(){
		setTimeout(() => {
			var that=this;
			const query=wx.createSelectorQuery()
			console.log('1',query);
			//获取product顶部
			query.select('.productDetails').boundingClientRect(function(res){
				console.log('product',res);
			}).exec(function(rect){
				that.productTop = rect[0].top+0
				console.log('product顶部值为',that.productTop);
			})
		}, 100);
		setTimeout(() => {
			var that=this;
			const query=wx.createSelectorQuery()
			// 获取pay底部
			query.select('.pay').boundingClientRect(function(res){
				console.log('pay',res);
			}).exec(function(rect){
				that.payBottom = rect[0].bottom+0
				console.log('pay底部值为',that.payBottom);
				that.productHeight=that.payBottom-that.productTop+10
				console.log('productHeight的值为',that.productHeight);
			})
		}, 100);
		
		setTimeout(() => {
			var that=this;
			const query=wx.createSelectorQuery()
			// 获取footer高度
			query.select('.footer').boundingClientRect(function(res){
				console.log('footer',res);
			}).exec(function(rect){
				that.footerHeight = rect[0].height+0
				console.log('footer高度值为',that.footerHeight);
			})
		}, 100);

		setTimeout(() => {
			this.a=wx.getSystemInfoSync().windowHeight
			console.log('屏高为',this.a);
			this.marginTop=wx.getSystemInfoSync().windowHeight-this.footerHeight-this.productHeight
			console.log('marginTop的值为',this.marginTop);
		}, 400);
	},
	onReady(){
		// this.marginTop=wx.getSystemInfoSync().windowHeight+'px'-this.footerHeight+'px'-this.productHeight+'px'
		// console.log('marginTop的值为',this.marginTop);
	}
}
</script>

<style lang="less">
.detail{
    position: relative;
    display: flex;
	flex-flow: column nowrap;
	// height: 100%;
	// width: 100%;
    height: 100vh;
    width: 100vw;
    .back{
        position: fixed;
        top: 0rpx;
        left: 0rpx;
		padding-left: 50rpx;
		padding-top: 100rpx;
        z-index: 667;
        image{
            height: 80rpx;
            width: 80rpx;
			margin-top: calc();
        }
    }
	.backShow{
		width: 100vw;
		background-color: white;
		z-index: 666;
	}
    .message{
        height: 85rpx;
        width: 100%;
        text-align: center;
        font-size: 25rpx;
        font-weight: 600;
        z-index: 667;
        line-height: 75rpx;
        position: fixed;
        top: -80rpx;
        transition: all .25s;
		display: flex;
		justify-content: center;
		.messageTips{
			width: 650rpx;
			background-color: white;
        	border-radius: 50rpx;
		}
    }
    .activeMessage{
        top: 110rpx;
    }
	.header{
		position: fixed;
		top: 0;
		left: 0;
		.indicator{
			height: 50rpx;
			width: 100%;
			display: flex;
			justify-content: center;
			align-items: center;
			position: absolute;
			bottom: 20rpx;
			z-index: 6;
			.items{
				display: flex;
				justify-content: center;
				align-items: center;
				position: fixed;
				.item{
					height: 20rpx;
					width: 20rpx;
					border-radius: 50%;
					background-color: gray;
					margin: 0 10rpx;
				}
				.itemActive{
					background-color: white;
				}
			}
		}
	}
    .swiper{
        width: 100vw;
        height: 65vh;
        position: relative;
		z-index: 1;
        .swiper-item{
            height: 100%;
            text-align: center;
        }
        .swiper-item image{
            display: inline-block;
            overflow: hidden;
            width: 100%;
            height: 100%;
        }
    }
    .productDetails{
        box-sizing: border-box;
        width: 100vw;
        // height: 550rpx;
        background-color: white;
        // position: absolute;
        // bottom: 0;
        border-top-left-radius: 50rpx;
        border-top-right-radius: 50rpx;
		z-index: 2;
		margin-top: 770rpx;
        .detailclothes{
            padding: 40rpx 50rpx 40rpx;
            .name{
                width: 100%;
                height: 70rpx;
                font-size: 33rpx;
                font-weight: 600;
                letter-spacing: 3rpx;
                image{
                    float: right;
                    width: 55rpx;
                    height: 55rpx;
                }
            }
            image{
                width: 250rpx;
                height: 40rpx;
            }
            .detailItem{
                height: 80rpx;
                width: 100%;
                display: flex;
                justify-content: flex-start;
                align-items: center;
                flex-flow: row nowrap;
                .picker{
                    // width: 100rpx;
                    height: 100%;
                    display: flex;
                    align-items: center;
                }
                span{
                    font-weight: 600;
                    font-size: 35rpx;
                    flex-grow: 1;
                    // width: 700rpx;
                }
                input{
                    font-size: 30rpx;
                    text-align: right;
                    padding-right: 10rpx;
                }
                image{
                    width: 60rpx;
                    height: 60rpx;
                }
            }
            .pay{
                text-align: center;
                font-size: 28rpx;
                font-weight: 600;
                letter-spacing: 2rpx;
                span{
                    color: gray;
                    font-weight: 500;
                }
            }
        }
    }
	.footer{
		padding: 10rpx 50rpx;
		height: 200rpx;
		width: 100%;
		background-color: rgba(36, 210, 253, 0.897);
		border-top-left-radius: 50rpx;
		border-top-right-radius: 50rpx;
		display: flex;
		justify-content: flex-start;
		align-items: center;
		padding-bottom: 50rpx;
		position: fixed;
		bottom: 0;
		left: 0;
		box-sizing: border-box;
		z-index: 3;
		.price{
			display: flex;
			flex-flow: column;
			align-items: flex-start;
			height: 100rpx;
			line-height: 25rpx;
			flex-grow: 1;
			vertical-align: sub;
			text{
				color: white;
				font-size: 55rpx;
			}
			span{
				font-size: 28rpx;
				color: rgba(245, 245, 245, 0.555);
				font-weight: 600;
			}
		}
		.addBag{
			text-align: center;
			height: 75rpx;
			width: 270rpx;
			border: 1rpx solid greenyellow;
			border-radius: 20rpx;
			line-height: 75rpx;
			span{
				color: white;
				font-size: 32rpx;   
			}
		}
	}
}

.changing{
    // height: 850rpx;
    width: 100vw;
    background-color: white;
    position: absolute;
    bottom: 0;
    border-top-left-radius: 50rpx;
    border-top-right-radius: 50rpx;
    z-index: 666;
    .content{
        margin: 50rpx;
        .title{
            font-size: 40rpx;
            font-weight: 600;
            letter-spacing: 3rpx;
            margin: 50rpx 0;
        }
        .lan{
            display: flex;
            justify-content: flex-start;
            align-items: center;
            flex-flow: row nowrap;
            margin: 20rpx 0;
            font-size: 33rpx;
            font-weight: 400;
            letter-spacing: 2rpx;
            position: relative;
            .lanItem{
                flex-grow: 1;
                .color{
                    width:40rpx;
                    height:40rpx;
                    border-radius: 30%;
                    margin-right: 20rpx;
                }
            }
            .radio{
                width: 50rpx;
                height: 50rpx;
                // padding: 4rpx;
                position: relative;
                border: 4rpx solid #2b90af;
                border-radius: 50%;
                box-sizing: border-box;
            }
            .radio-active{
                width: 80%;
                height: 80%;
                background: #6bd3f3;
                border-radius: 50%;
                position: absolute;
                top: 50%;
                left: 50%;
                transform: translate(-50%,-50%);
            }   
        }
        button{
            background-color: rgb(20, 196, 228);
            border-radius: 50rpx;
            margin-top: 100rpx;
            color: white;
            font-size: 35rpx;
            font-weight: 500;
            height: 100rpx;
            vertical-align: center;
            text-align: center;
            line-height: 100rpx;
        }
    }
}
 
</style>