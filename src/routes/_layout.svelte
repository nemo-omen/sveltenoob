<script>
	import Nav from '../components/Nav.svelte';

	export let segment;
</script>



<Nav {segment}/>

<main>
	<slot></slot>
</main>

<style>
	main {
		position: relative;
		background-color: #202020;
		padding: 2em;
		margin: 0 auto;
		box-sizing: border-box;
	}
</style>