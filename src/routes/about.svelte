<svelte:head>
	<title>About</title>
</svelte:head>
<div class="about-content">
	<div class="about-info">
		<h1>About SvelteNoob</h1>

		<p>SvelteNoob is a blog written by Jeff Caldwell. Jeff is pretty new to Svelte and JavaScript, so it takes him longer than most to get things done. When he does get them done, though, he writes about the process so other noobs can learn from his mistakes and successes.</p>

		<p>Jeff works for a local television news station and uses Svelte to build tools for their streaming operation and their website.</p>

		<!-- <p>Jeff promises not to call his time learning JavaScript and Svelte a 'journey.'</p> -->

	</div>

	<div class="about-profile">
			<div class="profile-image">
				<img src="images/derg.jpg" alt="Jeff Caldwell, SvelteNoob">
			</div>
			<ul>
				<li><a href="https://dev.to/trainingmontage"><i class="fab fa-dev"></i> @trainingmontage</a></li>
				<li><a href="https://github.com/nemo-omen"><i class="fab fa-github"></i> nemo-omen</a></li>
			</ul>
	</div>
</div>

<style>


@media (min-width: 800px) {
	.about-content {
		display: grid;
		justify-content: space-between;
		justify-self: center;
		grid-template-columns: repeat(2, 1fr);
		grid-gap: 6rem;
		max-width: 80%;
	}
	.about-info {
		justify-self: start;
		display: grid;
		justify-content: center;
	}
	.about-profile {
		justify-self: end;
		display: grid;
		justify-content: center;
	}
	}
	@media (max-width: 800px) {
		.about-content {
			width: 100%;
		}
		.about-info, .about-profile {
			justify-content: center;
			justify-self: center;
			margin-bottom: 3rem;
		}
	}
	.profile-image {
		overflow: hidden;
		width: 300px;
		height: 300px;
		display: grid;
		border-radius: 300px;
		justify-content: center;
		align-content: top;
		margin-bottom: 2rem;
		justify-self: center;
	}
	.profile-image img {
		width: 100%;
	}
	h1 {
		display: inline-block;
		border-bottom: 1px solid #ff3e00;
		margin: 0 0 1rem 0;
		padding-top: 0;
		padding-bottom: 0.25rem;
	}
	h3 {
		display: inline-block;
		margin: 0 0 1rem 0;
		font-size: 1.5rem;
		border-bottom: 1px solid #ff3e00;
		padding-bottom: 0.5rem;
	}
	ul {
		padding: 0;
		margin: 0;
	}
	ul li {
		list-style-type: none;
		font-size: 1.5rem;
		padding: 0.5rem;
	}
a {
	color: inherit;
	padding: 0;
	text-decoration: none;
	border-bottom: 1px solid rgba(0, 0, 0, 0.0);
	transition-property: border;
	transition-duration: 300ms;
}
	a:hover {
	border-bottom: 1px solid #ff3e00;
}
</style>