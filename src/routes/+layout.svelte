<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';
	
	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

{@render children?.()}

<style>
@import url('https://fonts.googleapis.com/css2?family=M+PLUS+1:wght@300&display=swap');
	:global(body) {
		font-family: "M PLUS 1", sans-serif;
		font-optical-sizing: auto;
		font-weight: 300;
		font-style: normal;
	}
</style>