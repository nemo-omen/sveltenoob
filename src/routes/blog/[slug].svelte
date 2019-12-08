<script context="module">
//You can find instructions at spiffy.tech/blog/setting-up-sapper-with-netlify-cms/

  export async function preload({ params, query }) {
    // the `slug` parameter is available because
    // this file is called [slug].svelte
    const res = await this.fetch(`_posts/${params.slug}.md`);

    if (res.status === 200) {
      return { postMd: await res.text() };
    } else {
      this.error(res.status, data.message);
    }
  }
</script>

<script>
  import fm from 'front-matter';
	import marked from 'marked';
	import Prism from 'prismjs'


	export let postMd;


	marked.setOptions({
		gfm: true,
		smartypants: true,
		headerIds: true,
		highlight: function(code, lang) {
			return Prism.highlight(code, Prism.languages[lang], lang);
		}
	});


	// const md = new MarkdownIt();

  $: frontMatter = fm(postMd);
  $: post = {
    ...frontMatter.attributes,
    html: marked(frontMatter.body)
  };
</script>



<svelte:head>
	<title>{post.title}</title>
</svelte:head>
<div class="blog-main">
	<div class="blog-header" style="background-image: url({post.thumbnail})">
		<h1>{post.title}</h1>
	</div>


	<div class='content'>
		<p class="post-date">{post.date}</p>
		{@html post.html}
	</div>
</div>

<style>
.blog-main {

	align-content: start;
}
.blog-header {

	display: grid;
	align-content: end;
	justify-content: stretch;
	text-align: start;
	margin: 0;
	height: 30vh;
	background-position: center;
	background-size: cover;
	background-repeat: no-repeat;

}
.blog-header h1 {
	font-size: 2rem;
	margin: 0;
	background-color: rgba(0, 0, 0, 0.3);
	padding: 1rem;
}
@media (min-width:800px) {
	.content {
		width: 80%;
		padding: 1rem;
	}
}
@media (max-width: 800px) {
	.blog-header {
		height: 20vh;
	}
	.content {
		width: 100%;
		padding: 0;
	}
}
@media (max-width: 500px) {
	.blog-header {
		height: 15vh;
	}
	.blog-header h1 {
		font-size: 1.5rem;
	}
}
.post-date {
	font-style: italic;
	color: #f8f8f8;
	border-bottom: 1px dotted #f8f8f8;
	padding: 0 0 1rem 0;
}
	/*
		By default, CSS is locally scoped to the component,
		and any unused styles are dead-code-eliminated.
		In this page, Svelte can't know which elements are
		going to appear inside the {{{post.html}}} block,
		so we have to use the :global(...) modifier to target
		all elements inside .content
	*/
	.content :global(code){
	font-family: 'IMB Plex Mono', menlo, inconsolata, monospace;
	white-space: pre-wrap;
	background-color: #2d2d2d;
	}
	.content :global(pre) {
		border-radius: 5px;
		padding: 1rem;
		white-space: pre-wrap;
		max-width: 80%;
		background-color: #2d2d2d;
	}
@media (max-width: 500px) {
	.content :global(code) {
		max-width: 100%;
	}
	.content :global(pre) {
		max-width: 100%;
	}
}
	</style>