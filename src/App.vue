<template>
<div id="app">
	<h1>Barbell Racking Calculator</h1>
	<input type="number" v-model="weight" step="5" min="45" @input="calculate" /> lbs

	<div class="rack">
		<div class="bar">{{barWeight}}</div>
		<div v-for="plate in plates">
			<div class="plate" :style="{width: 30+(plate*4)+'px'}">{{plate}}</div>
		</div>
	</div>
</div>
</template>

<script>
export default {
	name: 'App',
	data () {
		return {
			weight: 45,
			barWeight: 45,
			plates: [],
			weights: [45, 35, 25, 10, 5, 5, 2.5, 1.25]
		};
	},
	methods: {
		calculate () {
			this.plates = [];
			var left = this.weight - this.barWeight;
			while (left > 0) {
				// track if we found a plate, otherwise we will spin forever
				var foundOne = false;
				for (var i = 0; i < this.weights.length; i++) {
					var amount = this.weights[i] * 2;
					if (amount <= left) {
						left -= amount;
						this.plates.push(this.weights[i]);
						foundOne = true;
						break;
					}
				}
				if (!foundOne) break;
			}
		}
	}
};
</script>

<style>
#app {
	font-family: sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
.rack {
	margin: 20px auto;
}
.bar {
	width: 24px;
	margin: 4px auto;
	background: #e4e4e4;
	height: 50px;
	line-height: 50px;
	border: 2px solid #c5c5c5;
	border-radius: 5px;
}
.plate {
	margin: 4px auto;
	color: #fff;
	min-width: 30px;
	border: 2px solid #283544;
	border-radius: 5px;
	background: radial-gradient(circle, #666666, #444444);
}
input {
	font-size: 18pt;
	text-align: center;
	padding: 5px;
	border-radius: 4px;
	border: 1px solid #cad3dc;
	max-width: 80px;
}
</style>
