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
		background-color: #202020;
		padding: 0 2rem;
		margin: 0;
		display: grid;
		align-content: start;
		justify-content: stretch;
	}
</style>