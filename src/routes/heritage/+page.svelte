<script>
	import { onMount } from 'svelte';
	import { gsap } from 'gsap';
	import { ScrollTrigger } from 'gsap/dist/ScrollTrigger';
	import { MapPin, HardHat, TrendingUp, AlertTriangle, Heart } from 'lucide-svelte';
	import BeforeAfter from '$lib/components/BeforeAfter.svelte';

	onMount(() => {

		gsap.registerPlugin(ScrollTrigger);

		const screens = gsap.utils.toArray('.story-screen');

		screens.forEach((screen) => {
			const content = screen.querySelector('.story-content');
			

			gsap.from(content, {
				scrollTrigger: {
					trigger: screen,
					start: 'top 75%',
					toggleActions: 'play none none reverse'
				},
				opacity: 0,
				y: 50,
				duration: 1.2,
				ease: 'power3.out'
			});
		});

		return () => {
			ScrollTrigger.getAll().forEach(t => t.kill());
		};
	});
</script>

<svelte:head>
	<title>Héritage & Impact Local - JO Paris 2024</title>
</svelte:head>

<div class="bg-gray-950 min-h-screen text-gray-200 font-sans selection:bg-gold selection:text-primary overflow-x-hidden">
	
	<section class="story-screen min-h-screen flex items-center justify-center p-6 md:p-12 border-b border-gray-800 relative">
		<div class="absolute top-0 right-0 w-1/2 h-full bg-gradient-to-bl from-primary/10 to-transparent pointer-events-none"></div>

		<div class="story-content max-w-5xl mx-auto grid grid-cols-1 lg:grid-cols-2 gap-12 items-center relative z-10 w-full">
			<div>
				<p class="text-gold font-bold tracking-widest uppercase mb-4 text-sm">Le revers de la médaille</p>
				<h1 class="text-5xl md:text-6xl font-bold text-white mb-6 leading-tight">
					L'Héritage <br/>
					<span class="text-transparent bg-clip-text bg-gradient-to-r from-gold to-yellow-200">
						Vu de l'Intérieur
					</span>
				</h1>
				<p class="text-xl text-gray-400 leading-relaxed mb-6">
					Je suis habitant de Saint-Denis depuis toujours. On nous a dit que <strong class="text-white">80% des investissements</strong> des Jeux viseraient notre département.
				</p>
				<p class="text-lg text-gray-400 leading-relaxed">
					Deux projets phares sortent de terre ici : le Village olympique et le Centre aquatique. Une aubaine sur le papier, mais qu'en est-il de la réalité locale ?
				</p>
			</div>
			
			<div class="grid grid-cols-2 gap-4 md:gap-6 mt-8 lg:mt-0">
				<div class="bg-gray-900/80 backdrop-blur-md border border-gray-800 p-8 rounded-2xl flex flex-col items-center text-center shadow-xl hover:border-primary transition-colors">
					<MapPin size={48} class="text-primary mb-4" />
					<h3 class="font-bold text-white text-lg">Saint-Denis</h3>
					<p class="text-sm text-gray-500 mt-2">Épicentre de l'événement</p>
				</div>
				<div class="bg-gray-900/80 backdrop-blur-md border border-gray-800 p-8 rounded-2xl flex flex-col items-center text-center shadow-xl translate-y-8 hover:border-gold transition-colors">
					<HardHat size={48} class="text-gold mb-4" />
					<h3 class="font-bold text-white text-lg">Chantiers</h3>
					<p class="text-sm text-gray-500 mt-2">Transformations massives</p>
				</div>
			</div>
		</div>
	</section>

	<section class="story-screen min-h-screen flex items-center justify-center p-6 md:p-12 border-b border-gray-800 bg-gray-900/50">
		<div class="story-content max-w-5xl mx-auto w-full">
			<div class="mb-12 text-center max-w-3xl mx-auto">
				<h2 class="text-4xl md:text-5xl font-bold text-white mb-6">
					Le Logement : <br/><span class="text-secondary mt-2 inline-block">Contraste & Scepticisme</span>
				</h2>
				<p class="text-xl text-gray-400 leading-relaxed">
					L'ancien site industriel se transforme en 6 000 logements modernes. Pourtant, le scepticisme règne : seuls <strong class="text-white">25% seront réservés aux foyers modestes</strong>, alors qu'un tiers du département vit sous le seuil de pauvreté.
				</p>
			</div>

			<div class="mb-16">
				<BeforeAfter />
			</div>

			<div class="border-l-4 border-secondary bg-gray-950 p-8 md:p-10 rounded-r-2xl shadow-2xl max-w-4xl mx-auto relative overflow-hidden group">
				<div class="text-secondary opacity-5 absolute -top-10 -left-6 text-[150px] font-serif leading-none transition-transform group-hover:scale-110 duration-500">"</div>
				
				<p class="text-2xl md:text-3xl text-gray-300 italic font-medium relative z-10 pl-4 md:pl-8 leading-relaxed">
					Personne n’attendait des JO qu’ils améliorent la situation du logement – au contraire, ça l’a aggravée. Les familles relogées suite aux démolitions tardent à recevoir un toit équivalent.
				</p>
				<p class="text-right text-gray-500 mt-6 text-sm md:text-base uppercase tracking-widest font-bold">
					— Collectif de manifestants locaux
				</p>
			</div>
		</div>
	</section>

	<section class="story-screen min-h-screen flex items-center justify-center p-6 md:p-12 border-b border-gray-800 relative">
		<div class="story-content max-w-5xl mx-auto grid grid-cols-1 lg:grid-cols-2 gap-16 items-center w-full relative z-10">
			
			<div class="order-2 lg:order-1 flex flex-col gap-6">
				<div class="bg-gray-900 border border-gray-800 p-6 md:p-8 rounded-2xl flex items-start gap-4 hover:bg-gray-800/80 transition-colors">
					<TrendingUp class="text-accent flex-shrink-0 mt-1" size={32} />
					<div>
						<h3 class="font-bold text-white text-xl mb-2">Attractivité inédite</h3>
						<p class="text-gray-400 leading-relaxed">Tesla, la DGSI, le prolongement de la ligne 14 du métro... Les infrastructures se modernisent à vitesse grand V pour accueillir le monde.</p>
					</div>
				</div>
				<div class="bg-gray-900 border border-gray-800 p-6 md:p-8 rounded-2xl flex items-start gap-4 hover:bg-gray-800/80 transition-colors">
					<AlertTriangle class="text-secondary flex-shrink-0 mt-1" size={32} />
					<div>
						<h3 class="font-bold text-white text-xl mb-2">Chômage endémique</h3>
						<p class="text-gray-400 leading-relaxed">Le quotidien ne change pas pour la majorité. Malgré les milliers d'emplois de chantier, l'insertion à long terme reste faible.</p>
					</div>
				</div>
			</div>
			
			<div class="order-1 lg:order-2">
				<h2 class="text-4xl md:text-5xl font-bold text-white mb-6">
					L'Économie : <br/>La crainte de la <span class="text-accent">"Bulle"</span>
				</h2>
				<div class="w-20 h-1 bg-accent mb-8"></div>
				<p class="text-xl text-gray-400 leading-relaxed mb-6">
					Les maires vantent l'arrivée de nouvelles entreprises et la métamorphose de nos quartiers. C'est indéniable, le paysage change.
				</p>
				<p class="text-lg text-gray-500 italic bg-gray-900/50 p-6 border-l-2 border-gray-700 rounded-r-lg">
					Mais cette activité est-elle pérenne ? Est-ce que ces emplois resteront quand la flamme s'éteindra, ou vivons-nous dans une bulle éphémère ?
				</p>
			</div>
		</div>
	</section>

	<section class="story-screen min-h-screen flex items-center justify-center p-6 md:p-12 bg-gradient-to-b from-gray-950 to-[#001530] relative overflow-hidden">
		<div class="absolute bottom-0 left-1/2 -translate-x-1/2 w-full max-w-3xl h-96 bg-primary/20 blur-[100px] rounded-full pointer-events-none"></div>

		<div class="story-content max-w-4xl mx-auto text-center relative z-10">
			<div class="inline-flex items-center justify-center w-24 h-24 rounded-full bg-gray-900 border-2 border-primary/30 mb-8 shadow-[0_0_30px_rgba(0,38,84,0.5)]">
				<Heart class="text-primary" size={40} />
			</div>
			
			<h2 class="text-4xl md:text-5xl font-bold text-white mb-10">
				Cohésion Sociale & <span class="text-transparent bg-clip-text bg-gradient-to-r from-blue-400 to-primary">Avenir</span>
			</h2>
			
			<div class="text-xl text-gray-300 leading-relaxed space-y-8 text-left md:text-center max-w-3xl mx-auto">
				<p>
					Il y a, malgré tout, une immense fierté de voir notre cité au cœur de l'attention mondiale. Être l'épicentre des Jeux, c'est historique pour Saint-Denis.
				</p>
				<p class="bg-gray-900/40 p-6 rounded-2xl border border-gray-800">
					Toutefois, les <strong class="text-secondary">déplacements de populations fragiles</strong> — étudiants relogés en urgence, sans-abris éloignés des regards — nourrissent légitimement l'inquiétude d'un "nettoyage social" déguisé en fête.
				</p>
				<p class="text-2xl font-medium text-white mt-12 md:mt-16 border-t border-gray-800 pt-12 md:pt-16 leading-tight">
					L'héritage a un potentiel extraordinaire pour désenclaver notre territoire. Mais il faudra <span class="text-gold">continuer à lutter</span> pour que la population locale en bénéficie réellement à long terme.
				</p>
			</div>

			<div class="mt-24 text-gray-600 font-bold tracking-widest uppercase text-xs md:text-sm flex items-center justify-center gap-4">
				<div class="w-12 h-px bg-gray-800"></div>
				Fin du récit interactif
				<div class="w-12 h-px bg-gray-800"></div>
			</div>
		</div>
	</section>

</div>
