<svelte:head>
	<title>Performances - JO Paris 2024</title>
</svelte:head>

<div class="container mx-auto px-4 py-12">
	<div class="mb-10">
		<h1 class="text-3xl md:text-5xl font-bold text-primary mb-4">Dashboard Athlète</h1>
		<p class="text-lg text-gray-600 font-sans max-w-3xl">
			Consultez les statistiques, les records et les performances exceptionnelles des athlètes.
		</p>
	</div>

	<!-- TODO: Intégration future d'Echarts pour les graphiques de performances -->
	<div class="grid grid-cols-1 md:grid-cols-2 gap-8">
		<!-- Graphique 1 -->
		<div class="bg-white rounded-xl shadow-md border border-gray-100 p-6 h-[400px] flex items-center justify-center">
			<div class="text-center p-6 border-2 border-dashed border-secondary rounded-lg bg-red-50 w-full h-full flex flex-col justify-center">
				<h2 class="text-xl font-poppins font-semibold text-secondary mb-2">Graphique Echarts 1</h2>
				<p class="text-gray-500 font-sans text-sm">
					Intégration d'un graphique (ex: évolution des médailles).
				</p>
			</div>
		</div>
		
		<!-- Graphique 2 -->
		<div class="bg-white rounded-xl shadow-md border border-gray-100 p-6 h-[400px] flex items-center justify-center">
			<div class="text-center p-6 border-2 border-dashed border-primary rounded-lg bg-blue-50 w-full h-full flex flex-col justify-center">
				<h2 class="text-xl font-poppins font-semibold text-primary mb-2">Graphique Echarts 2</h2>
				<p class="text-gray-500 font-sans text-sm">
					Intégration d'un autre graphique (ex: répartition par pays).
				</p>
			</div>
		</div>
	</div>
</div>
