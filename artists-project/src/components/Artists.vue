<template>
	<div class="artists">
		<h2 class="artists__title">Artists</h2>
		<ul class="artists__cards">
			<li v-for="artist in artists" :key="artist.id">
				<a href="#" class="artists__card">
					<img :src="artist.image" class="artists__card-image" alt="img" />
					<div class="artists__card-overlay">
						<div class="artists__card-header">
							<img class="card-header__img" :src="artist.profileImage" alt="" />
							<div class="card-header__text">
								<h3 class="card__header-title">{{ artist.name }}</h3>
							</div>
						</div>
						<p class="card__header-description">
							{{ artist.description }}
						</p>
					</div>
				</a>
			</li>
		</ul>
		<div class="all-artists">
			<a href="#" class="all-artists__button">All Artists</a>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			artists: [
				{
					id: 1,
					name: 'Jessica Parker',
					image: 'https://i.imgur.com/oYiTqum.jpg',
					profileImage: 'https://i.imgur.com/7D7I6dI.png',
					description:
						'Lorem ipsum dolor sit amet consectetur adipisicing elit. Asperiores, blanditiis?',
				},
				{
					id: 2,
					name: 'Jessica Parker',
					image: 'https://i.imgur.com/oYiTqum.jpg',
					profileImage: 'https://i.imgur.com/7D7I6dI.png',
					description:
						'Lorem ipsum dolor sit amet consectetur adipisicing elit. Asperiores, blanditiis?',
				},
				{
					id: 3,
					name: 'Jessica Parker',
					image: 'https://i.imgur.com/oYiTqum.jpg',
					profileImage: 'https://i.imgur.com/7D7I6dI.png',
					description:
						'Lorem ipsum dolor sit amet consectetur adipisicing elit. Asperiores, blanditiis?',
				},
				{
					id: 4,
					name: 'Jessica Parker',
					image: 'https://i.imgur.com/oYiTqum.jpg',
					profileImage: 'https://i.imgur.com/7D7I6dI.png',
					description:
						'Lorem ipsum dolor sit amet consectetur adipisicing elit. Asperiores, blanditiis?',
				},
			],
		}
	},
}
</script>

<style scoped>
.artists {
	margin: 30px auto;
}

.artists__title {
	font-size: 45px;
	margin-bottom: 1.5rem;
	color: #fff;
	text-align: center;
	width: 100%;
}
.artists__cards {
	display: grid;
	grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
	gap: 1.5rem;
	margin: 4rem 5vw;
	padding: 0;
	list-style-type: none;
}

.artists__card {
	position: relative;
	display: block;
	height: 100%;
	border-radius: calc(40 * 1px);
	overflow: hidden;
	text-decoration: none;
}

.artists__card-image {
	width: 100%;
	height: auto;
}

.artists__card-overlay {
	position: absolute;
	bottom: 0;
	left: 0;
	right: 0;
	z-index: 1;
	border-radius: calc(40 * 1px);
	background-color: #fff;
	transform: translateY(100%);
	transition: 0.2s ease-in-out;
}

.artists__card:hover .artists__card-overlay,
.artists__card:hover .artists__card-header {
	transform: translateY(0);
}

.artists__card-header {
	position: relative;
	display: flex;
	align-items: center;
	gap: 2em;
	padding: 2em;
	border-radius: calc(40 * 1px) 0 0 0;
	background-color: #fff;
	transform: translateY(-100%);
	transition: 0.2s ease-in-out;
}

.card-header__img {
	flex-shrink: 0;
	width: 50px;
	height: 50px;
	border-radius: 50%;
}

.card__header-title {
	font-size: 1em;
	margin: 0 0 0.3em;
	color: #6a515e;
}

.card__header-description {
	padding: 0 2em 2em;
	margin: 0;
	color: #d7bdca;
	display: -webkit-box;
	-webkit-box-orient: vertical;
	-webkit-line-clamp: 3;
	overflow: hidden;
}

.all-artists {
	display: flex;
	justify-content: center;
	margin-top: 2rem;
}

.all-artists__button {
	padding: 0.75rem 1.5rem;
	background-color: #6a515e;
	color: #fff;
	border: none;
	border-radius: 8px;
	text-decoration: none;
	font-weight: bold;
	transition: background-color 0.3s;
}

.all-artists__button:hover {
	background-color: #8b697c;
}
</style>
