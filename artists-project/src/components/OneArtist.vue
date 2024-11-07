<template>
	<div class="artist">
		<div class="artist__header">
			<span style="opacity: 0.6;">live band</span>
			<h1 class="artist__header-title">Омар хаям</h1>
		</div>
		<div class="artist__main">
			<div class="artist__main-description">
				<p>
					Мы самая востребованная группа в Казахстане из Узбекистана. Мы были
					приглашены 2023 году на 168 мероприятии. 2024 году мы уверены что мы
					порадуем вас еще больше
				</p>
				<h6>Качественный репертуар</h6>
				<p>
					В репертуаре более 160 песен на разных языках в том числе казахские
					кавер хиты. Которые каждый раз обновляется новыми нашими песнями и
					кавер хитами
				</p>
				<h6>Яркие костюмы</h6>
				<p>
					Наши костюмы создавали лучшие дизайнеры Ташкента из дорогих и
					качественных материалов. За одно торжество мы меняем костюмы менее 3-х
					раз
				</p>
				<h6>Команда профессионалов</h6>
				<p>
					Гастрольная группа состоит из 8-ми человек. 2 солиста /Акмаль & Дана/
					4 музыканта, звукорежиссер и концертного директора
				</p>
			</div>
		</div>
	</div>
</template>

<script>

</script>

<style scoped>
.artist {
	min-height: 100vh;
}

.artist__header {
	background-image: url('../assets/images/1.jpg');
	background-size: cover;
	background-position: center;
	width: 100%;
	height: 100vh; /* Ограниченная высота */
	display: flex;
	flex-direction: column;
	justify-content: center;
	color: white;
	padding: 0 100px;
}

.artist__header-title {
	background: linear-gradient(119deg, #ff632e 6.3%, #e84151 20.17%);
	-webkit-text-fill-color: transparent;
	background-clip: text;
	font-weight: 600;
	font-size: 102px;
}

.artist__main {
	font-size: 22px;
	color: #fff;
}

.artist__main-description {
	padding: 0 100px;
}

h6 {
	font-weight: 600;
	font-size: 23px;
}

@media (min-width: 1024px) {
	.artist {
		display: flex;
		flex-direction: column;
		align-items: center;
	}
}
</style>