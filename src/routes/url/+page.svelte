<script lang="ts">
	import DataTable, { Body, Cell, Head, Row } from '@smui/data-table';
	import { onMount } from 'svelte';
	import Textfield from '@smui/textfield';
	import IconButton from '@smui/icon-button';

	type Ingress = {
		name: string;
		serviceUrls: string[];
	};
	let ingresses: Ingress[] = $state([]);
	let filter = $state('undefined');
	onMount(async () => ingresses = [
		{ name: 'agz-bff-mybff', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "] },
		{ name: 'agz-bff-myapp', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  },
		{ name: 'agz-svc-service', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  },
		{ name: 'agz-svc-appx', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]   },
		{ name: 'agz-ui-board', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  },
		{ name: 'agz-ui-items', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "] },
		{ name: 'agz-svc-bpmn', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  },
		{ name: 'agz-ui-dashboardx', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  },
		{ name: 'agz-ui-it', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  },
		{ name: 'agz-svc-motor', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  },
		{ name: 'agz-svc-server', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  },
		{ name: 'agz-svc-bbusiness', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  },
		{ name: 'agz-svc-demo', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  },
		{ name: 'agz-ui-dashboard', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  },
		{ name: 'agz-ui-welcome', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  },
		{ name: 'agz-svc-engine', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  },
		{ name: 'agz-ui-itemlines', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  },
		{ name: 'agz-svc-bpmnx', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  },
		{ name: 'agz-svc-srv', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  },
		{ name: 'agz-svc-security', serviceUrls: ["http://agz-bff-mybff", "rpc://agz-bff-mybff:26500 "]  }
	]);

</script>

<div class="columns margins">
	<div class="column">
		<Textfield bind:value={filter} label="Filter by name" />
		<IconButton class="material-icons" onclick={() => filter = ''}>delete</IconButton>
	</div>
</div>

<DataTable stickyHeader table$aria-label="URL list" style="width: 100%;">
	<Head>
		<Row>
			<Cell>Instance</Cell>
			<Cell>Service URLs</Cell>
			<Cell>Neutral URLs</Cell>
			<Cell>Ingress URLs</Cell>
		</Row>
	</Head>
	<Body>
	{#each ingresses as ingress (ingress.name)}
		{#if filter.length === 0 || ingress.name.toLowerCase().includes(filter.toLowerCase())}
		<Row>
			<Cell>{ingress.name}</Cell>
			<Cell>{#each ingress.serviceUrls as serviceURL (serviceURL)}{serviceURL}<br>{/each}</Cell>
			<Cell>{#each ingress.serviceUrls as serviceURL (serviceURL)}{serviceURL}.dev.xs1.cloud.azure<br>{/each}</Cell>
			<Cell>{#each ingress.serviceUrls as serviceURL (serviceURL)}{serviceURL}.ns-we0.act.cloud.azure<br>{/each}</Cell>
		</Row>
		{/if}
	{/each}
	</Body>
</DataTable>

