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
		background-color: #282828;
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
	}
	.nav-logo {
		display: grid;
	}

.nav-logo img {
	height: 2.5rem;
	padding: 0;
	margin: 0;
}

	.selected {
		display: block;
		border-bottom: 1px solid #ff3e00;
	}

	a {
		text-decoration: none;
		display: block;
	}
</style>