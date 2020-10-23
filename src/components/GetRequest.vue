<template>
	<div class="card m-6">
		<div style="width: 50%;">
			<ul id="example-2">
				<li v-for="(item, index) in allPostalCodes">
					{{ item.cp }} - {{ item.nom_ent }} -
					<button v-on:click="getdata(item.cp)">Ver Resultados</button>
				</li>
			</ul>
		</div>
	</div>
</template>

<script>
export default {
	name: "get-request",
	data() {
		return {
			allPostalCodes: null,
			results: null
		};
	},
	created() {
		// Simple GET request using fetch
		fetch("http://50.17.125.152:5000/getAllAviableCP")
			.then(response => response.json())
			.then(data => (this.allPostalCodes = data));
	},
	methods: {
		getdata: function (cp) {
			fetch("http://50.17.125.152:5000/getPotTotByCP/" + cp)
				.then(response => response.json())
				.then(data => (this.results = data))
				.then(data => alert('Codigo Postal: ' + data[0].cp
					+ '\nPoblacion Total: ' + data[0].pobtot
					+ '\nPoblación Femenina: ' + data[0].pobfem
					+ '\nPoblacion Masculina: ' + data[0].pobmas));
		}
	}
};
</script>
