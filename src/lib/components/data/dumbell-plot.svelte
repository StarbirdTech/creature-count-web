<script>
	// @ts-nocheck

	import { onMount } from 'svelte';
	import * as d3 from 'd3';
	import { browser } from '$app/environment';

	let containerWidth, containerHeight;

	const data = [
		{ bird: 'Greater Prairie Chicken', value1966: -4.5, value2015: 2.5 },
		{ bird: 'Chicken', value1966: -4.5, value2015: 2.5 },
		{ bird: 'Greater Prairie Chicken', value1966: -4.5, value2015: 2.5 },
		{ bird: "Henslow's Sparrow", value1966: -2, value2015: 3 }
		// ... other birds
	];

	// Function to draw the chart
	function drawChart(width, height) {
		const margin = { top: 20, right: 20, bottom: 70, left: 100 };
		const effectiveWidth = width - margin.left - margin.right;
		const effectiveHeight = height - margin.top - margin.bottom;

		d3.select('#chart').selectAll('*').remove(); // Clear the previous chart

		const svg = d3
			.select('#chart')
			.append('svg')
			.attr('width', effectiveWidth + margin.left + margin.right)
			.attr('height', effectiveHeight + margin.top + margin.bottom)
			.append('g')
			.attr('transform', `translate(${margin.left},${margin.top})`);

		const x = d3.scaleLinear().range([0, effectiveWidth]);
		const y = d3.scaleBand().range([effectiveHeight, 0]).padding(0.1);

		x.domain(d3.extent(data, (d) => Math.max(d.value1966, d.value2015)));
		y.domain(data.map((d) => d.bird));

		// Draw the grid lines
		svg
			.append('g')
			.attr('class', 'grid')
			.attr('transform', `translate(0,${effectiveHeight})`)
			.call(d3.axisBottom(x).tickSize(-effectiveHeight).tickFormat(''));

		// Draw the y-axis
		svg.append('g').call(d3.axisLeft(y));

		// Draw lines between the two data points
		data.forEach((d) => {
			svg
				.append('line')
				.attr('x1', x(d.value1966))
				.attr('x2', x(d.value2015))
				.attr('y1', y(d.bird))
				.attr('y2', y(d.bird))
				.attr('stroke', 'grey')
				.attr('stroke-width', '1px');
		});

		// Draw dots for the two time periods
		svg
			.selectAll('.dot1966')
			.data(data)
			.enter()
			.append('circle')
			.attr('class', 'dot1966')
			.attr('r', 5)
			.attr('cx', (d) => x(d.value1966))
			.attr('cy', (d) => y(d.bird))
			.attr('fill', 'black');

		svg
			.selectAll('.dot2015')
			.data(data)
			.enter()
			.append('circle')
			.attr('class', 'dot2015')
			.attr('r', 5)
			.attr('cx', (d) => x(d.value2015))
			.attr('cy', (d) => y(d.bird))
			.attr('fill', 'red');
	}

	onMount(() => {
		if (browser) {
			const chartContainer = document.getElementById('chart');
			containerWidth = chartContainer.clientWidth;
			containerHeight = chartContainer.clientHeight;

			// Draw initial chart
			drawChart(containerWidth, containerHeight);

			// Redraw chart on window resize
			window.addEventListener('resize', () => {
				containerWidth = chartContainer.clientWidth;
				containerHeight = chartContainer.clientHeight;
				drawChart(containerWidth, containerHeight);
			});
		}
	});
</script>

<div class="h-72" id="chart"></div>
