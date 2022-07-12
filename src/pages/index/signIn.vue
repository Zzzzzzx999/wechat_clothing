<template>
	<div class="content">
		<image class="bg" mode="scaleToFill" src="../../static/start(2).png"></image>
		<image class="bg2" src="../../static/start(1).png"></image>
		<div class="signIn">
			<span class="title">Sign In</span>
			<div class="login">
				<div class="userInfo" :class="emailFocus?'active':''">
					<span>E-mail</span><br> 
					<input type="text" placeholder="+90 555 555 44 33" @focus="emailFocus=true" @blur="emailFocus=false" maxlength="16" confirm-type="done" placeholder-style="color:black">
				</div>
				<div class="userInfo">
					<span>Password</span><br>
					<div class="password" :class="passwordFocus?'active':''">
						<input type=text :password="!open" placeholder="Password" @focus="passwordFocus=true" @blur="passwordFocus=false" maxlength="16" confirm-type="done" placeholder-style="color:black">
						<!-- <image src="../../static/icon/FeatherIconSet/Feather_Controls/eye-off.png"></image> -->
						<image :src="open?'../../static/icon/FeatherIconSet/Feather_Controls/eye.png':'../../static/icon/FeatherIconSet/Feather_Controls/eye-off.png'" @click="changePasswordType"></image>
					</div>
				</div>
				<div class="forgotPassword">
					<span @click="forgotPwdPath">Forgot your password?</span>
				</div>
				<div class="loginButton">
					<button @click="homePagePath">LOGIN</button>
				</div>
				<div class="loginSocial">
					<span id="bolder">Login with Social</span>
					<div class="socials">
						<div class="social">
							<image src="../../static/icon/Brand_Icon/Google（1）.png"></image>
						</div>
						<div class="social">
							<image src="../../static/icon/Brand_Icon/Facebook.png"></image>
						</div>
						<div class="social">
							<image src="../../static/icon/Brand_Icon/Apple.png"></image>
						</div>
					</div>
					<div class="notAccount">
						<span>Don' t have an account?</span>
						<span id="bolder" @click="signUpPath">Sign Up</span>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		name:'index',
		data() {
			return {
				open:false,
				emailFocus:false,
				passwordFocus:false,
			}
		},
		onLoad() {
			
		},
		methods: {
			changePasswordType(){
				this.open=!this.open
			},
			handleFocus(){
				this.focus=true
				console.log(this.focus,'获取到了焦点');
			},
			handleBlur(){
				this.focus=false
				console.log(this.focus,'失去了焦点');
			},
			signUpPath(){
				uni.navigateTo({url:'./signUp'})
			},
			forgotPwdPath(){
				uni.navigateTo({url:'./forgotPwd'})
			},
			homePagePath(){
				wx.navigateTo({url:'../homePage'}) //wx.navigateTo无法跳转到tabbar页面，故采用wx.switchTab
				// 取消了tabbar使用，仍然使用wx.navigateTo
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		justify-content: center;
		height: 100vh;
		width: 100vw;
		position: relative;
		margin: 0;
		padding: 0;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin: 200rpx auto 50rpx auto;
	}

	.title{
		font-size: 40rpx;
		font-weight: 600;
	}

	.bg{
		width: 800rpx;
		height: 750rpx;
		position: absolute;
		top: 0;
		left: 0;
		background-size:100% 100%;
		filter: brightness(0.65);
		z-index: -2;
	}

	.bg2{
		width: 200rpx;
		height: 200rpx;
		position: absolute;
		top: 10%;
		left: 50%;
		transform: translate(-50%,-20%);
		background-size:100% 100%;
		z-index: -1;
	}

	.signIn{
		width: 100%;
		height: 70vh;
		/* height: 880rpx; */
		position: absolute;
		bottom: 0;
		background-color: whitesmoke;
		border-radius: 5%;
		display: flex;
		justify-content: space-around;
		align-items: center;
		flex-flow: column nowrap;
		padding-bottom: 50rpx;
		box-sizing: border-box;
	}

	.signIn .title{
		margin: 30rpx 0rpx 20rpx;
	}

	.content .signIn .login{
		font-size: 35rpx;
		color: rgb(48, 46, 46);
		font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
	}
/* 
	.content .signIn .login .userInfo{
		padding-top: 20rpx;
	} */

	.content .signIn .login .userInfo input{
		display: flex;
		border: 3rpx solid #c6cbcc;   
  		border-radius: 50rpx;
		width: 630rpx;
		height: 85rpx;
		margin: 15rpx 0;
		padding-left: 35rpx;
		box-sizing: border-box;
		font-size: 30rpx;
	}

	.active input{
		border: 3rpx solid rgb(177, 45, 45)!important;
	}

	.content .signIn .login .userInfo .password{
		display: flex;
		justify-content: center;
		align-items: center;
		position: relative;
	}

	.content .signIn .login .userInfo .password image{
		position: absolute;
		right: 25rpx;
		width: 60rpx;
		height: 60rpx;
	}

	.content .signIn .login .forgotPassword{
		display: block;
		text-align: right;
		color: black;
		font-size: 35rpx;
	}

	.content .signIn .login .forgotPassword span{
		text-align: center;
		font-weight: 600;
	}

	.content .signIn .login .loginButton{
		margin-top: 20rpx;
	}

	.content .signIn .login .loginButton button{
		border-radius: 50rpx;
		color: white;
		background-color: #21bff0;
		font-size: 35rpx;
		border-radius: 50rpx;
		margin: 0;
		font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
		cursor: pointer;
	}
	.content .signIn .login .loginSocial{
		display: flex;
		flex-flow: column nowrap;
		justify-content: center;
		align-items: center;
		margin-top: 20rpx;
	}
	.content .signIn .login .loginSocial span{
		margin: 15rpx 0;
	}
	.content .signIn .login .loginSocial #bolder{
		color: rgb(48, 46, 46);
		font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
		font-weight: 600;
	}
	.content .signIn .login .loginSocial .socials{
		display: flex;
		flex-flow: row nowrap;
		justify-content: space-around;
		align-items: center;
		width: 600rpx;
		margin-top: 20rpx;
	}
	.content .signIn .login .loginSocial .socials .social{
		width: 80rpx;
		height: 80rpx;
		display: flex;
		justify-content: center;
		align-items: center;
		border-radius: 20rpx;
		background-color: white;
		box-shadow:0px 0px 30rpx 5rpx rgb(218, 216, 216);
	}
	.content .signIn .login .loginSocial .notAccount{
		margin: 20rpx 0;
	}
	.content .signIn .login .loginSocial .notAccount span:last-child{
		margin-left: 10rpx;
	}
	.content .signIn .login .loginSocial .socials .social image{
		width: 40rpx;
		height: 40rpx;
	}
</style>
