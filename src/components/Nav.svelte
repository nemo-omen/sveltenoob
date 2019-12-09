<script>
	export let segment;
</script>

<nav>
	<div class="nav-menu">
		<div class="nav-item">
			<a class:selected={segment === undefined} href=".">HOME</a>
		</div>
		<div class="nav-item">
			<div class="nav-logo">
				<a href='.'><img src="images/logo.svg" alt="SvelteNoob"></a>
			</div>
		</div>
		<div class="nav-item">
			<a class:selected={segment === 'about'} href="about">ABOUT</a>
		</div>
	</div>
</nav>

<style>
	nav {
		width: 100%;
		height: 5rem;
		font-weight: 300;
		display: grid;
		justify-content: center;
		align-content: center;
		position: fixed;
		left: 0;
		top: 0;
		z-index: 20;
		background-color: #2c2c2c;
	}
	.nav-menu {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		align-content: stretch;
	}

	.nav-item {
		margin: 0 2em;
		display: grid;
		align-content: center;
		justify-content: center;
		text-align: center;
	}
	.nav-logo {
		display: grid;
	}

.nav-logo img {
	height: 2.5rem;
	padding: 0;
	margin: 0;
	filter: drop-shadow(0px 0px 2px rgba(255, 255, 255, 0.0));
	transition-property: filter;
	transition-duration: 500ms;
}
.nav-logo img:hover {
	filter: drop-shadow(0px 0px 6px rgba(255, 255, 255, 0.514));
}

	.selected {
		display: block;
		border-bottom: 1px solid #ff3e00;
		/* border-bottom: 1px solid rgba(255, 118, 72, 0.514); */
	}

	a {
		text-decoration: none;
		display: block;
	}
</style>