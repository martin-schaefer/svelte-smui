<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';
	import TopAppBar, { Row, Section, Title } from '@smui/top-app-bar';
	import Tab, { Icon, Label } from '@smui/tab';
	import TabBar from '@smui/tab-bar';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';

	let tabs = [
		{
			icon: 'hive',
			label: 'Cluster',
			href: '/'
		},
		{
			icon: 'folder',
			label: 'Browse Package',
			href: '/package/'
		},
		{
			icon: 'link',
			label: 'Browse URLs',
			href: '/url/'
		}
	];
	let active = $state(tabs[0]);
	let { children } = $props();
	onMount(() => { goto(active.href);})
</script>
<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>
<header>
		<TopAppBar variant="static" style="background-color: var(--mdc-theme-background)">
			<Row>
				<Section>
					<Title>Material UI</Title>
				</Section>
				<Section>
					<TabBar {tabs} key={(tab) => tab.label} bind:active>
						{#snippet tab(tab)}
							<Tab {tab} href={tab.href}>
								<Icon class="material-icons">{tab.icon}</Icon>
								<Label>{tab.label}</Label>
							</Tab>
						{/snippet}
					</TabBar>
				</Section>
			</Row>
		</TopAppBar>
</header>
<main>
	{@render children()}
</main>

