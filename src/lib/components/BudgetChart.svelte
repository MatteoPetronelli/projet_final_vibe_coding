<script>
	import { onMount } from 'svelte';
	import * as echarts from 'echarts';

	/** @type {HTMLElement} */
	let chartContainer;
	/** @type {echarts.ECharts} */
	let chartInstance;

	onMount(() => {
		// Initialiser l'instance Echarts
		chartInstance = echarts.init(chartContainer);

		const option = {
			tooltip: {
				trigger: 'item',
				formatter: '{a} <br/>{b}: {c} Mds € ({d}%)'
			},
			legend: {
				bottom: '0%',
				left: 'center',
				textStyle: {
					fontFamily: 'Open Sans'
				}
			},
			series: [
				{
					name: 'Acteur',
					type: 'pie',
					selectedMode: 'single',
					center: ['50%', '45%'],
					radius: [0, '40%'],
					label: {
						position: 'inner',
						fontSize: 12,
						color: '#fff',
						fontFamily: 'Montserrat',
						fontWeight: 'bold'
					},
					labelLine: {
						show: false
					},
					data: [
						{ value: 3.8, name: 'COJO', itemStyle: { color: '#002654' } }, // Bleu Paris 2024
						{ value: 3.0, name: 'SOLIDEO', itemStyle: { color: '#00A651' } } // Vert Paris 2024
					]
				},
				{
					name: 'Origine',
					type: 'pie',
					center: ['50%', '45%'],
					radius: ['50%', '70%'],
					label: {
						formatter: '{b|{b}}\n{c} Mds €',
						rich: {
							b: {
								color: '#4a5568',
								fontSize: 12,
								fontWeight: 'bold',
								fontFamily: 'Open Sans',
								lineHeight: 20
							}
						}
					},
					data: [
						{ value: 3.686, name: 'Privé (COJO)', itemStyle: { color: '#336699' } },
						{ value: 0.114, name: 'Public (COJO)', itemStyle: { color: '#ED2939' } }, // Rouge
						{ value: 1.5, name: 'Privé (SOLIDEO)', itemStyle: { color: '#33cc77' } },
						{ value: 1.5, name: 'Public (SOLIDEO)', itemStyle: { color: '#ED2939' } } // Rouge
					]
				}
			]
		};

		chartInstance.setOption(option);

		// Gestion du redimensionnement
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

<div class="w-full h-full min-h-[450px]" bind:this={chartContainer}></div>
