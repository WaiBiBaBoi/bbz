<template>
	<div class="header" :class="isStart ? 'h-start' : 'h-hide'">
		<div class="header-container">
			<div class="left" :class="isStart ? '' : 'l-start'">
				<div class="logo">
					<span class="iconfont icon-bokeyuan"></span>
					<span class="logo-t">青柠</span>
				</div>
				<div class="nav-list">
					<div class="nav-item" :class="isStart ? '' : 'ns-nav-item'" v-for="(item,index) in navlist">
						<span>{{item.value}}</span>
					</div>
				</div>
				<div class="search-input" v-if="!isStart">
					<input type="text" placeholder="search">
				</div>
			</div>
			<div class="right">
				<div class="to-login-btn">
					登录 / 注册
				</div>
			</div>
		</div>
	</div>
	
</template>

<script>
	export default {
		name:'Header',
		data(){
			return {
				navlist:[
					{
						value:'首页'
					},
					{
						value:'文章'
					},
					{
						value:'话题'
					},
					{
						value:'发布'
					}
				],
				isStart:null
			}
		},
		created() {
			
			
		},
		watch:{
			$route(){
				let pathArr = ['/','/StartUp'];
				
				if(pathArr.includes(this.$route.path)){
					this.isStart = true
				}else{
					this.isStart = false
				}
			}
		},
		
	}
</script>

<style lang="less" scoped="scoped">
	.h-start{
		position: fixed;top: 0;left: 50%;
		transform: translateX(-50%);
		
		
	}
	.l-start{
		color: #333;
		
	}
	.h-hide{
		border-bottom: 1px solid #AAA;
		background: #FFF;
	}
	
	.header{
		width: 100%;
		z-index: 10;
	}
	.header-container{
		width: 1600px;
		height: 60px;
		margin: 0 auto;
		color: #FFF;
		padding: 0 15px;
		display: flex;
	}
	
	.left{
		display: flex;
		align-items: center;
		height: 100%;
		width: 80%;
		.logo{
			.icon-bokeyuan{
				font-size: 28px;
			}
			.logo-t{
				font-weight: bold;
				font-size: 20px;
				margin-left: 8px;
				position: relative;top: -1px;
			}
			
		}
		.nav-list{
			display: flex;
			margin-left: 35px;
			position: relative;top: 3px;
			.nav-item{
				line-height: 28px;
				margin: 0 12px;
				cursor: pointer;
				font-size: 14px;
				box-sizing: border-box;
			}
			.nav-item:hover{
				border-bottom: 1px solid #FFF;
				
			}
			.ns-nav-item:hover{
				border-bottom: 1px solid #333;
			}
		}
		.search-input{
			margin-left: 50px;
			width: 350px;
			height: 25px;
			background: rgba(215,215,215,0.3);
			border: 1px solid #CCC;
			border-radius: 20px;
			overflow: hidden;
			input{
				outline: none;
				border: none;
				background: transparent;
				width: 100%;
				height: 100%;
				text-indent: 1em;
				text-align: center;
			}
		}
	}
	
	
	.right{
		height: 100%;
		flex: 1;
		display: flex;
		align-items: center;
		.to-login-btn{
			padding: 4px 12px;
			border-radius: 2px;
			background: rgba(2,171,255,0.8);
			font-size: 14px;
			cursor: pointer;
		}
		.to-login-btn:hover{
			background: rgba(2,171,255,1);
		}
	}
</style>
