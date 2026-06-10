<script>
	import { onMount } from 'svelte';
	import { gsap } from 'gsap';
	import { ScrollTrigger } from 'gsap/dist/ScrollTrigger';
	import { Network, Trophy, BookOpen, Cpu, ArrowRight } from 'lucide-svelte';

	onMount(() => {

		gsap.registerPlugin(ScrollTrigger);

		gsap.from('.hero-element', {
			opacity: 0,
			y: 50,
			duration: 1,
			stagger: 0.2,
			ease: 'power3.out',
			delay: 0.1
		});

		gsap.fromTo('.bento-card', 
			{ opacity: 0, y: 50 },
			{
				scrollTrigger: {
					trigger: '#explore-section',
					start: 'top 85%'
				},
				opacity: 1,
				y: 0,
				duration: 0.8,
				stagger: 0.15,
				ease: 'power2.out'
			}
		);

		return () => {
			ScrollTrigger.getAll().forEach(t => t.kill());
		};
	});

	function scrollToExplore() {
		const section = document.getElementById('explore-section');
		if (section) {
			section.scrollIntoView({ behavior: 'smooth' });
		}
	}
</script>

<svelte:head>
	<title>Accueil - JO Paris 2024 | Expérience Interactive</title>
</svelte:head>

<section class="relative min-h-[85vh] flex items-center justify-center bg-[#002654] overflow-hidden border-b-8 border-gold">
	<div class="absolute inset-0 bg-gradient-to-tr from-[#001530] via-[#002654] to-[#00387a] opacity-90"></div>
	<div class="absolute w-[500px] h-[500px] bg-gold/10 blur-[150px] rounded-full top-0 left-0 -translate-x-1/2 -translate-y-1/2 pointer-events-none"></div>
	<div class="absolute w-[500px] h-[500px] bg-secondary/10 blur-[150px] rounded-full bottom-0 right-0 translate-x-1/3 translate-y-1/3 pointer-events-none"></div>

	<div class="relative z-10 text-center px-4 max-w-5xl mx-auto">
		<p class="hero-element text-gold uppercase tracking-[0.3em] font-bold text-sm md:text-base mb-6 drop-shadow-md">
			Vibe Coding Project
		</p>
		<h1 class="hero-element text-5xl md:text-7xl font-poppins font-bold text-white mb-8 leading-tight">
			Plongez au cœur des <br/>
			<span class="text-transparent bg-clip-text bg-gradient-to-r from-gold to-[#fff0a8]">
				Jeux Olympiques
			</span> <br/>
			de Paris 2024
		</h1>
		<p class="hero-element text-lg md:text-2xl text-blue-100 font-sans max-w-3xl mx-auto mb-14 leading-relaxed opacity-90">
			Gouvernance, Performances, Héritage et Innovations : explorez l'écosystème olympique à travers une expérience interactive unique.
		</p>
		<div class="hero-element">
			<button 
				onclick={scrollToExplore}
				class="inline-flex items-center gap-3 bg-white text-[#002654] px-8 py-4 rounded-full font-bold text-lg hover:bg-gold hover:text-white transition-all duration-300 shadow-[0_0_30px_rgba(255,215,0,0.3)] hover:shadow-[0_0_50px_rgba(255,215,0,0.6)] hover:-translate-y-1"
			>
				Commencer l'exploration
				<ArrowRight size={20} />
			</button>
		</div>
	</div>
</section>

