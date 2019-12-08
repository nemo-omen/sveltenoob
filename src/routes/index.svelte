<script context="module">
//You can find instructions at spiffy.tech/blog/setting-up-sapper-with-netlify-cms/

	export function preload({ params, query }) {
		return this.fetch(`blog.json`).then(r => r.json()).then(posts => {
			return { posts };
		});
	}
</script>

<script>
//You can find instructions at spiffy.tech/blog/setting-up-sapper-with-netlify-cms/

  import { onMount } from 'svelte';

  onMount(() => {
    if (window.netlifyIdentity) {
      window.netlifyIdentity.on("init", user => {
        if (!user) {
          window.netlifyIdentity.on("login", () => {
            document.location.href = "/admin/";
          });
        }
      });
    }
  });
		export let posts;

</script>

<svelte:head>
	<title>SvelteNoob - Blog</title>
	<script src="https://identity.netlify.com/v1/netlify-identity-widget.js"></script>
</svelte:head>


<div class="blog-grid">
	{#each posts as post}
		<!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
		<div class="blog-preview" style="background-image: url({post.thumbnail})">
			<div class="img-preview">
				<a rel='prefetch' href='blog/{post.slug}'><img src="{post.thumbnail}" alt="{post.slug}"></a>
			</div>
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
		grid-template-columns: repeat(2, 1fr);
		grid-gap: 2rem;
		justify-content: stretch;
	}
	.blog-preview {
		display: grid;
		justify-content: stretch;
		align-content: stretch;
		/* border-radius: 5px; */
		box-shadow: 0px 0px 5px rgba(255, 255, 255, 0.2);
		padding: 0;
		overflow: hidden;
		height: 20rem;
		border-radius: 5px;
		background-position: center top;
		background-size: cover;
		background-repeat: no-repeat;
	}
	.blog-preview-content {
		background-color: rgba(0, 0, 0, 0.3);
		z-index: 10;
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
		align-content: start;
		justify-content: stretch;
		width: 100%;
		/* z-index: 5; */
		overflow: hidden;
		margin: 0;
		padding: 0;
	}
	.img-preview img {
		width: 100%;
		margin: 0;
		padding: 0;
		opacity: 0;
	}
@media (max-width: 800px) {
	.blog-grid {
		grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
	}
}
@media (max-width: 350px) {
	.img-preview {
		opacity: 0;
	}
	.img-preview img {
		opacity: 0;
	}
}
</style>