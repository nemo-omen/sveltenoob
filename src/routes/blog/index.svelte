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
</script>

<style>
	.blog-grid {
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		grid-gap: 1rem;
		justify-content: space-around;
	}
	.blog-preview {
		display: grid;
		border-radius: 5px;
		box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
	}
</style>

<svelte:head>
	<title>SvelteNoob - Blog</title>
</svelte:head>


<div class="blog-grid">
	{#each posts as post}
		<!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
		<div class="blog-preview"><a rel='prefetch' href='blog/{post.slug}'>{post.title}</a></div>
	{/each}
</div>