<script>
	import { onMount } from 'svelte';
	import * as echarts from 'echarts';

	let { radarData = [], domainName = '' } = $props();

	/** @type {HTMLElement} */
	let chartContainer;
	/** @type {echarts.ECharts} */
	let chartInstance;

	$effect(() => {
		const currentData = radarData;
		const currentName = domainName;
		if (chartInstance && currentData && currentData.length > 0) {
			updateChart(currentData, currentName);
		}
	});

	function updateChart(/** @type {number[]} */ data, /** @type {string} */ name) {
		const option = {
			tooltip: {
				trigger: 'item',
				formatter: (/** @type {any} */ params) => {
					const values = params.value;
					const indicators = ['Sécurité & Contrôle', 'Efficacité', 'Expérience Utilisateur', 'Durabilité', 'Risques & Éthique'];
					let str = `<div style="font-family: 'Open Sans', sans-serif; padding: 4px;">`;
					str += `<strong style="color: #002654; font-size: 14px; display:block; margin-bottom: 6px; border-bottom: 1px solid #e2e8f0; padding-bottom: 4px;">${name}</strong>`;
					indicators.forEach((ind, i) => {
						str += `<div style="display:flex; justify-content:space-between; margin-bottom:2px;">
                                    <span style="color: #718096; margin-right: 12px;">${ind}:</span> 
                                    <strong style="color: #002654;">${values[i]}/10</strong>
                                </div>`;
					});
					str += `</div>`;
					return str;
				}
			},
			radar: {
				indicator: [
					{ name: 'Sécurité & Contrôle', max: 10 },
					{ name: 'Efficacité Opérationnelle', max: 10 },
					{ name: 'Expérience Utilisateur', max: 10 },
					{ name: 'Durabilité & Écologie', max: 10 },
					{ name: 'Risques & Éthique', max: 10 }
				],
				splitNumber: 5,
				axisName: {
					color: '#002654',
					fontFamily: 'Montserrat',
					fontWeight: 'bold',
					fontSize: 11
				},
				splitArea: {
					areaStyle: {
						color: ['#ffffff', '#f8fafc', '#f1f5f9', '#e2e8f0', '#cbd5e1'],
						shadowColor: 'rgba(0, 0, 0, 0.05)',
						shadowBlur: 10
					}
				},
				axisLine: { lineStyle: { color: '#cbd5e1' } },
				splitLine: { lineStyle: { color: '#cbd5e1' } }
			},
			series: [
				{
					type: 'radar',
					data: [
						{
							value: data,
							name: name,
							itemStyle: { color: '#ED2939' },
							areaStyle: { color: 'rgba(237, 41, 57, 0.2)' },
							lineStyle: { width: 3, color: '#ED2939' }
						}
					],
					animationDuration: 1000,
					animationEasing: 'cubicOut'
				}
			]
		};
		chartInstance.setOption(option, true);
	}

	onMount(() => {
		chartInstance = echarts.init(chartContainer);
		updateChart(radarData, domainName);

		const resizeObserver = new ResizeObserver(() => {
			if (chartInstance) chartInstance.resize();
		});
		resizeObserver.observe(chartContainer);

		return () => {
			resizeObserver.disconnect();
			if (chartInstance) chartInstance.dispose();
		};
	});
</script>

<div bind:this={chartContainer} class="w-full h-full min-h-[400px]"></div>
