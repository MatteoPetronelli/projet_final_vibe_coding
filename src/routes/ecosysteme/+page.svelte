<script>
	import BudgetChart from '$lib/components/BudgetChart.svelte';
	import { 
		Map, Building, Home, Sun, Leaf, Car, 
		Landmark, Users, Trophy, HardHat, ArrowDown, Info, ChevronRight 
	} from 'lucide-svelte';

	const instances = [
		{ 
			id: 'cio', name: 'CIO', role: 'Comité International Olympique', 
			desc: 'Définit les règles globales, choisit la ville hôte et conserve les droits exclusifs sur l\'événement planétaire.', 
			icon: Landmark, color: 'text-primary', bg: 'bg-blue-50' 
		},
		{ 
			id: 'cnosf', name: 'CNOSF', role: 'Comité National Olympique et Sportif Français', 
			desc: 'Sélectionne, prépare et mène la délégation sportive française vers les podiums.', 
			icon: Users, color: 'text-secondary', bg: 'bg-red-50' 
		},
		{ 
			id: 'cojo', name: 'COJO Paris 2024', role: 'Comité d\'Organisation (Tony Estanguet)', 
			desc: 'Planifie, organise et finance le déroulement des Jeux, avec un accent fort sur l\'expérience et le spectacle.', 
			icon: Trophy, color: 'text-gold', bg: 'bg-yellow-50' 
		},
		{ 
			id: 'solideo', name: 'SOLIDEO', role: 'Société de Livraison des Ouvrages', 
			desc: 'Livre les infrastructures pérennes (villages, centre aquatique) qui resteront en héritage pour les territoires.', 
			icon: HardHat, color: 'text-accent', bg: 'bg-green-50' 
		}
	];

	let activeInstance = $state(instances[0]);
</script>

<svelte:head>
	<title>Écosystème - JO Paris 2024</title>
</svelte:head>

