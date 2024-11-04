<template>
	<header class="header">
		<a href="" class="header__logo">
			<img src="../assets/images/logo.png" alt="logo" />
		</a>
		<nav v-if="!isMobileMenuOpen" class="header__menu">
			<ul class="header__menu-list">
				<li
					class="header__menu-item"
					v-for="(item, index) in menuItems"
					:key="index"
				>
					<!-- Основное меню -->
					<a
						href="#"
						class="flip-animate"
						:class="{ active: activeLink === item.name }"
						@click="setActiveLink(item.name)"
					>
						<span :data-hover="item.name">{{ item.name }}</span></a
					>
					<!-- Подменю -->
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
		<div class="header__buttons">
			<button type="button" class="header__menu-shop">
				<img src="../assets/images/icons8-сумка-для-покупок-24.png" alt="" />
			</button>
			<button
				@click="toggleMobileMenu"
				class="header__menu-toggle"
				v-if="isMobileView"
			>
				<img
					src="../assets/images/icons8-xbox-menu-50.png"
					alt="Menu Icon"
					class="header__menu-icon"
				/>
			</button>
		</div>
		<div
			v-if="isMobileMenuOpen"
			class="mobile-menu-overlay"
			@click="toggleMobileMenu"
		>
			<div class="mobile-menu" @click.stop>
				<ul class="mobile-menu__list">
					<li
						class="mobile-menu__item"
						v-for="(item, index) in menuItems"
						:key="index"
					>
						<!-- Мобильное меню -->
						<a
							href="#"
							:class="{ active: activeLink === item.name }"
							@click.prevent="setActiveLink(item.name)"
						>
							{{ item.name }}
						</a>
						<ul
							v-if="item.submenu && activeSubMenuIndex === index"
							class="mobile-submenu"
						>
							<li v-for="(subItem, subIndex) in item.submenu" :key="subIndex">
								<!-- Подпункты мобильного меню -->
								<a href="#" @click.prevent="setActiveLink(subItem)">{{
									subItem
								}}</a>
							</li>
						</ul>
					</li>
				</ul>
			</div>
		</div>
	</header>
</template>

<script setup>
import { ref } from 'vue'

// Данные для меню
const menuItems = [
	{ name: 'Home', submenu: ['Item 1', 'Item 2', 'Item 3', 'Item 4', 'Item 5'] },
	{ name: 'Discography', submenu: ['Albums', 'Single Album'] },
	{ name: 'Events', submenu: ['All Events', 'Single Event'] },
	{ name: 'Gallery' },
	{ name: 'Videos', submenu: ['Video Gallery', 'Single Video'] },
	{ name: 'Shop', submenu: ['All Products', 'Single Product'] },
	{ name: 'News', submenu: ['All News', 'Single News'] },
	{ name: 'Contact' },
]

// Хук для отслеживания активной ссылки
const activeLink = ref(null)
const activeSubMenuIndex = ref(null)
const isMobileMenuOpen = ref(false)
const isMobileView = ref(window.innerWidth <= 1200)

function setActiveLink(link, event) {
	activeLink.value = link
	isMobileMenuOpen.value = false // Закрываем меню после выбора
	activeSubMenuIndex.value = null // Сбрасываем активный подпункт
}

window.addEventListener('resize', () => {
	isMobileView.value = window.innerWidth <= 1200
})
// Функция для установки активной ссылки

function toggleMobileMenu() {
	isMobileMenuOpen.value = !isMobileMenuOpen.value
	activeSubMenuIndex.value = null // Сбрасываем активный подпункт при закрытии меню
}

function toggleSubMenu(index) {
	activeSubMenuIndex.value = activeSubMenuIndex.value === index ? null : index
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
	position: absolute;
	top: 100%;
	left: 0;
	background-color: #000;
	min-width: 150px;
	padding: 10px 0;
	box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
	z-index: 1000; /* Поверх других элементов */
	transform: translateY(20px);
	opacity: 0;
	visibility: hidden;
	transition: transform 0.3s ease, opacity 0.3s ease, visibility 0s 0.3s;
}

/* Показ выпадающего списка при наведении Показ выпадающего*/
.header__menu-item:hover .header__menu-dropdown,
.header__menu-dropdown:hover {
	display: block;
	transform: translateY(0);
	opacity: 1;
	visibility: visible;
	transition: transform 0.3s ease, opacity 0.3s ease, visibility 0s;
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
	transition: color 0.3s;
	outline: none;
}

/* Кнопка магазина */
.header__menu-shop {
	outline: none;
	background: none;
	border: none;
}

.header__menu-toggle {
	background: none;
	border: none;
	color: #fff;
	font-size: 1.2rem;
	cursor: pointer;
	display: none;
}

.header__menu-icon {
	width: 30px;
	height: 30px;
}

.header__buttons {
	display: flex;
	align-items: center;
	gap: 10px;
}

button {
	cursor: pointer;
	outline: none;
	background: none;
	border: none;
}

a.flip-animate {
	perspective: 1000px;
}

a.flip-animate span {
	position: relative;
	display: inline-block;
	padding: 0;
	transition: transform 0.3s;
	transform-origin: 50% 0;
	transform-style: preserve-3d;
}

a.flip-animate span:before {
	position: absolute;
	top: 100%;
	left: 0;
	width: 100%;
	height: 100%;
	content: attr(data-hover);
	transition: color 0.3s;
	transform: rotateX(-90deg);
	transform-origin: 50% 0;
	text-align: center;
}

a.flip-animate:hover span,
a.flip-animate:focus span {
	transform: rotateX(90deg) translateY(-22px);
}

.mobile-menu-overlay {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background-color: rgba(0, 0, 0, 0.95);
	display: flex;
	align-items: center;
	justify-content: center;
	z-index: 1000;
}

.mobile-menu {
	display: flex;
	flex-direction: column;
	gap: 20px;
}

.mobile-menu__list {
	list-style: none;
	text-align: center;
	padding: 0;
}

.mobile-menu__item a {
	color: #fff;
	font-size: 1.5rem;
	text-decoration: none;
}

.mobile-menu__item a.active-item {
	color: #ffcc00; /* Активный пункт */
}

/* Стили для подпунктов */
.mobile-submenu {
	list-style: none;
	padding: 10px 0;
	text-align: center;
	background-color: #333;
	border-radius: 5px;
}

.mobile-submenu li a {
	color: #fff;
	font-size: 1.2rem;
}

.mobile-submenu li a:hover {
	color: #ffcc00; /* Цвет при наведении */
}

.header__menu-item:hover .header__menu-dropdown {
	display: block;
	transform: translateY(0);
	opacity: 1;
	visibility: visible;
	transition: opacity 0.3s ease, transform 0.3s ease;
}

@media (max-width: 1200px) {
	.header__menu {
		display: none;
	}
	.header__menu-toggle {
		display: block;
	}
}
</style>
