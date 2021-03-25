<script>
	import Header from './Header.svelte';
	import InteractiveList from './InteractiveList.svelte';
</script>

<main>
	<Header/>
	<InteractiveList/>
</main>

<style>
	main {
		text-align: center;
		padding: 3rem 0 0 0;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
