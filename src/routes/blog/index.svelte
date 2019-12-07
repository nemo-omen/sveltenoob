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
		<div class="blog-preview">
			<div class="img-preview">
				<a rel='prefetch' href='blog/{post.slug}'><img src="{post.thumbnail}" alt="{post.slug}"></a>
			</div>
			<article>
				<a rel='prefetch' href='blog/{post.slug}'><h3>{post.title}</h3></a>
			</article>
			<footer>
				<p>Here's some filler text for styling.</p>
			</footer>
		</div>
	{/each}
</div>

<style>
	.blog-grid {
		display: grid;
		width: 100%;
		grid-template-columns: repeat(2, 1fr);
		grid-gap: 2rem;
		justify-content: stretch;
	}
	.blog-preview {
		display: grid;
		border-radius: 5px;
		box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
		padding: 0;
		overflow: hidden;
	}

	.blog-preview article {
		margin: 1rem 0 0 0;
		padding: 0 1rem;
	}
	.blog-preview article h3 {
		font-size: 1.75rem;
	}
	.blog-preview article a {
		text-decoration: none;
	}
	.blog-preview article a:hover {
		text-decoration: underline;
	}
	.blog-preview footer {
		font-style: italic;
		padding: 0 1rem;
	}
	.img-preview {
		display: grid;
		align-content: center;
		height: 20rem;
		overflow: hidden;
		margin: 0;
		padding: 0;
		border-bottom: 3px solid #333;
	}
</style>