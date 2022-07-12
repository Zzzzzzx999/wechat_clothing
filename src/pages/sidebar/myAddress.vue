<template>
  <div class="myAddress">
      <div class="title">
          <span>My Address</span>
      </div>
      <div class="addressDetail">
          <div class="name" :class="focus.name?'active':''">
              <span>Address Name</span>
              <input type="text" placeholder="Home" placeholder-style="color:black" @focus="focus.name=true" @blur="focus.name=false">
          </div>
          <div class="street" :class="focus.street?'active':''">
              <span>Street</span>
              <input type="text" placeholder="82 Hinkle Lake Road" placeholder-style="color:black" @focus="focus.street=true" @blur="focus.street=false">
          </div>
          <div class="city" :class="focus.city?'active':''">
              <span>City</span>
              <picker range-key="name" @change="changeCity" :value="cityIndex" :range="citys"> 
                <div class="chooseCity picker">
                    <input type="text" v-model="citys[cityIndex].name" placeholder="Boston" placeholder-style="color:black" @focus="focus.city=true" @blur="focus.city=false">
                    <image src="../../static/icon/FeatherIconSet/Feather_Chevron/chevron-down.png"></image>
                </div>
              </picker>
          </div>
          <div class="state" :class="focus.state?'active':''">
              <span>State</span>
              <picker range-key="name" @change="changeState" :value="stateIndex" :range="states"> 
                <div class="chooseState picker">
                    <input type="text" v-model="states[stateIndex].name" placeholder="Select" placeholder-style="color:black" @focus="focus.state=true" @blur="focus.state=false">
                    <image src="../../static/icon/FeatherIconSet/Feather_Chevron/chevron-down.png"></image>
                </div>
              </picker>
          </div>
          <div class="zipCode" :class="focus.zipCode?'active':''">
              <span>Zip Code</span>
              <input type="text" placeholder="02115" placeholder-style="color:black" @focus="focus.zipCode=true" @blur="focus.zipCode=false">
          </div>
      </div>
      <div class="button">
          <button @click="btnPath('../sidebar/myAddressList')">DONE</button>
      </div>
  </div>
</template>

<script>
export default {
    name:"myAddress",
    data() {
        return {
            focus:{
                name:false,
				street:false,
				city:false,
				state:false,
				zipCode:false,
            },
            cityIndex:0,
            citys:[
                {id:1,name:'Boston'},
                {id:2,name:'New York'},
                {id:3,name:'Chicago'},
                {id:4,name:'Washington'},
                {id:5,name:'San Francisco'},
                {id:6,name:'Houston'},
            ],
            stateIndex:-1,
            states:[
                {id:1,name:'Chinese'},
                {id:2,name:'America'},
                {id:3,name:'Russia'},
                {id:4,name:'England'},
                {id:5,name:'Japan'},
                {id:6,name:'France'},
            ]
        }
    },
    methods: {
        changeCity(e) {
            console.log('123',e)
            this.cityIndex = e.detail.value
        },
        changeState(e) {
            console.log('456',e)
            this.stateIndex = e.detail.value
        },
        btnPath(a){
            wx.redirectTo({url:a})
        }
    },
}
</script>

<style lang="less">
    .myAddress{
        margin: 0 50rpx;
        padding: 50rpx 0;
        position: relative;
        height: 100vh;
        box-sizing: border-box;
        .title{
            font-size: 42rpx;
            font-weight: 600;
            margin: 50rpx 0;
        }
        .addressDetail{
            span{
                font-size: 30rpx;
            }
            input{
                display: flex;
                border: 3rpx solid #c6cbcc;   
                border-radius: 50rpx;
                width: 100%;
                height: 85rpx;
                margin: 15rpx 0;
                padding-left: 35rpx;
                box-sizing: border-box;
                font-size: 30rpx;
            }
            .picker{
                display: flex;
                justify-content: flex-start;
                align-items: center;
                flex-flow: row nowrap;
                position: relative;
                flex-grow: 1;
                image{
                    width: 50rpx;
                    height: 50rpx;
                    position: absolute;
                    top: 8rpx;
                    right: 10rpx;
                    transform: translate(-50%,50%);
                }
            }
        }
        .button{
            position: absolute;
            bottom: 200rpx;
            width: 100%;
            button{
                background-color: rgb(20, 196, 228);
                border-radius: 50rpx;
                color: white;
                font-size: 35rpx;
                font-weight: 500;
                height: 100rpx;
                line-height: 100rpx;
            }
        }
    }

    .active input{
		border: 3rpx solid rgb(177, 45, 45)!important;
	}
</style>