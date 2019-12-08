<script context="module">
//You can find instructions at spiffy.tech/blog/setting-up-sapper-with-netlify-cms/

	export function preload({ params, query }) {
		return this.fetch(`blog.json`).then(r => r.json()).then(posts => {
			return { posts };
		});
	}
</script>

<script>
	export let posts;

	console.log(posts);
</script>

<!-- Markup -->
<svelte:head>
	<title>SvelteNoob - Blog</title>
</svelte:head>


<div class="blog-grid">
	{#each posts as post}
		<!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
		<div class="blog-preview" style="background-image: url({post.thumbnail})">
		<a class="div-link" href="blog/{post.slug}">
		</a>
			<!-- <div class="img-preview">
				<a rel='prefetch' href='blog/{post.slug}'><img src="{post.thumbnail}" alt="{post.slug}"></a>
			</div> -->
			<div class="blog-preview-content">
				<article>
					<a rel='prefetch' href='blog/{post.slug}'><h3>{post.title}</h3></a>
				</article>
				<footer>
					<p>{post.description}</p>
				</footer>
			</div>
		</div>
	{/each}
</div>

<style>
	.blog-grid {
		display: grid;
		width: 100%;
		grid-template-columns: repeat(2, minmax(300px, 1fr));
		grid-gap: 2rem;
		justify-content: stretch;
	}
	.blog-preview {
		display: grid;
		justify-content: stretch;
		align-content: end;
		/* border-radius: 5px; */
		box-shadow: 0px 0px 5px rgba(255, 255, 255, 0.2);
		padding: 0;
		overflow: hidden;
		background-repeat: no-repeat;
		background-position: center;
		background-size: cover;
		height: 20rem;
		border-radius: 5px;
	}
	.blog-preview-content {
		background-color: rgba(0, 0, 0, 0.3);
	}
	.div-link {
		position: absolute;
		left: 0;
		top: 0;
		width: 100%;
		height: 100%;
		text-decoration: none;
		z-index: 20;
		opacity: 0;
	}

	.blog-preview article {
		display: grid;
		margin: 1rem 0 0 0;
		padding: 0 1rem;
		width: 100%;
	}
	.blog-preview article h3 {
		font-size: 2rem;
		font-weight: bold;
		margin: 0;
	}
	.blog-preview article a {
		text-decoration: none;
	}

	.blog-preview footer {
		font-style: italic;
		padding: 0 1rem;
		font-size: 1.25rem;
	}
	.img-preview {
		display: grid;
		align-content: center;
		justify-content: center;
		height: 10rem;
		overflow: hidden;
		margin: 0;
		padding: 0;
	}
	.img-preview img {
		width: 100%;
	}
</style>