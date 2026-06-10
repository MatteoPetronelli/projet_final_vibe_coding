<script>
	import { onMount } from 'svelte';
	import { gsap } from 'gsap';
	import { Trophy, Medal, Activity } from 'lucide-svelte';
	import AthleteChart from '$lib/components/AthleteChart.svelte';

	// Données de Teddy Riner (Saison 2024)
	const competitions = [
		{ name: 'Paris 2024 (JO)', type: 'Jeux Olympiques', medal: 'Or', points: 1100, desc: 'La consécration ultime à domicile. Une victoire historique qui marque sa domination absolue sur la catégorie reine des +100 kg devant son public.' },
		{ name: 'Paris Grand Slam', type: 'Grand Slam', medal: 'Or', points: 500, desc: 'Une victoire prestigieuse à l\'Accor Arena, lançant parfaitement son année olympique avec une démonstration de force et de technique.' },
		{ name: 'Antalya Grand Slam', type: 'Grand Slam', medal: 'Or', points: 500, desc: 'Confirmation de son excellente forme internationale en Turquie, écartant tous ses adversaires avec une maîtrise impressionnante.' },
		{ name: 'Dushanbe Grand Slam', type: 'Grand Slam', medal: 'Or', points: 500, desc: 'Nouveau succès majeur en Grand Slam, engrangeant de précieux points pour s\'assurer une place de tête de série aux Jeux.' },
		{ name: 'Marrakech Open', type: 'Open', medal: 'Or', points: 50, desc: 'Tournoi de préparation tactique au Maroc pour affûter ses sensations et régler les derniers détails de ses mouvements spéciaux.' },
		{ name: 'Madrid Open', type: 'Open', medal: 'Or', points: 50, desc: 'Ultime répétition victorieuse sur le sol européen avant la grande échéance olympique, montrant une condition physique optimale.' }
	];

	// États réactifs (Runes Svelte 5)
	let filter = $state('Toutes');
	/** @type {any} */
	let selectedComp = $state(null);

	// Filtrage réactif des données
	let filteredData = $derived(
		filter === 'Toutes' ? competitions : competitions.filter(c => c.type === filter)
	);

	// Fonction callback passée au composant Echarts
	function handleBarClick(/** @type {any} */ comp) {
		selectedComp = comp;
	}

	onMount(() => {
		// Animation GSAP des KPI à l'apparition de la page
		gsap.from('.kpi-card', {
			opacity: 0,
			y: 30,
			duration: 0.8,
			stagger: 0.15,
			ease: 'power3.out'
		});
	});
</script>

<svelte:head>
	<title>Performances - JO Paris 2024</title>
</svelte:head>

