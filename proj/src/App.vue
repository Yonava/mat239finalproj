<template>
    <div id="app">

		<center>

			<div v-if="selected === 'paths'">
				<Paths />
			</div>
			<div v-else-if="selected === 'complete'">
				<Complete />
			</div>
			<div v-else-if="selected === 'cycle'">
				<Cycles />
			</div>

		
			<div v-else class="main-container">

				<h1>Choose Your Poison:</h1>

				<button v-on:mouseleave="hover = false;
				animation = 0" v-on:mouseover="hover = true; styling = 'width: 80vw;'; model = 'path'; 
				animate()" v-on:click="switchPage('paths')">Pebble a Path Graph</button>

				<button v-on:mouseleave="hover = false; animation = 0" v-on:mouseover="hover = true; 
				styling = 'width: 25vw;'; model = 'complete'; animate()" 
				v-on:click="switchPage('complete')">Pebble a Complete Graph</button>

				<button v-on:mouseleave="hover = false; animation = 0" v-on:mouseover="hover = true; 
				styling = 'width: 25vw;'; model = 'cycle'; animate()" 
				v-on:click="switchPage('cycle')">Pebble a Cycle Graph</button>

			</div>

			<div v-if="hover && selected === ''">
				<div v-for="step in steps" :key="step">
					<img :style="styling" v-if="animation === step" 
					:src="require(`./assets/${model}/${step}.svg`)" alt="animation">
				</div>
				
				
			</div>

		</center>
		
    </div>
</template>

<script>

import Paths from './components/Paths.vue'
import Complete from './components/Complete.vue'
import Cycles from './components/Cycles.vue'

export default {
	name: 'App',
	components: {
		Paths,
		Complete,
		Cycles
	},
	data: () => {
		return {
			model: '',
			hover: true,
			selected: '',
			animation: 0,
			steps: [1,2,3,4,5,6,7,8,9,10,11],
			styling: '',
		}
	},
	mounted() {

	},
	watch: {
	
	},
	methods: {
		switchPage(selected) {
			this.selected = selected
		},
		animate() {
			console.log(this.animation, this.hover)
			this.animation++;
			if (this.animation < this.steps.length && this.hover) setTimeout(this.animate, 500);
		},
	},
	computed: {

	}
}
</script>

<style>
.main-container {
	/* border: 5px solid black; */
}
button {
	background-color: white;
	border-radius: 25px;
	margin: 2.5%;
	padding: 3%;
	font-size: 1.5rem;
	cursor: pointer;
	font-family: monospace;
	transition: 1s ease-out;
}
button:hover {
	background-color: rgb(100, 196, 228);
    box-shadow: grey 30px 50px 40px;
}
input {
	width: 25vw;
	font-size: 20pt;
	padding: 1%;
	border-radius: 10px;
}
body {
	font-family: monospace;
	font-size: 1.5rem;
	background-color: rgb(240, 240, 240);
	cursor: default;
}
.home {
	position: sticky;
	bottom: 0;
}
</style>
