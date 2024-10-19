<template>
	<div class="container">
		<h2 class="text-center">Артисты</h2>
		<div class="row">
			<div class="col-4" v-for="artist in artist" :key="artist.id">
				<div class="card">
					<img :src="artist.image" class="card-img-top" :alt="artist.name">
					<div class="card-body">
						<h5 class="card-title">{{ artist.name }}</h5>
						<p class="card-text">{{ artist.price }}</p>
						<a href="#" class="btn btn-primary">Подробнее</a>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script setup>
const artist = [
	{id: 1, name: "Artist 1", image: "/path/to/image1.jpg", price: "10000"},
	{id: 2, name: "Artist 2", image: "/path/to/image2.jpg", price: "20000"},
	{id: 3, name: "Artist 3", image: "/path/to/image3.jpg", price: "15000"}
]
</script>

<style scoped>
.card {
	margin-bottom: 20px;
}

.card-img-top {
	height: 200px;
	object-fit: cover;
}
</style>