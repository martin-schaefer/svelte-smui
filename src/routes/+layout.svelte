<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';
	import TopAppBar, { Row, Section, Title } from '@smui/top-app-bar';
	import Tab, { Icon, Label } from '@smui/tab';
	import TabBar from '@smui/tab-bar';

	let tabs = [
		{
			icon: 'access_time',
			label: 'Recents',
		},
		{
			icon: 'near_me',
			label: 'Nearby',
		},
		{
			icon: 'favorite',
			label: 'Favorites',
		},
		{
			icon: 'github',
			label: 'Woof',
		},
	];
	let active = $state(tabs[0]);
	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>
<header>
		<TopAppBar style="background-color: #212121;">
			<Row>
				<Section>
					<Title>Bitzer</Title>
				</Section>
				<Section>
					<TabBar {tabs} key={(tab) => tab.label} bind:active>
						{#snippet tab(tab)}
							<Tab {tab}>
								<Icon class="material-icons">{tab.icon}</Icon>
								<Label>{tab.label}</Label>
							</Tab>
						{/snippet}
					</TabBar>
				</Section>
			</Row>
		</TopAppBar>
</header>
{@render children()}

