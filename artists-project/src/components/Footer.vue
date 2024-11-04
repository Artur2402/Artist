<template>
	<footer class="footer">
		<a href="mailto:hello@melodica.com" class="footer__email flip-animate"
			><span data-hover="hello@melodica.com">hello@melodica.com</span></a
		>
		<div class="footer__social">
			<a href="#" class="footer__social-item flip-animate"
				><span data-hover="facebook">facebook</span></a
			>
			<a href="#" class="footer__social-item flip-animate"
				><span data-hover="twitter">twitter</span></a
			>
			<a href="#" class="footer__social-item flip-animate"
				><span data-hover="instagram">instagram</span></a
			>
			<a href="#" class="footer__social-item flip-animate"
				><span data-hover="youtube">youtube</span></a
			>
			<a href="#" class="footer__social-item flip-animate"
				><span data-hover="spotify">spotify</span></a
			>
		</div>
		<div class="header__logo">
			<img src="../assets/images/logo.png" alt="logo" />
		</div>
		<p class="footer__copyright">© 2024 Melodica Band / Design by Tavonline</p>
	</footer>
</template>

<style scoped>
footer {
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	text-align: center;
	padding: 20px;
	color: #fff;
}

.footer__email {
	font-weight: 600;
	font-size: 30px;
	line-height: 90.02%;
	margin: 20px 0px;
}

.footer__social {
	margin: 20px 0px;
}

.footer__social-item {
	font-size: 15px;
	font-weight: 400;
	margin: 0 22px;
}

.header__logo {
	margin: 30px 0px;
}

.footer__copyright {
	opacity: 0.6;
	letter-spacing: 1px;
	font-weight: 400;
}

a {
	color: #fff;
	text-decoration: none;
	transition: color 0.3s;
	outline: none;
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
	color: #9f5afd;
	transform: rotateX(90deg) translateY(-22px);
}
</style>
