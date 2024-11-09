<template>
	<div class="audio-player">
		<div class="audio-player__container" data-start="-10">
			<!-- Информация о песне -->
			<div class="audio-player__song-info" data-url="assets/musics/1.mp3"></div>

			<!-- Верхняя часть плеера -->
			<div class="audio-player__top">
				<div class="audio-player__cover">
					<img src="../assets/images/album-1.jpg" alt="song" />
				</div>
				<div class="audio-player__details" data-url="assets/musics/1.mp3">
					<h6 class="audio-player__title">Hands All Over</h6>
					<span class="audio-player__subtitle">New Single</span>
				</div>
				<div class="audio-player__share">
					<a href="#"><i class="fab fa-apple"></i></a>
					<a href="#"><i class="fab fa-soundcloud"></i></a>
					<a href="#"><i class="fab fa-spotify"></i></a>
				</div>
			</div>

			<!-- Нижняя часть плеера -->
			<div class="audio-player__bottom">
				<div class="audio-player__controls">
					<button class="audio-player__play-pause" @click="togglePlayPause">
						<span
							:class="{
								'audio-player__icon--play': !isPaused,
								'audio-player__icon--pause': isPaused,
							}"
						></span>
					</button>
					<span class="audio-player__current-time">01:53</span>
				</div>

				<div class="audio-player__progress">
					<progress class="audio-player__progress-bar"></progress>
				</div>

				<span class="audio-player__duration">03:45</span>

				<div class="audio-player__volume">
					<div class="audio-player__volume-control">
						<button class="audio-player__mute" @click="toggleMute">
							<span
								:class="{
									'audio-player__icon--mute': isMuted,
									'audio-player__icon--unmute': !isMuted,
								}"
							></span>
						</button>
						<input
							type="range"
							class="audio-player__volume-slider"
							v-model="volume"
							:disabled="isMuted"
						/>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script setup>
import { ref } from 'vue'

const isPaused = ref(true)
const isMuted = ref(false)
const volume = ref(100);

function togglePlayPause() {
	isPaused.value = !isPaused.value
}

function toggleMute() {
	isMuted.value = !isMuted.value
	// При активации mute, устанавливаем ползунок в 0 (выключить звук)
  if (isMuted.value) {
    volume.value = 0;
  } else {
    // Восстанавливаем громкость, если она была не в 0
    // Можно добавить условие для восстановления первоначальной громкости
    volume.value = 100;
  }
}
</script>

<style scoped>
/* Основной контейнер плеера */
.audio-player {
	width: 100%;
	color: #fff;
}

.audio-player__container {
	position: relative;
	background: rgba(255, 255, 255, 0.1);
	backdrop-filter: blur(100px);
	border-radius: 8px 8px 0 0;
	padding: 20px;
	box-sizing: border-box;
	height: 214px;
}

/* Верхняя часть плеера */
.audio-player__top {
	display: flex;
	align-items: center;
	justify-content: space-between;
}

.audio-player__cover img {
	width: 100px;
	border-radius: 4px;
}

.audio-player__details {
	flex: 1;
	margin-left: 15px;
}

.audio-player__title {
	font-size: 23px;
	font-weight: bold;
	margin: 0;
}

.audio-player__subtitle {
	font-size: 14px;
	color: rgba(255, 255, 255, 0.7);
}

.audio-player__share a {
	color: #fff;
	font-size: 1.2rem;
	margin-left: 10px;
}

/* Нижняя часть плеера */
.audio-player__bottom {
	display: flex;
	align-items: center;
	margin-top: 20px;
}

.audio-player__controls,
.audio-player__progress,
.audio-player__duration {
	display: flex;
	align-items: center;
}

/* Стили для иконок Play и Pause */
.audio-player__play-pause {
	background: none;
	border: none;
	cursor: pointer;
	padding: 0 10px;
	font-size: 24px;
	display: flex;
	align-items: center;
	justify-content: center;
	color: #fff;
}

.audio-player__icon--play::after {
	content: '\EFD9'; /* Символ play */
	font-family: 'remixicon' !important;
	font-style: normal;
}

.audio-player__icon--pause::after {
	content: '\F012'; /* Символ pause */
	font-family: 'remixicon' !important;
	font-style: normal;
}

/* Стили для иконок mute/unmute */
.audio-player__icon--mute::after {
	content: '\F29E'; /* Символ mute */
	font-family: 'remixicon' !important;
	font-style: normal;
	font-size: 24px;
}

.audio-player__icon--unmute::after {
	content: '\F2A1'; /* Символ unmute */
	font-family: 'remixicon' !important;
	font-style: normal;
	font-size: 24px;
}

/* Кнопка mute/unmute */
.audio-player__mute {
	background: none;
	border: none;
	cursor: pointer;
	padding: 5px;
	font-size: 24px;
	color: #fff;
	margin-left: 13px;
}

.audio-player__current-time {
	font-size: 0.875rem;
	margin-right: 10px;
}

.audio-player__duration {
	font-size: 0.875rem;
	margin-left: 10px;
}

.audio-player__progress {
	flex-grow: 1;
	margin: 0 15px;
}

.audio-player__progress-bar {
	width: 100%;
	height: 5px;
	border-radius: 3px;
	background: rgba(255, 255, 255, 0.3);
}

.audio-player__volume {
	display: flex;
	align-items: center;
	padding: 4px;
	border-radius: 3px;
}

.audio-player__volume-slider {
	width: 100px;
	margin-right: 10px;
	height: 5px;
	background: rgba(255, 255, 255, 0.3); /* Совпадающий с прогресс-баром фон */
	-webkit-appearance: none;
	appearance: none;
	border-radius: 3px;
	cursor: pointer;
	transform: translateY(-5px);
}

.audio-player__volume-slider::-webkit-slider-thumb {
	-webkit-appearance: none;
	appearance: none;
	width: 16px;
	height: 16px;
	background: #fff;
	border-radius: 50%;
	cursor: pointer;
}

.audio-player__volume-slider::-moz-range-thumb {
	width: 16px;
	height: 16px;
	background: #fff;
	border-radius: 50%;
	cursor: pointer;
}

@media (max-width: 480px) {
	.audio-player__volume-slider {
	width: 60px;
	}

	.audio-player__progress {
		margin: 0;
	}
}
</style>
