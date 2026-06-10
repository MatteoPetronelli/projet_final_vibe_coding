<script>
	import { Cpu, Smartphone, Video, Shield, Leaf, Scale, GraduationCap, Users } from 'lucide-svelte';
	import InnovationChart from '$lib/components/InnovationChart.svelte';

	const domains = [
		{
			id: 'sport',
			name: 'Sport et opérations',
			icon: Cpu,
			desc: "Utilisation de l'IA et du digital twin pour la planification des sites. Suivi de la performance par capteurs portables et IA pour optimiser les entraînements et la logistique de l'événement.",

			radarData: [6, 9, 7, 5, 4]
		},
		{
			id: 'spectateurs',
			name: 'Spectateurs et expérience',
			icon: Smartphone,
			desc: "Billetterie « intelligente » (NFC/RFID) pour une fluidité d'accès, et applications mobiles de Réalité Augmentée. Déploiement de Chatbots IA pour guider les flux et fournir des infos pratiques en temps réel.",
			radarData: [7, 8, 9, 6, 6]
		},
		{
			id: 'medias',
			name: 'Médias et retransmission',
			icon: Video,
			desc: "Diffusion 8K UHD étendue et génération automatisée de résumés par IA. Caméras spécifiques et algorithmes de vision par ordinateur pour le suivi 3D en direct des athlètes sur le terrain.",
			radarData: [5, 8, 9, 5, 3]
		},
		{
			id: 'securite',
			name: 'Sécurité et surveillance',
			icon: Shield,
			desc: "Déploiement controversé de caméras « smart » équipées d'IA pour détecter automatiquement des situations à risque (objets abandonnés, mouvements de foule suspects) et alerter les forces de l'ordre.",
			radarData: [10, 8, 4, 3, 9]
		},
		{
			id: 'durabilite',
			name: 'Durabilité et mobilité',
			icon: Leaf,
			desc: "Parc automobile 100% électrifié et hydrogène (dont 500 voitures Toyota Mirai). Capteurs IoT répartis sur les sites pour mesurer en continu la qualité de l'air et de l'eau (notamment dans la Seine).",
			radarData: [6, 7, 6, 9, 5]
		}
	];

	let activeDomainId = $state(domains[0].id);
	let activeDomain = $derived(domains.find(d => d.id === activeDomainId) || domains[0]);
	let ActiveIcon = $derived(activeDomain.icon);

	const recommendations = [
		{
			title: 'Gouvernance éthique',
			icon: Scale,
			desc: 'Établir des cadres transparents et garantir la minimisation des données (notamment biométriques) pour protéger la vie privée des citoyens.'
		},
		{
			title: 'Pérennisation',
			icon: GraduationCap,
			desc: 'Former le personnel local et les collectivités pour que ces infrastructures technologiques survivent aux Jeux et profitent au territoire.'
		},
		{
			title: 'Acceptabilité',
			icon: Users,
			desc: 'Associer le grand public et communiquer de façon transparente pour accroître l\'acceptabilité sociale des nouvelles technologies de surveillance.'
		}
	];
</script>

<svelte:head>
	<title>Innovations Technologiques - JO Paris 2024</title>
</svelte:head>

