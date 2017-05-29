<template>
	<div class="container">
		<h1>Slider</h1>
		
		<section data-title="" id="demo2">
			<div>
				<vue-slider  @callback="cb" ref="slider2" v-bind="demo.demo2" v-model="demo.demo2.value"></vue-slider>
				<h3><small>Value: </small>{{ demo.demo2.value }}</h3>
				<div class="btn-group">
				
				  <img-slider style="text-align:center;">
				  <div class="option-image" id="thumbs">
				  <div id="20" style="display:display;" ><img src="./img/20.jpg" /></div>
				  <div id="24"  style="display:none;"><img  src="./img/24.jpg" /></div>
				  <div id="24"  style="display:none;"><img  src="./img/28.jpg" /></div>
				  <div id="24"  style="display:none;"><img  src="./img/35.jpg" /></div>
				  <div id="24"  style="display:none;"><img  src="./img/50.jpg" /></div>
				  <div id="24"  style="display:none;"><img  src="./img/70.jpg" /></div>
				  
					</div>
					
				  </img-slider>
				  </br>
					<button @click="setValue('demo2', '20mm')">Value = 20mm</button>
					<button @click="setValue('demo2', '24mm')">Value = 24mm</button>
					<button @click="setValue('demo2', '28mm')">Value = 28mm</button>
					<button @click="setValue('demo2', '35mm')">Value = 35mm</button>
					<button @click="setValue('demo2', '50mm')">Value = 50mm</button>
					<button @click="setValue('demo2', '70mm')">Value = 70mm</button>
					
				  </div>
			</div>
			
		</section>
		
		
	</div>
</template>

<script>
import vueSlider from './vue-slider/';

export default {
	components: {
		vueSlider
	},
	data () {
		return {
			demo: {
				default: {
					value: 0,
					width: 'auto',
					height: 6,
					direction: 'horizontal',
					dotSize: 16,
					eventType: 'auto',
					min: 0,
					max: 100,
					interval: 1,
					disabled: false,
					show: true,
					realTime: false,
					tooltip: 'always',
					clickable: true,
					tooltipDir: 'top',
					piecewise: false,
					lazy: false,
					reverse: false,
					speed: 0.5,
					formatter: null,
					bgStyle: null,
					sliderStyle: null,
					tooltipStyle: null,
					processStyle: null,
					piecewiseStyle: null,
					
					
					
				},
				
				demo2: {
				
					value: '',
					width: '80%',
					tooltip: 'always',
					disabled: false,
					piecewise: true,
					piecewiseLabel: true,
					style: {
						marginLeft: '10%'
					},
					data: [
					
                      "20mm",
					  "24mm",
					  "28mm",
					  "35mm",
					  "50mm",
					  "70mm",
					     	],
					piecewiseStyle: {
						backgroundColor: '#ccc',
						visibility: 'visible',
						width: '12px',
						height: '12px'
					},
					piecewiseActiveStyle: {
						backgroundColor: '#3498db'
					},
					labelActiveStyle: {
						color: '#3498db'
					}
				},	
			
				annotation: {
					width: '组件宽度',
					height: '组件高度',
					direction: '组件方向',
					eventType: '事件类型',
					dotSize: '滑块大小',
					min: '最小值',
					max: '最大值',
					interval: '分段间隔',
					disabled: '是否不可用',
					clickable: '是否可点击的',
					show: '是否显示组件',
					realTime: '是否实时计算组件布局',
					speed: '动画速度',
					tooltip: '是否显示工具提示',
					lazy: '是否在拖拽结束后同步值',
					tooltipDir: '工具提示方向',
					tooltipStyle: '工具提示样式',
					piecewise: '是否显示分段样式',
					reverse: '是否反向组件',
					formatter: '格式化tooltip的值',
					processStyle: '进度条样式',
					sliderStyle: '滑块样式',
					bgStyle: '组件背景样式',
					piecewiseStyle: '分割点的样式',
					value: '值'
				}
			}
		}
	},
	methods: {
		format(value) {
			return value === null ? 'null' : (typeof value === 'string' ? `"${value}"` : value)
		},
		formatting(value) {
			this.demo.demo5.processStyle.backgroundColor = `rgba(71, 113, 255, ${value/100})`
			return value
		},
		setDisabled(name) {
			let obj = this.demo[name]
			obj.disabled = !obj.disabled
		},
		setTooltip(name) {
			let obj = this.demo[name]
			obj.tooltip = obj.tooltip === 'hover' ? 'always' : 'hover'
		},
		setValue(name, num) {
			let obj = this.demo[name]
			obj.value = num
		},
		setIndex(name, num) {
			let slider = this.$refs[name]
			slider.setIndex(num)
		},
		getValue(name) {
			let slider = this.$refs[name]
			alert(slider.getValue())
		},
		getIndex(name) {
			let slider = this.$refs[name]
			alert(slider.getIndex())
		},
		dragStart() {
			this.demo.demo5.speed = 0
		},
		dragEnd() {
			this.demo.demo5.speed = 0.5
		},
		cb(val) {
			// console.log(val)
		}
	}
}