<div class="container mx-auto px-4 py-12 max-w-7xl">
	
	<header class="mb-12 border-b-2 border-gray-100 pb-6">
		<h1 class="text-4xl md:text-5xl font-bold text-primary mb-4 tracking-tight">Rapport d'Écosystème</h1>
		<p class="text-lg text-gray-600 font-sans max-w-3xl">
			Analyse structurelle de l'organisation, du financement et de l'impact territorial des Jeux Olympiques de Paris 2024.
		</p>
	</header>

	<div class="grid grid-cols-1 lg:grid-cols-2 gap-10">

		<section class="bg-white rounded-2xl shadow-sm border border-gray-200 p-6 flex flex-col h-full">
			<h2 class="text-2xl font-bold text-primary mb-6 flex items-center gap-2">
				<Landmark class="text-gold" /> Gouvernance et Acteurs
			</h2>
			
			<div class="flex-grow grid grid-cols-1 md:grid-cols-2 gap-6 relative">
				<div class="flex flex-col gap-2 relative">
					{#each instances as inst, index}
						{#if index > 0}
							<div class="flex justify-center my-1 text-gray-300">
								<ArrowDown size={20} />
							</div>
						{/if}
						
						<!-- svelte-ignore a11y_click_events_have_key_events -->
						<!-- svelte-ignore a11y_no_static_element_interactions -->
						<div 
							class="p-4 rounded-xl border transition-all duration-300 cursor-pointer flex items-center justify-between group
							{activeInstance?.id === inst.id ? 'border-primary shadow-md bg-gray-50' : 'border-gray-100 hover:border-gray-300 hover:shadow-sm'}"
							onclick={() => activeInstance = inst}
						>
							<div class="flex items-center gap-3">
								<div class="{inst.bg} {inst.color} p-2 rounded-lg">
									<inst.icon size={24} />
								</div>
								<div>
									<h3 class="font-bold text-gray-800">{inst.name}</h3>
								</div>
							</div>
							<ChevronRight size={18} class="text-gray-400 group-hover:text-primary transition-colors" />
						</div>
					{/each}
				</div>

				<div class="bg-gray-50 rounded-xl p-6 border border-gray-100 h-full flex flex-col justify-center transition-all">
					{#if activeInstance}
						<div class="animate-in fade-in slide-in-from-right-4 duration-300">
							<div class="{activeInstance.color} mb-4">
								<Info size={40} />
							</div>
							<h3 class="text-xl font-bold text-primary mb-2">{activeInstance.name}</h3>
							<h4 class="text-sm font-semibold text-gray-500 mb-4 uppercase tracking-wide">{activeInstance.role}</h4>
							<p class="text-gray-700 font-sans leading-relaxed">
								{activeInstance.desc}
							</p>
						</div>
					{:else}
						<div class="text-center text-gray-400 flex flex-col items-center">
							<Info size={48} class="mb-4 opacity-50" />
							<p>Cliquez sur une instance pour afficher son rôle détaillé.</p>
						</div>
					{/if}
				</div>
			</div>
		</section>

		<section class="bg-white rounded-2xl shadow-sm border border-gray-200 p-6 flex flex-col h-full">
			<h2 class="text-2xl font-bold text-primary mb-6 flex items-center gap-2">
				<Landmark class="text-secondary" /> Budget et Financement
			</h2>
			<div class="flex-grow flex flex-col">
				<div class="grid grid-cols-2 gap-4 mb-6">
					<div class="bg-blue-50 p-4 rounded-xl border border-blue-100">
						<p class="text-xs font-bold text-primary uppercase mb-1">Budget COJO</p>
						<p class="text-2xl font-bold text-primary">3,8 Md€</p>
						<p class="text-sm text-gray-600 mt-1"><span class="font-bold text-green-600">97%</span> Privé</p>
					</div>
					<div class="bg-green-50 p-4 rounded-xl border border-green-100">
						<p class="text-xs font-bold text-accent uppercase mb-1">Budget SOLIDEO</p>
						<p class="text-2xl font-bold text-accent">3,0 Md€</p>
						<p class="text-sm text-gray-600 mt-1">50% Public / 50% Privé</p>
					</div>
				</div>
				<div class="flex-grow bg-white border border-gray-100 rounded-xl p-2 min-h-[300px]">
					<BudgetChart />
				</div>
			</div>
		</section>

		<section class="bg-white rounded-2xl shadow-sm border border-gray-200 p-6 flex flex-col h-full lg:col-span-2 xl:col-span-1">
			<h2 class="text-2xl font-bold text-primary mb-6 flex items-center gap-2">
				<Map class="text-gold" /> Sites et Territoire
			</h2>
			
			<div class="mb-6 bg-gray-50 p-4 rounded-xl border-l-4 border-gold">
				<p class="font-sans text-gray-700">
					Un modèle de sobriété avec <span class="font-bold text-primary">95 %</span> des infrastructures qui existent déjà ou seront temporaires.
				</p>
			</div>

			<div class="grid grid-cols-1 md:grid-cols-3 gap-4 flex-grow">
				<div class="group bg-white border border-gray-200 rounded-xl p-5 hover:-translate-y-1 hover:shadow-lg hover:border-gold transition-all duration-300">
					<Building class="text-primary mb-3 group-hover:scale-110 transition-transform" size={32} />
					<h3 class="font-bold text-primary mb-2">Sites Clés</h3>
					<p class="text-sm text-gray-600">Stade de France, Arena Bercy, Grand Palais, Centre Aquatique de St-Denis.</p>
				</div>
				<div class="group bg-white border border-gray-200 rounded-xl p-5 hover:-translate-y-1 hover:shadow-lg hover:border-secondary transition-all duration-300">
					<Home class="text-secondary mb-3 group-hover:scale-110 transition-transform" size={32} />
					<h3 class="font-bold text-secondary mb-2">Logements</h3>
					<p class="text-sm text-gray-600">Reconversion du Village Olympique en 6 000 logements pour les habitants de Seine-Saint-Denis.</p>
				</div>
				<div class="group bg-white border border-gray-200 rounded-xl p-5 hover:-translate-y-1 hover:shadow-lg hover:border-accent transition-all duration-300">
					<Building class="text-accent mb-3 group-hover:scale-110 transition-transform" size={32} />
					<h3 class="font-bold text-accent mb-2">Bureaux</h3>
					<p class="text-sm text-gray-600">Création de 6 000 bureaux et nouveaux quartiers d'activités économiques durables.</p>
				</div>
			</div>
		</section>

		<section class="bg-white rounded-2xl shadow-sm border border-gray-200 p-6 flex flex-col h-full lg:col-span-2 xl:col-span-1">
			<h2 class="text-2xl font-bold text-primary mb-6 flex items-center gap-2">
				<Leaf class="text-accent" /> Héritage Durable
			</h2>
			
			<div class="flex-grow flex flex-col justify-center">
				<div class="text-center mb-8">
					<div class="inline-flex items-center justify-center w-24 h-24 rounded-full bg-green-100 text-accent font-bold text-2xl border-4 border-white shadow-md mb-4 z-10 relative">
						-50%
					</div>
					<h3 class="text-xl font-bold text-gray-800">d'émissions de CO2</h3>
					<p class="text-gray-500 text-sm mt-1">Objectif principal par rapport aux éditions précédentes</p>
				</div>

				<div class="flex flex-wrap gap-4 justify-center">
					<div class="flex items-center gap-3 bg-gray-50 border border-gray-200 px-4 py-3 rounded-full hover:bg-yellow-50 hover:border-gold transition-colors cursor-default">
						<Sun class="text-gold" size={24} />
						<span class="font-semibold text-gray-700 text-sm">Parc photovoltaïque 3D</span>
					</div>
					<div class="flex items-center gap-3 bg-gray-50 border border-gray-200 px-4 py-3 rounded-full hover:bg-blue-50 hover:border-primary transition-colors cursor-default">
						<Car class="text-primary" size={24} />
						<span class="font-semibold text-gray-700 text-sm">500 véhicules hydrogène</span>
					</div>
					<div class="flex items-center gap-3 bg-gray-50 border border-gray-200 px-4 py-3 rounded-full hover:bg-green-50 hover:border-accent transition-colors cursor-default">
						<Trophy class="text-accent" size={24} />
						<span class="font-semibold text-gray-700 text-sm">Label Terre de Jeux 2024</span>
					</div>
				</div>
			</div>
		</section>

	</div>
</div>
