<template>
	<div class="container">
		<!-- Отображаем активное изображение -->
		<div class="feature">
			<figure
				class="feature__item image-holder r-3-2 transition"
				:style="{ backgroundImage: 'url(' + featuredImage + ')' }"
			></figure>
		</div>
		<!-- Галерея изображений -->
		<div class="wrapper">
			<div
				class="gallery"
				:style="{ transform: 'translateX(' + galleryPosition + '%)' }"
			>
				<div v-for="image in images" :key="image" class="gallery__item-wrapper">
					<figure
						class="gallery__item image-holder r-3-2 transition"
						:class="{ active: image === featuredImage }"
						:style="{ backgroundImage: 'url(' + image + ')' }"
						@click="selectItem(image)"
						loading="lazy"
					></figure>
				</div>
			</div>
		</div>
		<!-- Управляющие кнопки -->
		<div class="controls">
			<button
				class="move-btn left"
				@mouseenter="startMoving('left')"
				@mouseleave="stopMoving"
			>
				&larr;
			</button>
			<button
				class="move-btn right"
				@mouseenter="startMoving('right')"
				@mouseleave="stopMoving"
			>
				&rarr;
			</button>
		</div>
	</div>
</template>

<script setup>
import { ref } from 'vue'

const images = [
	'https://s3-us-west-2.amazonaws.com/forconcepting/800Wide50Quality/car.jpg',
	'https://s3-us-west-2.amazonaws.com/forconcepting/800Wide50Quality/city.jpg',
	'https://s3-us-west-2.amazonaws.com/forconcepting/800Wide50Quality/deer.jpg',
	'https://s3-us-west-2.amazonaws.com/forconcepting/800Wide50Quality/flowers.jpg',
	'https://s3-us-west-2.amazonaws.com/forconcepting/800Wide50Quality/food.jpg',
]

const featuredImage = ref(images[0]) // Первое изображение по умолчанию
const galleryPosition = ref(0) // Позиция галереи
const itemWidth = 23 // Ширина элемента галереи в процентах
let scrollInterval = null

function selectItem(image) {
	featuredImage.value = image
}

function startMoving(direction) {
	stopMoving() // Останавливаем любое текущее движение
	scrollInterval = setInterval(() => {
		const maxPosition = -(itemWidth * (images.length - 4)) // Максимально возможное смещение влево

		if (direction === 'left') {
			// Двигаемся влево
			if (galleryPosition.value < 0) {
				galleryPosition.value += 0.3 // Медленная прокрутка влево
			}
		} else if (direction === 'right') {
			// Двигаемся вправо
			if (galleryPosition.value > maxPosition) {
				galleryPosition.value -= 0.3 // Медленная прокрутка вправо
			}
		}
	}, 10)
}

// Останавливаем движение
function stopMoving() {
	if (scrollInterval) {
		clearInterval(scrollInterval)
		scrollInterval = null
	}
}
</script>

<style scoped>
.container {
	width: 90%; /* Увеличиваем ширину контейнера */
	max-width: 800px; /* Максимальная ширина */
	margin: 0 auto;
}

.wrapper {
	overflow: hidden; /* Ограничивает выход галереи за границы */
}

.gallery {
	display: flex;
	transition: transform 0.3s ease; /* Плавный переход */
}

.gallery__item-wrapper {
	width: 23%; /* Сохраняем ширину для изображений в нижней панели */
	cursor: pointer;
	display: inline-block;
}

.image-holder {
	background-size: cover;
	background-position: center center;
	background-repeat: no-repeat;
}

.transition {
	transition: all 350ms ease-in-out;
}

.r-3-2 {
	width: 100%;
	padding-bottom: 66.667%;
	background-color: #ddd;
}

.gallery__item {
	opacity: 0.5;
	transition: opacity 0.3s ease;
}

.gallery__item.active {
	opacity: 1;
	border: 2px solid #ff632e; /* Подсветка активного изображения */
}

.controls {
	font-size: 0;
	border-top: none;
	text-align: center;
	margin-top: 10px; /* Отступ сверху для кнопок */
}

.move-btn {
	display: inline-block;
	width: 50%;
	border: none;
	color: #ccc;
	background-color: transparent;
	padding: 0.2em 1.5em;
	cursor: pointer;
}
</style>
