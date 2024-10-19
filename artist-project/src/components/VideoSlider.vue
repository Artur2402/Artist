<template>
	<div id="videoSlider" class="carousel slide" data-bs-ride="carousel">
		<div class="carousel-inner">
			<div class="carousel-item" :class="{active: index === 0}" v-for="(video, index) in videos" :key="index">
				<video v-if="video.type === 'local'" class="d-block w-100" controls>
					<source :src="video.src" type="video/mp4">
					Your browser does not support the video tag
				</video>
				<iframe 
				v-else-if="video.type === 'youtube'" 
				class="d-block w-100" 
				:src="`https://www.youtube.com/embed/${video.src}`"
				frameborder="0"
				allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
				allowfullscreen
				></iframe>
			</div>
		</div>
		<button class="carousel-control-prev" type="button" data-bs-target="#videoSlider" data-bs-slide="prev">
			<span class="carousel-control-prev-icon" aria-hidden="true"></span>
			<span class="visual-hidden">Previous</span>
		</button>
		<button class="carousel-control-next" type="button" data-bs-target="#videoSlider" data-bs-slide="next">
			<span class="carousel-control-next-icon" aria-hidden="true"></span>
			<span class="visual-hidden">Next</span>
		</button>
	</div>
</template>

<script setup>
const videos = [
	{type: 'local', src: ''},
	{type: 'youtube', src: ''}
]
</script>

<style scoped>
.carousel-item {
	height: 400px;
}

video, iframe {
	height: 100%;
}
</style>