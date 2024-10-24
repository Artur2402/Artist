<template>
	<header class="header">
		<a href="" class="header__logo">
			<img src="../assets/images/logo.png" alt="logo" />
		</a>
		<nav class="header__menu">
			<ul class="header__menu-list">
				<li class="header__menu-item">
					<a href="#">Home</a>
					<ul class="header__menu-dropdown">
						<li><a href="#">Item 1</a></li>
						<li><a href="#">Item 2</a></li>
						<li><a href="#">Item 3</a></li>
						<li><a href="#">Item 4</a></li>
						<li><a href="#">Item 5</a></li>
					</ul>
				</li>
				<li class="header__menu-item">
					<a href="#">Discography</a>
				</li>
				<li class="header__menu-item">
					<a href="#">Events</a>
				</li>
				<li class="header__menu-item">
					<a href="#">Gallery</a>
				</li>
				<li class="header__menu-item">
					<a href="#">Videos</a>
				</li>
				<li class="header__menu-item">
					<a href="#">Shop</a>
				</li>
				<li class="header__menu-item">
					<a href="#">News</a>
				</li>
				<li class="header__menu-item">
					<a href="#">Contact</a>
				</li>
			</ul>
		</nav>
		<button type="button" class="header__menu-shop">
			<img src="../assets/images/icons8-сумка-для-покупок-24.png" alt="" />
		</button>
	</header>
</template>

<script></script>

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
	padding-left: 0px;
}

.header__menu-dropdown {
	list-style: none;
	margin-top: 12px;
	margin-left: -20px;
	/* display: none; */
	background-color: #000;
	position: absolute;
	min-width: 150px;
	padding: 10px 20px;
	text-align: center;
}

li:hover .header__menu-dropdown {
	display: block;
}

.header__menu-dropdown li {
	padding: 7px;
	width: 100%;
}

a {
	color: #fff;
	text-decoration: none;
}

button {
	cursor: pointer;
	outline: none;
	background: none;
	border: none;
}
</style>
