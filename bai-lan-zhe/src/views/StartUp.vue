<template>
	<div class="start-up">
		<div class="b-image" :class="isFocus ? 'filter' : ''">
			<div class="mask">
				
				
			</div>
		</div>
		<div class="content-container">
			<div class="content">
				<div class="cuurent-time">
					<span>{{h}}</span>
					<span>:</span>
					<span>{{m}}</span>
					<span>:</span>
					<span>{{s}}</span>
				</div>
				<div class="search-input" :class="isFocus ? 'b-white' : ''">
					<input @focus="searchFocus" @input="searchContentChange" @blur="searchBlur" v-model="searchContent" type="text" :placeholder="isFocus ? '' : 'search'">
				</div>
				<div class="op-icon">
					<span @click="to('/User')" class="iconfont icon-yonghu-yuan"></span>
					<span class="shu">|</span>
					<span class="iconfont icon-jinru"></span>
				</div>
				<div class="search-list">
					<div class="list-item" v-for="(item,index) in searchList" >
						{{item.value}}
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		name:'StartUp',
		data(){
			return {
				h:0,
				m:0,
				s:0,
				isFocus:false,
				searchContent:'',
				timeDelay:null,
				searchList:[
					
				]
			}
		},
		created() {
			this.updateTime()
			setInterval(() => {
				this.updateTime()
			},1000)
		},
		methods:{
			searchFocus(){
				this.isFocus = true
			},
			searchContentChange(){
				clearTimeout(this.timeDelay)
				if(this.searchContent.trim() == ''){
					this.searchList = []
					return
				}			
				
				this.timeDelay = setTimeout(() => {
					this.searchList = [
						{
							id:1001,
							value:'Java跨平台解决方案',
						},
						{
							id:1002,
							value:'JavaScript实现雨水效果'
						},
						{
							id:1003,
							value:'Vue创建流程'
						}
					]
				},1000)
			},
			searchBlur(){
				clearTimeout(this.timeDelay)
				this.isFocus = false
				this.searchContent = ''
				this.searchList = []
			},
			updateTime(){
				let date = new Date();
				this.h = date.getHours();
				this.m = date.getMinutes();
				let s = date.getSeconds();
				this.s = s

				
			},
			to(path){
				
				
				const routeData = this.$router.resolve({
						path: path,
					});
				window.open(routeData.href, '_blank');
			}
		}
	}
</script>

<style lang="less" scoped="scoped">
	.start-up{
		width: 100%;
		height: 100%;
		overflow: hidden;
	}
	.b-image {
		width: 100%;
		height: 100%;
		
		position: relative;
		background-size: cover;
		background-position: center;
		background-image: url(../assets/start/-365873383.jpg);
		transition: 0.3s;
		.mask{
			width: 100%;
			height: 100%;
			position: absolute;left: 0;top: 0;
			opacity: 0.45;
			background-image: linear-gradient(#000000bf, #66ccff8c);
		}
	}
	.filter{
		filter: blur(5px);
		transform: scale(1.3);
	}
	
	.content-container{
		width: 100%;
		height: 100%;
		position: absolute;left: 0;top: 0;
		display: flex;
		justify-content: center;
		align-items: center;
		
		.content{
			position: relative;top: -180px;
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			
			> div{
				margin: 25px;
			}
			.cuurent-time{
				font-size: 28px;
				font-weight: bold;
				color: #FFF;
				span{
					margin: 0 8px;
				}
			}
			.search-input{
				width: 600px;
				height: 40px;
				border: 1px solid #aaa;
				border-radius: 40px;
				background: rgba(215,215,215,0.7);
				
				input{
					width: 100%;
					height: 100%;
					text-align: center;
					background: none;
					outline: none;
					border: none;
				}
				
				
			}
			.b-white{
				background: #FFF;
				
			}
			
			.op-icon{
				display: flex;
				align-items: center;
				background: rgba(255,255,255,0.5);
				padding: 5px 15px;
				border-radius: 35px;
				span{
					margin: 0 15px;
				}
				.iconfont{
					font-size: 36px;
					color: #000;
					cursor: pointer;
				}
				.shu{
					font-size: 20px;
					color: #FFF;
				}
				.iconfont:hover{
					color: #FFF;
				}
			}
			
			.search-list{
				width: 560px;
				margin: 0 auto;
				background: rgba(215,215,215,0.7);
				position: absolute;left: 50%;bottom: -50%;
				transform: translateX(-50%);
				border-radius: 5px;
				.list-item{
					margin: 10px 5px;
					padding: 5px;
					cursor: pointer;
				}
				.list-item:hover{
					background: #FFF;
				}
			}
		}
		
		
	}
</style>
