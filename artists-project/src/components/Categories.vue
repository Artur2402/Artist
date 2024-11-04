<template>
	<div class="categories">
		<h2 class="categories__title">Categories</h2>
		<div class="categories__container">
			<!-- Цикл по строкам, каждая строка содержит максимум 4 категории -->
			<div
				class="categories__container-row"
				v-for="(row, rowIndex) in categoryRows"
				:key="rowIndex"
			>
				<div
					class="categories__container-elem"
					v-for="category in row"
					:key="category.name"
				>
					<a href="#" class="categories__container-link">{{ category.name }}</a>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			// Массив категорий
			categories: [
				{ name: 'Category 1' },
				{ name: 'Category 2' },
				{ name: 'Category 3' },
				{ name: 'Category 4' },
				{ name: 'Category 5' },
				{ name: 'Category 6' },
				{ name: 'Category 7' },
				{ name: 'Category 8' },
			],
		}
	},
	computed: {
		// Делим категории на строки по 4 элемента
		categoryRows() {
			const rows = []
			for (let i = 0; i < this.categories.length; i += 4) {
				rows.push(this.categories.slice(i, i + 4))
			}
			return rows
		},
	},
}
</script>

<style scoped>
.categories {
	display: flex;
	flex-direction: column;
	align-items: center;
	margin: 20px 0;
}

.categories__title {
	color: white;
	font-size: 50px;
	font-weight: 600;
}

.categories__container {
	margin: 60px 0;
	width: 100%;
	max-width: 1200px;
}

/* Стили для строки с категориями */
.categories__container-row {
	display: flex;
	justify-content: space-around;
	margin-bottom: 80px;
}

/* Стили для элемента категории */
.categories__container-link {
	position: relative;
	width: 200px;
	margin: 20px;
	padding: 20px;
	background: rgba(255, 255, 255, 0.6);
	box-shadow: 0 5px 15px rgba(105, 105, 105, 0.7);
	font-size: 20px;
	text-align: center;
	transition: 0.2s ease-in-out;
}

.categories__container-link:hover {
	background: rgba(255, 255, 255, 0.8);
	box-shadow: 0 25px 125px rgba(255, 255, 255, 0.7);
	transform: scale(1.1);
	transition-delay: 0.2s;
}
</style>
