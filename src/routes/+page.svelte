<script lang="ts">
	import * as Card from '$lib/components/ui/card';

	import BarChart from '$lib/components/data/bar-chart.svelte';
	import DumbellPlot from '$lib/components/data/dumbell-plot.svelte';
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Main dashboard" />
</svelte:head>

<div class="m-8 grid gap-4 md:grid-cols-2 lg:grid-cols-4">
	<Card.Root class="col-span-3">
		<Card.Header>
			<Card.Title>Main Viz</Card.Title>
			<Card.Description>Desc</Card.Description>
		</Card.Header>
		<Card.Content><BarChart /></Card.Content>
		<Card.Footer>Foot</Card.Footer>
	</Card.Root>
	<Card.Root class="col-span-1">
		<Card.Header>
			<Card.Title>Main Viz</Card.Title>
			<Card.Description>Desc</Card.Description>
		</Card.Header>
		<Card.Content>Test</Card.Content>
		<Card.Footer>Foot</Card.Footer>
	</Card.Root>
	<Card.Root class="col-span-3">
		<Card.Header>
			<Card.Title>Main Viz</Card.Title>
			<Card.Description>Desc</Card.Description>
		</Card.Header>
		<Card.Content><DumbellPlot /></Card.Content>
		<Card.Footer>Foot</Card.Footer>
	</Card.Root>
</div>
