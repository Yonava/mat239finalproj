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
				<button v-on:click="switchPage('paths')">Pebble a Path Graph</button>
				<button v-on:click="switchPage('complete')">Pebble a Complete Graph</button>
				<button v-on:click="switchPage('cycle')">Pebble a Cycle Graph</button>
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
			selected: '',
		}
	},
	mounted() {

	},
	watch: {
	
	},
	methods: {
		switchPage(selected) {
			this.selected = selected
		}
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
}
button:hover {
	background-color: rgb(100, 196, 228);
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
}
.home {
	position: sticky;
	bottom: 0;
}
</style>
