<script setup>
import Header from '@/components/Header.vue'
import Slider from '@/components/Slider.vue'
import Categories from '@/components/Categories.vue'
import Artists from '@/components/Artists.vue'
import Footer from '@/components/Footer.vue'
</script>

<template>
	<Header />
	<h2 class="categories__title" style="padding-top: 80px;">Videos</h2>
	<Slider />
	<Categories />
	<Artists />
	<Footer />
</template>

<style>
.categories__title {
	color: white;
	font-size: 50px;
	font-weight: 600;
	text-align: center;
}
</style>
