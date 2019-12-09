<script>
	import Nav from '../components/Nav.svelte';

	export let segment;
</script>



<Nav {segment}/>
<div class="container">
	<main>
		<slot></slot>
	</main>
</div>

<style>
	.container {
		width: 100%;
		display: grid;
		justify-content: center;
		margin: 7rem 0;
		padding: 0;
	}
	main {
		background-color: #282828;
		justify-self: center;
		display: grid;
		align-content: start;
		width: 60%;
		/* justify-content: stretch; */
	}
	@media (max-width: 800px) {
		main {
			width: 90%;
		}
	}
</style>