<section id="explore-section" class="py-24 bg-gray-50 min-h-screen flex items-center">
	<div class="container mx-auto px-4 max-w-6xl">
		<div class="text-center mb-16">
			<h2 class="text-4xl font-poppins font-bold text-[#002654] mb-4">Choisissez votre parcours</h2>
			<div class="w-20 h-1 bg-secondary mx-auto rounded-full"></div>
		</div>

		<div class="grid grid-cols-1 md:grid-cols-2 gap-6 md:gap-8">
			
			<a href="/ecosysteme" class="bento-card group relative overflow-hidden bg-white rounded-3xl p-8 md:p-10 shadow-sm border border-gray-200 hover:shadow-[0_20px_50px_rgba(0,0,0,0.08)] hover:border-gold hover:-translate-y-2 transition-all duration-500 flex flex-col h-full">
				<div class="absolute top-0 right-0 w-32 h-32 bg-gold/5 rounded-bl-full transition-transform duration-500 group-hover:scale-110"></div>
				<div class="w-16 h-16 rounded-2xl bg-[#002654]/5 flex items-center justify-center text-[#002654] group-hover:bg-[#002654] group-hover:text-gold transition-colors duration-300 mb-6 relative z-10">
					<Network size={32} />
				</div>
				<h3 class="text-2xl font-bold text-[#002654] mb-3 font-poppins relative z-10">Infographie Interactive</h3>
				<p class="text-gray-600 font-sans leading-relaxed flex-grow relative z-10 text-lg">
					Découvrez la gouvernance, le budget et les sites clés des Jeux Olympiques à travers des diagrammes réactifs.
				</p>
				<div class="mt-8 font-bold text-sm text-gray-400 group-hover:text-gold uppercase tracking-wider transition-colors duration-300 flex items-center gap-2 relative z-10">
					L'Écosystème <ArrowRight size={16} />
				</div>
			</a>

			<a href="/performances" class="bento-card group relative overflow-hidden bg-white rounded-3xl p-8 md:p-10 shadow-sm border border-gray-200 hover:shadow-[0_20px_50px_rgba(0,0,0,0.08)] hover:border-secondary hover:-translate-y-2 transition-all duration-500 flex flex-col h-full">
				<div class="absolute top-0 right-0 w-32 h-32 bg-secondary/5 rounded-bl-full transition-transform duration-500 group-hover:scale-110"></div>
				<div class="w-16 h-16 rounded-2xl bg-secondary/10 flex items-center justify-center text-secondary group-hover:bg-secondary group-hover:text-white transition-colors duration-300 mb-6 relative z-10">
					<Trophy size={32} />
				</div>
				<h3 class="text-2xl font-bold text-[#002654] mb-3 font-poppins relative z-10">Dashboard Performances</h3>
				<p class="text-gray-600 font-sans leading-relaxed flex-grow relative z-10 text-lg">
					Analysez la route vers l'or de Teddy Riner grâce à des visualisations interactives Echarts de son palmarès.
				</p>
				<div class="mt-8 font-bold text-sm text-gray-400 group-hover:text-secondary uppercase tracking-wider transition-colors duration-300 flex items-center gap-2 relative z-10">
					L'Athlète <ArrowRight size={16} />
				</div>
			</a>

			<a href="/heritage" class="bento-card group relative overflow-hidden bg-white rounded-3xl p-8 md:p-10 shadow-sm border border-gray-200 hover:shadow-[0_20px_50px_rgba(0,0,0,0.08)] hover:border-[#002654] hover:-translate-y-2 transition-all duration-500 flex flex-col h-full">
				<div class="absolute top-0 right-0 w-32 h-32 bg-[#002654]/5 rounded-bl-full transition-transform duration-500 group-hover:scale-110"></div>
				<div class="w-16 h-16 rounded-2xl bg-gray-100 flex items-center justify-center text-gray-700 group-hover:bg-[#002654] group-hover:text-white transition-colors duration-300 mb-6 relative z-10">
					<BookOpen size={32} />
				</div>
				<h3 class="text-2xl font-bold text-[#002654] mb-3 font-poppins relative z-10">Récit Immersif</h3>
				<p class="text-gray-600 font-sans leading-relaxed flex-grow relative z-10 text-lg">
					Plongez dans l'impact des Jeux vu par un habitant de Seine-Saint-Denis, avec une narration Scroll Storytelling.
				</p>
				<div class="mt-8 font-bold text-sm text-gray-400 group-hover:text-[#002654] uppercase tracking-wider transition-colors duration-300 flex items-center gap-2 relative z-10">
					L'Héritage <ArrowRight size={16} />
				</div>
			</a>

			<a href="/innovations" class="bento-card group relative overflow-hidden bg-white rounded-3xl p-8 md:p-10 shadow-sm border border-gray-200 hover:shadow-[0_20px_50px_rgba(0,0,0,0.08)] hover:border-[#00A651] hover:-translate-y-2 transition-all duration-500 flex flex-col h-full">
				<div class="absolute top-0 right-0 w-32 h-32 bg-[#00A651]/5 rounded-bl-full transition-transform duration-500 group-hover:scale-110"></div>
				<div class="w-16 h-16 rounded-2xl bg-[#00A651]/10 flex items-center justify-center text-[#00A651] group-hover:bg-[#00A651] group-hover:text-white transition-colors duration-300 mb-6 relative z-10">
					<Cpu size={32} />
				</div>
				<h3 class="text-2xl font-bold text-[#002654] mb-3 font-poppins relative z-10">Rapport Technologique</h3>
				<p class="text-gray-600 font-sans leading-relaxed flex-grow relative z-10 text-lg">
					Explorez les avancées technologiques en IA, sécurité et mobilité verte à l'aide d'un radar multicritère dynamique.
				</p>
				<div class="mt-8 font-bold text-sm text-gray-400 group-hover:text-[#00A651] uppercase tracking-wider transition-colors duration-300 flex items-center gap-2 relative z-10">
					Les Innovations <ArrowRight size={16} />
				</div>
			</a>

		</div>
	</div>
</section>
