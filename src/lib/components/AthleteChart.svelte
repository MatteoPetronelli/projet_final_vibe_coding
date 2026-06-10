<script>
	import { onMount } from 'svelte';
	import * as echarts from 'echarts';

	let { data = [], onBarClick } = $props();

	/** @type {HTMLElement} */
	let chartContainer;
	/** @type {echarts.ECharts} */
	let chartInstance;

	$effect(() => {
		const currentData = data;
		if (chartInstance && currentData) {
			updateChart(currentData);
		}
	});

	function updateChart(/** @type {any[]} */ chartData) {
		const option = {
			tooltip: {
				trigger: 'axis',
				axisPointer: { type: 'shadow' },
				formatter: (/** @type {any} */ params) => {
					const item = params[0].data;
					return `<div style="font-family: 'Open Sans', sans-serif; padding: 4px;">
						<strong style="color: #002654; font-size: 14px;">${item.name}</strong><br/>
						<span style="color: #718096;">Type:</span> ${item.type}<br/>
						<span style="color: #718096;">Résultat:</span> ${item.medal}<br/>
						<span style="color: #718096;">Points WRL:</span> <strong style="color: #00A651;">${item.value}</strong>
					</div>`;
				}
			},
			grid: {
				left: '2%',
				right: '4%',
				bottom: '10%',
				top: '15%',
				containLabel: true
			},
			xAxis: {
				type: 'category',
				data: chartData.map(d => d.name),
				axisLabel: {
					interval: 0,
					rotate: 25,
					fontFamily: 'Open Sans',
					color: '#4a5568',
					fontSize: 11
				},
				axisTick: { alignWithLabel: true }
			},
			yAxis: {
				type: 'value',
				name: 'Points WRL',
				nameTextStyle: { fontFamily: 'Montserrat', color: '#002654', fontWeight: 'bold', padding: [0, 0, 0, 20] },
				splitLine: { lineStyle: { type: 'dashed', color: '#e2e8f0' } }
			},
			series: [
				{
					type: 'bar',
					data: chartData.map(d => ({
						value: d.points,
						name: d.name,
						type: d.type,
						medal: d.medal,
						desc: d.desc,
						itemStyle: {

							color: d.type === 'Jeux Olympiques' ? '#FFD700' : (d.type === 'Grand Slam' ? '#002654' : '#ED2939'),
							borderRadius: [6, 6, 0, 0]
						}
					})),
					barWidth: '45%',
					label: {
						show: true,
						position: 'top',
						fontFamily: 'Open Sans',
						fontWeight: 'bold',
						color: '#002654'
					},
					animationDuration: 1000,
					animationEasing: 'cubicOut'
				}
			]
		};
		chartInstance.setOption(option, true);
	}

	onMount(() => {
		chartInstance = echarts.init(chartContainer);
		updateChart(data);

		chartInstance.on('click', (/** @type {any} */ params) => {
			if (onBarClick && params.data) {
				onBarClick(params.data);
			}
		});

		const resizeObserver = new ResizeObserver(() => {
			chartInstance.resize();
		});
		resizeObserver.observe(chartContainer);

		return () => {
			resizeObserver.disconnect();
			chartInstance.dispose();
		};
	});
</script>

<div class="w-full h-full min-h-[400px]" bind:this={chartContainer}></div>