<div class="container mx-auto px-4 py-12 max-w-7xl">
	<div class="text-center mb-16 animate-in slide-in-from-bottom-4 duration-500">
		<h1 class="text-4xl md:text-5xl font-poppins font-bold text-primary mb-4">
			Dashboard des <span class="text-secondary">Innovations</span>
		</h1>
		<p class="text-xl text-gray-600 font-sans max-w-3xl mx-auto">
			Les Jeux Olympiques de Paris 2024 ont servi de vitrine technologique mondiale. Découvrez l'impact, les bénéfices et les risques de ces innovations déployées sur le territoire.
		</p>
	</div>

	<div class="bg-white rounded-3xl shadow-[0_8px_30px_rgb(0,0,0,0.04)] border border-gray-100 overflow-hidden mb-24 animate-in slide-in-from-bottom-8 duration-700">
		<div class="flex overflow-x-auto border-b border-gray-200 hide-scrollbar bg-gray-50">
			{#each domains as domain}
				{@const Icon = domain.icon}
				<!-- svelte-ignore a11y_consider_explicit_label -->
				<button 
					class="flex items-center gap-2 px-6 py-4 whitespace-nowrap font-bold transition-colors border-b-2 flex-shrink-0
						{activeDomainId === domain.id ? 'border-secondary text-primary bg-white' : 'border-transparent text-gray-500 hover:bg-gray-100 hover:text-gray-800'}"
					onclick={() => activeDomainId = domain.id}
				>
					<Icon size={18} class={activeDomainId === domain.id ? 'text-secondary' : ''} />
					{domain.name}
				</button>
			{/each}
		</div>

		<div class="p-8 md:p-12 grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
			
			<div class="lg:col-span-5">
				<div class="inline-flex items-center justify-center w-16 h-16 rounded-2xl bg-gray-100 text-primary mb-6 shadow-sm border border-gray-200">
					<ActiveIcon size={32} />
				</div>
				<h2 class="text-3xl font-bold text-primary mb-4 leading-tight">{activeDomain.name}</h2>
				<div class="w-16 h-1 bg-gold mb-6"></div>
				<p class="text-lg text-gray-700 leading-relaxed font-sans">
					{activeDomain.desc}
				</p>
				
				<div class="mt-10 bg-[#002654]/5 p-6 rounded-2xl border border-[#002654]/10">
					<h4 class="font-bold text-primary mb-3 flex items-center gap-2">
						<span class="w-2.5 h-2.5 rounded-full bg-secondary"></span>
						Lecture du graphique
					</h4>
					<p class="text-sm text-gray-700 font-sans leading-relaxed">
						Le graphique Radar évalue l'impact technologique sur 5 axes (notés sur 10). 
						<br/><br/>
						⚠️ Un score élevé en <strong class="text-secondary">Risques & Éthique</strong> signale des défis majeurs (atteinte à la vie privée, pannes, ou acceptabilité).
					</p>
				</div>
			</div>

			<div class="lg:col-span-7 bg-white rounded-3xl p-2 md:p-6 shadow-inner border border-gray-100 h-[450px] md:h-[500px] w-full">
				<InnovationChart 
					radarData={activeDomain.radarData} 
					domainName={activeDomain.name} 
				/>
			</div>
		</div>
	</div>

	<div>
		<div class="text-center mb-12">
			<h2 class="text-3xl font-bold text-primary mb-4">Recommandations pour l'Héritage</h2>
			<div class="w-24 h-1 bg-accent mx-auto"></div>
		</div>
		
		<div class="grid grid-cols-1 md:grid-cols-3 gap-8">
			{#each recommendations as rec}
				{@const RecIcon = rec.icon}
				<div class="bg-white rounded-2xl p-8 shadow-[0_4px_20px_rgb(0,0,0,0.03)] border border-gray-100 hover:shadow-lg transition-all duration-300 hover:-translate-y-1 group">
					<div class="w-16 h-16 rounded-full bg-accent/10 flex items-center justify-center mb-6 group-hover:bg-accent group-hover:text-white text-accent transition-colors">
						<RecIcon size={32} />
					</div>
					<h3 class="text-xl font-bold text-primary mb-4">{rec.title}</h3>
					<p class="text-gray-600 font-sans leading-relaxed">
						{rec.desc}
					</p>
				</div>
			{/each}
		</div>
	</div>
</div>

<style>
	/* Masquer la barre de défilement (scrollbar) pour les onglets horizontaux sur mobile */
	.hide-scrollbar::-webkit-scrollbar {
		display: none;
	}
	.hide-scrollbar {
		-ms-overflow-style: none;
		scrollbar-width: none;
	}
</style>
