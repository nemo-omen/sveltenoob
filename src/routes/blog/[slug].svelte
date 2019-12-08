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
<header>
	<img src="{post.thumbnail}" alt="{post.title}">
</header>
<h1>{post.title}</h1>
<p>{post.date}</p>

<div class='content'>
	{@html post.html}
</div>

<style>
	/*
		By default, CSS is locally scoped to the component,
		and any unused styles are dead-code-eliminated.
		In this page, Svelte can't know which elements are
		going to appear inside the {{{post.html}}} block,
		so we have to use the :global(...) modifier to target
		all elements inside .content
	*/
	header {
		display: grid;
		align-content: center;
		width: 100%;
		height: 30em;
		overflow: hidden;
		margin: 0 0 1em 0;
	}
	header img {
		width: 100%;
	}
	.content :global(code){
	font-family: 'IMB Plex Mono', menlo, inconsolata, monospace;
	}
	.content :global(pre) {
		border-radius: 5px;
		margin: 0 1rem;
	}

	</style>