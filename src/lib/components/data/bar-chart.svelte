<script>
	// @ts-nocheck

	import { onMount } from 'svelte';
	import * as d3 from 'd3';

	let data = [
		{ bird: 'Sparrow', count: 250 },
		{ bird: 'Robin', count: 150 },
		{ bird: 'Eagle', count: 50 }
		// Add more bird data here
	];

	let chartWidth, chartHeight;

	onMount(() => {
		const container = document.querySelector('#bar-chart');
		const boundingRect = container.getBoundingClientRect();

		chartWidth = boundingRect.width;
		chartHeight = boundingRect.height;

		const margin = { top: 20, right: 30, bottom: 40, left: 90 };
		const width = chartWidth - margin.left - margin.right;
		const height = chartHeight - margin.top - margin.bottom;

		const svg = d3
			.select(container)
			.append('svg')
			.attr('width', width + margin.left + margin.right)
			.attr('height', height + margin.top + margin.bottom)
			.append('g')
			.attr('transform', `translate(${margin.left},${margin.top})`);

		const x = d3
			.scaleLinear()
			.domain([0, d3.max(data, (d) => d.count)])
			.range([0, width]);

		svg.append('g').call(d3.axisBottom(x)).attr('transform', `translate(0,${height})`);

		const y = d3
			.scaleBand()
			.range([0, height])
			.domain(data.map((d) => d.bird))
			.padding(0.1);

		svg.append('g').call(d3.axisLeft(y));

		svg
			.selectAll('myRect')
			.data(data)
			.enter()
			.append('rect')
			.attr('x', x(0))
			.attr('y', (d) => y(d.bird))
			.attr('width', (d) => x(d.count))
			.attr('height', y.bandwidth())
			.attr('fill', '#69b3a2');
	});
</script>

<div class="h-72" id="bar-chart"></div>
