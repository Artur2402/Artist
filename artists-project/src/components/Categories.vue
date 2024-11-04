<template>
	<div class="categories">
		<h2 class="categories__title">Categories</h2>
		<div class="categories__container">
			<div
				v-for="(category, index) in categories"
				:key="index"
				class="categories__container-elem"
			>
				<a href="#" class="categories__container-link">{{ category.name }}</a>
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
	text-align: center;
}

.categories__container {
	display: grid;
	grid-template-columns: repeat(4, 1fr); /* Четыре элемента в строку */
	gap: 20px;
	width: 100%;
	max-width: 1200px;
	padding: 20px;
	margin: 20px;
}

.categories__container-elem {
	width: 100%;
}

.categories__container-link {
	display: block;
	width: 100%;
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

/* Адаптивность для среднего экрана: 3 категории в строку */
@media (max-width: 992px) {
	.categories__container {
		grid-template-columns: repeat(3, 1fr); /* Три элемента в строку */
	}
}

/* Адаптивность для небольших экранов: 2 категории в строку */
@media (max-width: 768px) {
	.categories__container {
		grid-template-columns: repeat(2, 1fr); /* Два элемента в строку */
	}
}

/* Адаптивность для маленьких экранов: 1 категория в строку */
@media (max-width: 480px) {
	.categories__container {
		grid-template-columns: 1fr; /* Один элемент в строку */
	}
	.categories__title {
		font-size: 32px; /* Уменьшаем размер заголовка для мобильных устройств */
	}
}
</style>
