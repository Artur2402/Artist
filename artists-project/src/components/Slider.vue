<template>
	<div class="video-slider-container">
		<div class="video-slider">
			<!-- Слайды -->
			<div
				class="video-slider-slides"
				:style="{ transform: `translateX(-${current * 100}%)` }"
			>
				<div
					v-for="(video, index) in videos"
					:key="index"
					class="video-slider-slide"
				>
					<video :src="video.src" controls autoplay muted></video>
				</div>
			</div>

			<!-- Кнопки управления -->
			<div class="video-slider-controls" v-if="videos.length > 1">
				<button class="video-slider-control" @click="prevSlide">
					&lsaquo;
				</button>
				<button class="video-slider-control" @click="nextSlide">
					&rsaquo;
				</button>
			</div>

			<!-- Пагинация -->
			<div class="video-slider-pagination" v-if="videos.length > 1">
				<button
					v-for="(video, index) in videos"
					:key="index"
					:class="[
						'video-slider-pagination-btn',
						{ active: current === index },
					]"
					@click="jumpToSlide(index)"
				></button>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			videos: [
				{ id: 1, name: 'Video 1', src: 'video1.mp4' },
				{ id: 2, name: 'Video 2', src: 'video2.mp4' },
				{ id: 3, name: 'Video 3', src: 'video3.mp4' },
				{ id: 4, name: 'Video 4', src: 'video4.mp4' },
			],
			current: 0,
		}
	},
	methods: {
		nextSlide() {
			this.current = (this.current + 1) % this.videos.length
		},
		prevSlide() {
			this.current =
				(this.current - 1 + this.videos.length) % this.videos.length
		},
		jumpToSlide(index) {
			this.current = index
		},
	},
}
</script>

<style scoped>
.video-slider-container {
	width: 100vw;
	max-width: 1320px;
	overflow: hidden;
	margin: 0 auto;
	position: relative;
	margin-top: 30px;
}

.video-slider {
	width: 100%;
	position: relative;
}

.video-slider-slides {
	display: flex;
	transition: transform 0.5s ease;
}

.video-slider-slide {
	flex: 0 0 100%;
	display: flex;
	align-items: center;
	justify-content: center;
}

video {
	width: 100%;
	height: auto;
}

.video-slider-controls {
	position: absolute;
	top: 50%;
	width: 100%;
	display: flex;
	justify-content: space-between;
	transform: translateY(-50%);
	padding: 0 10px;
}

.video-slider-control {
	background: none;
	border: none;
	font-size: 2rem;
	cursor: pointer;
	opacity: 0.5;
	color: white;
}

.video-slider-pagination {
	margin-top: 20px;
	text-align: center;
}

.video-slider-pagination-btn {
	width: 10px;
	height: 10px;
	margin: 0 5px;
	border-radius: 50%;
	background-color: #ccc;
	border: none;
	cursor: pointer;
}

.video-slider-pagination-btn.active {
	background-color: #f0783d;
}

.video-slider-control:hover {
	opacity: 1; /* Увеличиваем непрозрачность при наведении */
}
</style>
