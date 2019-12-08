<script>
	export let segment;
</script>

<nav>
	<!-- <ul>
		<li><a class:selected='{segment === undefined}' href='.'>home</a></li>
		<li><a class:selected='{segment === "about"}' href='about'>about</a></li> -->

		<!-- for the blog link, we're using rel=prefetch so that Sapper prefetches
		     the blog data when we hover over the link or tap it on a touchscreen -->
		<!-- <li><a rel=prefetch class:selected='{segment === "blog"}' href='blog'>blog</a></li>
	</ul> -->

	<div class="nav-menu">
		<div class="nav-logo">
			<a href='.'><img src="images/logo.svg" alt="SvelteNoob"></a>
		</div>
		<div class="nav-item">
			<a class:selected={segment === undefined} href=".">HOME</a>
		</div>
		<div class="nav-item">
			<a class:selected={segment === 'about'} href="about">ABOUT</a>
		</div>
		<div class="nav-item">
			<a class:selected={segment === 'blog'} href="blog">BLOG</a>
		</div>
	</div>
</nav>

<style>
	nav {
		font-weight: 300;
		padding: 1rem 2rem;
		display: grid;
		justify-content: start;
		align-content: end;
	}
	.nav-logo {
		display: grid;
		justify-content: start;
		align-content: center;
		height: 60px;
		margin: 0 2rem 0 0;
	}

.nav-logo img {
	height: 60px;
}
	.nav-menu {
		display: grid;
		width: 100%;
		justify-content: space-between;
		grid-template-columns: repeat(4, 1fr);
	}


	.selected {
		position: relative;
		display: inline-block;
		color: #ff3e00;
	}

	a {
		text-decoration: none;
		padding: 1em 0.5em;
		display: block;
	}
</style>