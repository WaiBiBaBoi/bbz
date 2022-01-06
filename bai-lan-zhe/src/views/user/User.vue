<template>
	<div class="user">
		<div class="user-info">
			<img src="../../assets/user/Avatar.png" >
			<div class="n-d">
				<p class="name">青柠</p>
				<p class="desc">
					这个人很懒，什么都没有留下
				</p>
			</div>
			<div class="user-data">
				<div>
					<span class="iconfont icon-31dianzan" title="获得点赞数"></span>
					<span class="num">999</span>
				</div>
				<div>
					<span class="iconfont icon-icon_fabu" title="发布稿件数"></span>
					<span class="num">666</span>
				</div>
			</div>
			<div class="set">
				<span class="iconfont icon-shezhi" title="设置"></span>
			</div>
		</div>
		<div class="nav-list">
			<div class="nav-item" v-for="(item,index) in navlist">
				<span>{{item.value}}</span>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		name:'User',
		data(){
			return {
				navlist:[
					{
						value:'日志'
					},
					{
						value:'收藏'
					},
					{
						value:'发布'
					}
				]
			}
		}
	}
</script>

<style lang="less" scoped="scoped">
	.user{
		width: 1160px;
		margin: 0 auto;
		
	}
	
	.user-info{
		width: 100%;
		height: 160px;
		margin-top: 66px;  
		padding: 0 12px;
		padding-top: 66px;
		position: relative;
		background-image: url(../../assets/user/Back.png);
		background-size: cover;
		background-position: center top;
		box-sizing: border-box;
		
		img{
			width: 120px;
			border-radius: 50%;
			border: 1px solid #AAA;
			position: absolute;left: 50%;top: -33%;
			transform: translateX(-50%);
			display: block;
		}
		
		.n-d{
			text-align: center;
			.name{
				font-size: 18px;
				font-weight: bold;
				margin: 12px 0;
			}
			.desc{
				width: 100%;
				font-size: 14px;
				line-height: 20px;
				
				
				
			}
			
		}
		
		.user-data{
			position: absolute;left: 8;top: 6px;
			display: flex;
			> div{
				margin-right: 15px;
				.iconfont{
					font-weight: bold;
					font-size: 18px;
					cursor: pointer;
				}
				.num{
					margin-left: 6px;
					font-size: 14px;
				}
			}
		}
		
		.set{
			position: absolute;right: 8px;top: 6px;
			.iconfont{
				font-weight: bold;
				font-size: 18px;
				cursor: pointer;
			}
		}
	}
	
	.nav-list{
		display: flex;
		align-items: center;
		background: #FFF;
		font-size: 14px;
		height: 36px;
		overflow: hidden;
		border-radius: 0 0 3px 3px;
		.nav-item{
			margin: 0 12px;
			cursor: pointer;
		}
		.nav-item:hover{
			color: #66CCFF;
		}
	}
</style>
