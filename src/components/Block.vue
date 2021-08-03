<template>
	<p>{{res}}</p>
	<div id="squar" v-if="showSquar" :style="{ top: x + 'px', left: y + 'px' }" @click="countClicks">
		click here
	</div>	
</template>



<script>
export default{
	props: ['delay'],
	data(){
		return{
			showSquar: false,
			timer: null,
			clickTime: 2000,
			x: '500',
			y: '50',
			res: 0
		}
	},
	mounted(){
		setTimeout(() => {
			this.showSquar = true
			this.startTimer()
		}, this.delay)
	},
	methods: {
		startTimer(){
			this.timer = setTimeout(() => {
				this.showSquar = false
			}, this.clickTime)
		},
		countClicks(){
			this.res += 1
			this.showSquar = false

			console.log(this.res)
			this.showAgain()
		},
		showAgain(){
			let num = Math.floor(Math.log10(this.res)) + 1
			if(this.res>25){
				num += 1
			}
			if (this.res>50) {
				num += 1
			}
			setTimeout(() =>{
				this.clickTime = 2000/num
				this.x = (170+Math.random()*400).toString()
				this.y = (50+Math.random()*750).toString()
				this.showSquar = true
				this.startTimer()
			}, 2000)
		}
	}
}	
</script>



<style>
	#squar{
    width: 100px;
    height: 100px;
    border-radius: 5px;
    background: rgb(0,70,40,0.8);
    color: white;
    text-align: center;
    vertical-align: middle;
    line-height: 100px; 
    position: absolute; 
    
  	}
</style>