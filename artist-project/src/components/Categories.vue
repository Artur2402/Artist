<template>
	<div class="container">
		<div class="row">
			<div class="col-4" v-for="category in categories" :key="category.id">
				<div class="category-box">
					{{ category.name }}
				</div>
			</div>
		</div>
	</div>
</template>

<script setup>
const categories = [
	{id: 1, name: "Category 1"},
	{id: 2, name: "Category 2"},
	{id: 3, name: "Category 3"}
]
</script>

<style scoped>
.category-box {
	background-color: #f8f9fa;
	border: 1px solid #dee2e6;
	padding: 20px;
	margin-bottom: 20px;
	text-align: center;
	font-weight: bold;
}
</style>