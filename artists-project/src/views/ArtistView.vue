<template>
	<Header />
	<OneArtist />
	<h4 class="artist__main-title">Video</h4>
	<Slider />
	<h4 class="artist__main-title">Gallery</h4>
	<Footer />
</template>

<script setup>
import OneArtist from '@/components/OneArtist.vue'
import Slider from '@/components/Slider.vue'
import Footer from '@/components/Footer.vue'
import Header from '@/components/Header.vue';

</script>

<style scoped>
.artist__main-title {
	background: linear-gradient(119deg, #ff632e 6.3%, #e84151 20.17%);
	-webkit-text-fill-color: transparent;
	background-clip: text;
	font-weight: 600;
	font-size: 48px;
	text-align: center;
	margin: 40px 0;
}
</style>
