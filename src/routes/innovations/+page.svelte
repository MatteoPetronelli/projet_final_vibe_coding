<svelte:head>
	<title>Innovations - JO Paris 2024</title>
</svelte:head>

<div class="container mx-auto px-4 py-12">
	<div class="mb-10 text-center md:text-left">
		<h1 class="text-3xl md:text-5xl font-bold text-primary mb-4">Rapport Innovations</h1>
		<p class="text-lg text-gray-600 font-sans max-w-3xl">
			Découvrez les avancées technologiques, écologiques et sociales introduites lors de ces Jeux Olympiques.
		</p>
	</div>

	<!-- TODO: Intégration future d'un système de filtrage et d'affichage par cartes -->
	<div class="mb-8 flex flex-wrap gap-4 justify-center md:justify-start">
		<button class="px-6 py-2 rounded-full bg-primary text-white font-semibold hover:bg-opacity-90 transition-colors shadow-sm">Toutes</button>
		<button class="px-6 py-2 rounded-full bg-gray-200 text-gray-700 font-medium hover:bg-gray-300 transition-colors">Écologie</button>
		<button class="px-6 py-2 rounded-full bg-gray-200 text-gray-700 font-medium hover:bg-gray-300 transition-colors">Technologie</button>
		<button class="px-6 py-2 rounded-full bg-gray-200 text-gray-700 font-medium hover:bg-gray-300 transition-colors">Social</button>
	</div>

	<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
		<!-- Placeholder de carte innovation -->
		<div class="bg-white rounded-xl shadow-lg border border-gray-100 overflow-hidden hover:shadow-xl transition-shadow cursor-pointer">
			<div class="h-48 bg-gray-200 flex items-center justify-center text-gray-400 font-medium border-b border-gray-100">
				Image ou Illustration
			</div>
			<div class="p-6">
				<span class="text-xs font-bold uppercase tracking-wider text-accent mb-2 block">Écologie</span>
				<h3 class="text-xl font-bold text-primary mb-3">Village Olympique Bas Carbone</h3>
				<p class="text-gray-600 font-sans text-sm mb-4">
					Construit avec des matériaux biosourcés, fonctionnant aux énergies renouvelables et conçu pour laisser un héritage utile au territoire.
				</p>
				<button class="text-primary font-semibold text-sm hover:text-secondary transition-colors inline-flex items-center gap-1">
					En savoir plus
					<span>→</span>
				</button>
			</div>
		</div>

		<!-- D'autres cartes viendront ici -->
		<div class="bg-white rounded-xl shadow-lg border border-gray-100 overflow-hidden hover:shadow-xl transition-shadow cursor-pointer opacity-70">
			<div class="h-48 bg-gray-200 flex items-center justify-center text-gray-400 font-medium border-b border-gray-100">
				Image ou Illustration
			</div>
			<div class="p-6">
				<span class="text-xs font-bold uppercase tracking-wider text-secondary mb-2 block">Technologie</span>
				<h3 class="text-xl font-bold text-primary mb-3">Innovation Future</h3>
				<p class="text-gray-600 font-sans text-sm mb-4">
					Description de l'innovation à venir.
				</p>
			</div>
		</div>
	</div>
</div>