<div class="container mx-auto px-4 py-12 max-w-7xl">
	
	<!-- En-tête -->
	<header class="mb-10 border-b-2 border-gray-100 pb-6 flex flex-col md:flex-row md:justify-between md:items-end">
		<div>
			<h1 class="text-4xl md:text-5xl font-bold text-primary mb-2 tracking-tight">Dashboard Athlète</h1>
			<p class="text-xl text-gray-600 font-sans font-medium">
				Focus sur : <span class="text-secondary font-bold">Teddy Riner</span> (Saison 2024)
			</p>
		</div>
		<div class="mt-4 md:mt-0 flex gap-4 bg-gray-50 p-3 rounded-lg border border-gray-200">
			<!-- Légende couleurs -->
			<div class="flex items-center gap-2 text-sm font-bold text-gray-700">
				<span class="w-3 h-3 rounded-full bg-gold inline-block"></span> JO
			</div>
			<div class="flex items-center gap-2 text-sm font-bold text-gray-700">
				<span class="w-3 h-3 rounded-full bg-primary inline-block"></span> Grand Slam
			</div>
			<div class="flex items-center gap-2 text-sm font-bold text-gray-700">
				<span class="w-3 h-3 rounded-full bg-secondary inline-block"></span> Open
			</div>
		</div>
	</header>

	<!-- KPI Cards -->
	<div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-10">
		<!-- KPI 1 -->
		<div class="kpi-card bg-white rounded-2xl p-6 shadow-sm border border-gray-200 flex items-center gap-4 border-l-4 border-l-primary hover:shadow-md transition-shadow">
			<div class="bg-blue-50 p-3 rounded-xl text-primary">
				<Activity size={32} />
			</div>
			<div>
				<p class="text-sm font-bold text-gray-500 uppercase tracking-wide">Total Points WRL</p>
				<p class="text-3xl font-bold text-gray-900">2 700</p>
			</div>
		</div>

		<!-- KPI 2 -->
		<div class="kpi-card bg-white rounded-2xl p-6 shadow-sm border border-gray-200 flex items-center gap-4 border-l-4 border-l-gold hover:shadow-md transition-shadow">
			<div class="bg-yellow-50 p-3 rounded-xl text-gold">
				<Trophy size={32} />
			</div>
			<div>
				<p class="text-sm font-bold text-gray-500 uppercase tracking-wide">Ratio de Victoire</p>
				<p class="text-3xl font-bold text-gray-900">100% <span class="text-sm text-gray-400 font-normal">(6/6)</span></p>
			</div>
		</div>

		<!-- KPI 3 -->
		<div class="kpi-card bg-white rounded-2xl p-6 shadow-sm border border-gray-200 flex items-center gap-4 border-l-4 border-l-secondary hover:shadow-md transition-shadow">
			<div class="bg-red-50 p-3 rounded-xl text-secondary">
				<Medal size={32} />
			</div>
			<div>
				<p class="text-sm font-bold text-gray-500 uppercase tracking-wide">Catégorie</p>
				<p class="text-3xl font-bold text-gray-900">+100 kg</p>
			</div>
		</div>
	</div>

	<!-- Section Graphique et Filtres -->
	<section class="bg-white rounded-2xl shadow-sm border border-gray-200 p-6 mb-8">
		<div class="flex flex-col md:flex-row justify-between items-center mb-8 gap-4">
			<h2 class="text-2xl font-bold text-primary">Évolution des Points WRL</h2>
			
			<!-- Système de filtrage -->
			<div class="flex flex-wrap gap-2 bg-gray-50 p-1.5 rounded-xl border border-gray-200">
				{#each ['Toutes', 'Jeux Olympiques', 'Grand Slam', 'Open'] as f}
					<button 
						class="px-4 py-2 rounded-lg text-sm font-bold transition-all duration-200 {filter === f ? 'bg-white text-primary shadow-sm border border-gray-200' : 'text-gray-500 hover:text-gray-800 hover:bg-gray-100'}"
						onclick={() => { filter = f; selectedComp = null; }}
					>
						{f}
					</button>
				{/each}
			</div>
		</div>

		<!-- Conteneur du graphique Echarts -->
		<div class="w-full">
			<AthleteChart data={filteredData} onBarClick={handleBarClick} />
		</div>
	</section>

	<!-- Panneau de détails interactif (Modale inline) -->
	<div class="min-h-[150px]">
		{#if selectedComp}
			<div class="animate-in slide-in-from-bottom-4 fade-in duration-300 bg-gray-50 rounded-2xl p-6 md:p-8 border-2 border-primary shadow-md flex flex-col md:flex-row gap-6 items-center transition-all">
				<div class="bg-white p-4 rounded-full shadow-sm border border-gray-200 text-gold flex-shrink-0">
					<Trophy size={48} />
				</div>
				<div>
					<div class="flex flex-wrap items-center gap-3 mb-2">
						<h3 class="text-2xl font-bold text-primary">{selectedComp.name}</h3>
						<span class="bg-gold text-white text-xs font-bold px-3 py-1 rounded-full uppercase shadow-sm">{selectedComp.medal}</span>
						<span class="bg-gray-200 text-gray-700 text-xs font-bold px-3 py-1 rounded-full">{selectedComp.type}</span>
					</div>
					<p class="text-lg font-sans text-gray-700 leading-relaxed">
						{selectedComp.desc}
					</p>
					<p class="mt-3 text-sm font-bold text-accent">+ {selectedComp.value} Points gagnés au World Ranking List (WRL)</p>
				</div>
			</div>
		{:else}
			<div class="bg-gray-50 border border-dashed border-gray-300 rounded-2xl p-8 flex flex-col items-center justify-center text-center h-full">
				<p class="text-gray-500 font-sans font-medium text-lg">
					Cliquez sur l'une des barres du graphique pour afficher les détails et l'importance de cette victoire.
				</p>
			</div>
		{/if}
	</div>

</div>
