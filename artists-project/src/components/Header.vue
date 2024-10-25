<template>
	<header class="header">
		<a href="" class="header__logo">
			<img src="../assets/images/logo.png" alt="logo" />
		</a>
		<nav class="header__menu">
			<ul class="header__menu-list">
				<li
					class="header__menu-item"
					v-for="(item, index) in menuItems"
					:key="index"
				>
					<a
						href="#"
						:class="{ active: activeLink === item.name }"
						@click="setActiveLink(item.name)"
						>{{ item.name }}</a
					>
					<ul class="header__menu-dropdown" v-if="item.submenu">
						<li v-for="(subItem, subIndex) in item.submenu" :key="subIndex">
							<a
								href="#"
								:class="{ active: activeLink === subItem }"
								@click="setActiveLink(subItem)"
								>{{ subItem }}</a
							>
						</li>
					</ul>
				</li>

			</ul>
		</nav>
		<button type="button" class="header__menu-shop">
			<img src="../assets/images/icons8-сумка-для-покупок-24.png" alt="" />
		</button>
	</header>
</template>

<script setup>
import { ref } from 'vue';

// Данные для меню
const menuItems = [
	{ name: 'Home', submenu: ['Item 1', 'Item 2', 'Item 3', 'Item 4', 'Item 5'] },
	{ name: 'Discography', submenu: ['Albums', 'Single Album'] },
	{ name: 'Events', submenu: ['All Events', 'Single Event'] },
	{ name: 'Gallery' },
	{ name: 'Videos', submenu: ['Video Gallery', 'Single Video'] },
	{ name: 'Shop', submenu: ['All Products', 'Single Product'] },
	{ name: 'News', submenu: ['All News', 'Single News'] },
	{ name: 'Contact' }
];

// Хук для отслеживания активной ссылки
const activeLink = ref(null);

// Функция для установки активной ссылки
function setActiveLink(link) {
	activeLink.value = link;
}
</script>

<style>
.header {
	display: flex;
	justify-content: space-between;
	align-items: center;
	padding: 30px 60px 0;
}

.header__menu-list {
	display: flex;
	gap: 35px;
	margin-right: 20px;
	list-style: none;
	padding-left: 0;
}

.header__menu-item {
	position: relative; /* Чтобы меню выпадало относительно каждого элемента */
}

.header__menu-dropdown {
	list-style: none;
	margin-left: -20px;
	display: none; /* Изначально скрываем список */
	position: absolute;
	top: 100%;
	left: 0;
	background-color: #000;
	min-width: 150px;
	padding: 10px 0;
	box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
	z-index: 1000; /* Поверх других элементов */
}

/* Показ выпадающего списка при наведении */
.header__menu-item:hover .header__menu-dropdown,
.header__menu-dropdown:hover {
	display: block;
}

.header__menu-dropdown li {
	padding: 7px 20px;
	width: 100%;
}

.header__menu-dropdown li a {
	color: #616161;
	display: block;
	transition: background-color 0.3s ease; /* Плавный переход */
}

.header__menu-dropdown li a:hover {
	color: #fff; /* Цвет текста при наведении */
}

.header__menu-dropdown li a.active {
	color: #fff; /* Цвет текста при наведении */
}

/* Основные стили для ссылок */
a {
	color: #fff;
	text-decoration: none;
}

/* Кнопка магазина */
.header__menu-shop {
	cursor: pointer;
	outline: none;
	background: none;
	border: none;
}

button {
	cursor: pointer;
	outline: none;
	background: none;
	border: none;
}
</style>
