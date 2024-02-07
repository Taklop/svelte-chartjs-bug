<script lang="ts">
	import { Line } from 'svelte-chartjs';
	import type { Chart, ChartData } from 'chart.js';
	// import type { Line as LineType } from 'svelte-chartjs';

	import {
		Chart as ChartJS,
		Title,
		Tooltip,
		Legend,
		LineElement,
		LinearScale,
		PointElement,
		CategoryScale,
		Filler
	} from 'chart.js';

	// this registers the chart.js plugins
	ChartJS.register(
		Title,
		Tooltip,
		Legend,
		Filler,
		LineElement,
		LinearScale,
		PointElement,
		CategoryScale
	);

	// ~~This is required to type the line element~~
	// type LineChartElement = Pick<LineType, 'LineProps'>['LineProps']['chart'];
	// let chartElement: LineChartElement | undefined = undefined;

	let chartElement: Chart<'line'> | undefined = undefined;

	// ~~This is required to type the data element~~
	// type LineChartData = Pick<Line, "LineProps">["LineProps"]["data"];

	// export let data: LineChartData = {...etc}

	export let data: ChartData<'line'> = {
		labels: ['Mon 1', 'Tues 2', 'Wed 3', 'Thu 4', 'Fri 5', 'Sat 6', 'Sun 07'],
		datasets: [
			{
				label: 'Dataset 1',
				backgroundColor: '#C478FF',
				borderColor: '#C478FF',
				borderWidth: 1,
				data: [65, 59, 80, 81, 56, 55, 40]
			}
		]
	};
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<div>
	<!-- typing error for bind:chart={chartElement} -->
	<!-- error is: Type '(number | Point | null)[]' is not assignable to type '(number | Point)[]' -->

	<!-- typing error for {data} -->
	<!-- Type 'ChartData<"line", (number | Point | null)[], unknown>' is not assignable to type 'ChartData<"line", (number | Point)[], unknown>' -->
	<Line bind:chart={chartElement} {data} />
</div>
