<script lang="ts">
	import DataTable, { Head, Body, Row, Cell } from '@smui/data-table';
	import { onMount } from 'svelte';

	type Instance = {
		name: string;
		version: string;
		deploy: boolean;
	};
	let instances: Instance[] = $state([]);

	onMount(async () => instances = [
		{ name: 'agz-bff-mybff', version: '2.0.0', deploy: true },
		{ name: 'agz-bff-myapp', version: '1.0.1',  deploy: true },
		{ name: 'agz-svc-service', version: '1.3.0', deploy: false },
		{ name: 'agz-svc-appx', version: '1.3.0', deploy: true },
		{ name: 'agz-ui-board', version: '1.3.0', deploy: true },
		{ name: 'agz-ui-items', version: '1.3.0',  deploy: true },
		{ name: 'agz-svc-engine', version: '2.3.0', deploy: false },
		{ name: 'agz-ui-dashboardx', version: '1.3.0', deploy: true },
		{ name: 'agz-ui-it', version: '4.3.0',  deploy: true },
		{ name: 'agz-svc-motor', version: '2.3.0', deploy: false },
		{ name: 'agz-svc-server', version: '3.0.0',  deploy: true },
		{ name: 'agz-ui-dashboard', version: '1.3.0', deploy: true },
		{ name: 'agz-ui-welcome', version: '1.3.0',  deploy: true },
		{ name: 'agz-svc-bpmn', version: '2.3.0', deploy: false },
		{ name: 'agz-ui-itemlines', version: '1.3.0',  deploy: true },
		{ name: 'agz-svc-bpmnx', version: '2.3.0', deploy: false },
		{ name: 'agz-svc-srv', version: '3.0.0',  deploy: true },
		{ name: 'agz-svc-security', version: '1.3.0', deploy: true }
	]);

</script>

<DataTable stickyHeader table$aria-label="Package content list" style="width: 100%;">
	<Head>
		<Row>
			<Cell>Instance</Cell>
			<Cell align="right" >Version</Cell>
			<Cell>Chart</Cell>
			<Cell>Deploy/Delete</Cell>
		</Row>
	</Head>
	<Body>
	{#each instances as instance (instance.name)}
		<Row>
			<Cell>{instance.name}</Cell>
			<Cell>{instance.version}</Cell>
			<Cell>agz-stable/{instance.name}</Cell>
			<Cell>{instance.deploy}</Cell>
		</Row>
	{/each}
	</Body>
</DataTable>

