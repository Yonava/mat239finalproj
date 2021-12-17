<template>
    <div id="app">

		<div style="font-size: 1rem; border: 2px dashed black; padding: 2%;" v-if="info && selected===''">
			<h1 style="margin-top: 1vh;">Welcome to the 2-player game of graph pebbling:</h1>
			
			<h2>There are no turns in this game, just rounds. In round 1, player 1 does what they 
			need, in round 2, player 2 gets as many moves as they need.</h2>
           
			<h2>Player 1:</h2>
           
			<p>The goal of player one is to analyze the playing surface (a graph) and choose any Vertice on the graph
			as the target. After player 1 chooses the target vertex, they are tasked with distributing 
			pebbles (currency) across other
			Vertices on the graph.</p>

			<h2>Player 2:</h2>

			<p>After player 1 has finished placing the pebbles, player 2 takes over. Pebbles placed by 
			player 1 act as currency for player 2 in the second round. Player 2s mission is to get at least 1 pebble 
			on the target Vertex by maneuvering the pebbles on the playing surface, however there is a catch. 
			Every time player 2 moves pebbles from 1 Vertice to another along an edge, half the pebbles are removed 
			from the game (lost to taxation). If player 2 moves an odd number of pebbles, the tax is rounded up 
			(IE moving 9 pebbles costs 5 pebbles).</p>

			<h3>Definition: What Is The Pebbling Number of a Graph?</h3>

			<p>The pebbling number of a graph is, simply put, the fewest pebbles given to player 1 
			that would make it impossible to prevent player 2 from winning.</p>

		</div>

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
				
				<button class="info" @click="info = !info">Toggle Rules</button>
				
				<h1>Choose Which Graph To Explore:</h1>

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
			info: false,
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
			this.animation++;
			if (this.animation < this.steps.length && this.hover) setTimeout(this.animate, 500);
		},
	},
	computed: {

	}
}
</script>

<style>
.info {
	transition: 0s;
	padding: 10px;
	border-radius: 10px;
	margin: 5px;
	background-color: greenyellow;
}
.info:hover {
	box-shadow: none;
	background-color: yellow;
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
