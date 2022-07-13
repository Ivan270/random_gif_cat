<template>
	<div class="cats-container">
		<div class="cats-title">
			<h1>RandomGif Cat Generator</h1>
		</div>
		<div class="form-container">
			<div class="cats-form">
				<form action="">
					<label for="">Titulo</label>
					<input type="text" v-model="titulo" id="form-title" />
					<label for="">Filtro</label>
					<select @change="changeFilter" id="form-filter">
						<option v-for="opt in filtersOpt" :key="opt" :value="opt">
							{{ opt }}
						</option>
					</select>
					<label for="">Color</label>
					<select @change="changeColor" id="form-color">
						<option
							v-for="color in colorsOpt"
							:key="color.color"
							:value="color.value"
						>
							{{ color.color }}
						</option>
					</select>
					<div class="color-box" :style="myStyles"></div>

					<label for="">Tamaño</label>
					<input
						type="number"
						min="1"
						max="600"
						@change="changeFontSize"
						id="form-size"
					/>
				</form>
			</div>
			<div class="cats-image">
				<img :src="img" alt="" />
			</div>
			<img :src="image" alt="" width="80px" id="cat-logo" />
		</div>
	</div>
</template>

<script>
	import cat from '@/assets/cat.png';
	export default {
		name: 'random-cat',
		// props: {},
		data: function () {
			return {
				titulo: 'miau',
				tamaño: '20',
				filter: 'none',
				color: 'white',
				filtersOpt: [
					'none',
					'blur',
					'mono',
					'sepia',
					'negative',
					'paint',
					// 'pixel',
				],
				colorsOpt: [
					{
						color: 'Blanco',
						value: 'white',
					},
					{
						color: 'Verde',
						value: 'green',
					},
					{
						color: 'Amarillo',
						value: 'yellow',
					},
					{
						color: 'Gris',
						value: 'gray',
					},
					{
						color: 'Rojo',
						value: 'red',
					},
					{
						color: 'Azul',
						value: 'blue',
					},
				],
				myStyles: {
					backgroundColor: this.color,
				},
				image: cat,
			};
		},
		computed: {
			img() {
				return `https://cataas.com/cat/gif/says/${this.titulo}?filter=${this.filter}&color=${this.color}&size=${this.tamaño}&type=or`;
			},
		},
		methods: {
			changeFontSize(event) {
				this.tamaño = event.target.value;
				console.log(this.tamaño);
			},
			changeColor(event) {
				this.color = event.target.value;
				this.myStyles.backgroundColor = this.color;
				console.log(this.color);
			},
			changeFilter(event) {
				this.filter = event.target.value;
				console.log(this.titulo);
				console.log(this.filter);
				console.log(this.color);
			},
		},
		// watch: {},
		// components: {},
		// mixins: [],
		// filters: {},
		// -- Lifecycle Methods
		// -- End Lifecycle Methods
	};
</script>

<style scoped>
	.cats-container {
		display: grid;
		grid-template-columns: repeat(12, 1fr);
		grid-template-rows: repeat(6, 1fr);
		grid-gap: 10px;
		height: 100vh;
	}

	.cats-title {
		margin-left: 10px;
		grid-column: 1/5;
		grid-row: span 6;
		display: grid;
		grid-template-rows: repeat(6, 1fr);
		place-content: center left;
	}
	.cats-title h1 {
		align-self: center;
		grid-row: 2/6;
		text-align: left;
		font-size: 50px;
		letter-spacing: 20px;
		line-height: 2;
		font-family: 'Anton', sans-serif;
		font-weight: 400;
		color: #f9f73b;
		position: relative;
		animation: move 1s 3;
	}
	#cat-logo {
		align-self: end;
		grid-row: 6/7;
		grid-column: 12/13;
	}
	.form-container {
		grid-column: 5/13;
		grid-row: 1/7;
		display: grid;
		grid-template-columns: repeat(12, 1fr);
		grid-template-rows: repeat(6, 1fr);
		grid-gap: 10px;
		background: #16beca;
	}
	.cats-form {
		grid-column: 3/12;
		grid-row: 1/2;
		display: grid;
		justify-content: start;
		align-items: end;
		font-size: 20px;
		font-weight: 300;
		color: white;
		text-align: left;
	}
	label {
		margin-left: 10px;
		margin-right: 10px;
		font-weight: 500;
		color: #f9f73b;
	}
	#form-title {
		padding-left: 5px;
		height: 30px;
		width: 60px;
		border: none;
		border-bottom: 2px solid white;
		background: none;
		color: white;
		font-family: 'Montserrat';
		font-size: 16px;
		font-weight: 300;
		transition: all 0.2s ease-out;
	}
	#form-title:focus {
		outline: none;
		width: 120px;
	}
	#form-filter {
		padding: 0 10px;
		border-radius: 15px;
		border: 2px solid white;
		background: none;
		color: white;
		font-family: 'Montserrat';
		font-size: 16px;
		font-weight: 300;
		cursor: pointer;
	}
	#form-filter option {
		background: #16beca;
		color: white;
	}
	#form-color {
		padding: 0 10px;
		border-radius: 15px;
		border: 2px solid white;
		background: none;
		color: white;
		font-family: 'Montserrat';
		font-size: 16px;
		font-weight: 300;
		cursor: pointer;
	}
	#form-color option {
		background: #16beca;
		color: white;
	}
	#form-size {
		padding-left: 5px;
		border: none;
		border-bottom: 2px solid white;
		background: none;
		color: white;
		font-family: 'Oswald';
		font-size: 16px;
		font-weight: 300;
	}
	#form-size:focus {
		outline: none;
	}
	.color-box {
		width: 30px;
		height: 30px;
		border: 2px solid #f9f73b;
		display: inline-block;
		border-radius: 50%;
		margin-left: 15px;
		margin-right: 15px;
	}
	form {
		display: flex;
	}
	.cats-image {
		grid-column: 3/11;
		grid-row: 2/6;
		display: grid;
		place-content: center;
		background: #fe91a8;
		border-radius: 15px;
		transition: transform 0.3s ease-in-out;
	}
	.cats-image:hover {
		transform: rotate(-2deg);
	}
	@keyframes move {
		0% {
			left: 0px;
		}
		33% {
			left: 15px;
		}
		100% {
			left: 0px;
		}
	}
</style>
