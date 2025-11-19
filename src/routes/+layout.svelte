<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';
	import TopAppBar, { Row, Section, Title } from '@smui/top-app-bar';
	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>
<header>
	<Row>
		<TopAppBar>
			<Section>
				<Title>Bitzer</Title>
			</Section>
		</TopAppBar>
	</Row>
</header>
{@render children()}