</script>


<style scope>
.container {
	width: 100%;
	overflow: hidden;
	background-color: #f4f4f4;
}

.container h1 {
	font-size: 50px;
	text-align: center;
	padding-top: 200px;
	color: #2980b9;
}

.container code {
    padding: 10px 20px;
    margin: 0;
    display: block;
    background-color: #333;
    color: #fff;
    overflow-x: auto;
    font-family: Consolas, Monaco, Droid, Sans, Mono, Source, Code, Pro, Menlo, Lucida, Sans, Type, Writer, Ubuntu, Mono;
    border-radius: 5px;
    white-space: pre-line;
}

section {
	padding: 70px 20px 20px 20px;
	margin: 50px auto;
	box-shadow: 2px 2px 5px 2px rgba(0, 0, 0, .36);
	max-width: 800px;
	background-color: #fff;
	position: relative;
}


section::after {
	content: attr(data-title);
	position: absolute;
	left: 10px;
	top: 10px;
	font-size: 18px;
	font-weight: bold;
	color: #f05b72;
}


.btn-group {
	margin: 10px 0;
}

.btn-group button, .upload-group label {
    padding: 8px 12px;
    display: inline-block;
    border: none;
    background-color: #ccc;
    border-radius: 3px;
    margin: 5px 10px 5px 0;
}

.red {
	color: #d93a49;
}

.green {
	color: #2ecc71;
}

.yellow {
	color: #ffd400;
}

.gray {
	color: #D3DCE6;
}

.preWrap {
	white-space: pre-wrap;
}

.ml-sm {
	margin-left: 5px;
}

.star-slider .vue-slider .vue-slider-dot {
	background: url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABYAAAAWCAYAAADEtGw7AAABdElEQVRIS63VXU6DQBQF4HOwJia2yA6sK7CvxkjpTroD6wqkK9AdqCvpjzG+4grEFYilTZqa9hogVGQQhmpfmfv1cO/MQGj+5PmgjeUyYA+BTgl1FskIFgzzFRSPdtjTqdGDJ6YL4joGuenxYj6uwivh77SwEkzGOqmr4WzaNKZG6lJYTZvK1anL4aK0mqljON5Kn41jiNGBAQsiDoQWiE75kCQaYgDSw0Z8UHys5y/RlqRMWx7A06op13x+FcF9gHc1C39fLvhAY+0krfgvPEXPF952eH/GM2h8jrLvtDOeQxV4p7YUoMVwdOHsme/6w5QJ7dDJr1cOiDw2HYgx0ocB2jPFUeGpOQBwUwfG/uqEZ0s/W6PCk+YtaFzWggsupYLErTHAbg5+A8SFsA1gAOLox3PBkN2ZW5HYDDKFMUg7vN/ea8nXJGpX5g/kgXbYL4enpgBQwHxrkiu16SZtU3eG2oqnww5WC1/3oxnfjNFJyw3vC/6grFUpX2dVAAAAAElFTkSuQmCC') no-repeat;
	background-size: contain;
	box-shadow: none;
	border-radius: 0;
}

#pretty-slider .vue-slider-process {
	background-image: -webkit-linear-gradient(left, #f05b72, #3498db);
}
</style>
