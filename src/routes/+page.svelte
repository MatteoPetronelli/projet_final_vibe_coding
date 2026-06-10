<script>
	import { ArrowRight } from 'lucide-svelte';
</script>

<svelte:head>
	<title>Accueil - JO Paris 2024</title>
</svelte:head>

<div class="container mx-auto px-4 py-16 md:py-24 flex flex-col items-center justify-center text-center">
	<h1 class="text-4xl md:text-6xl font-bold text-primary mb-6 leading-tight">
		Bienvenue dans l'Écosystème des <br class="hidden md:block" />
		<span class="text-secondary">Jeux Olympiques Paris 2024</span>
	</h1>
	
	<p class="text-lg md:text-xl text-gray-600 max-w-2xl mb-12 font-sans">
		Découvrez une expérience immersive au cœur des performances, des innovations et de l'héritage exceptionnel de cet événement planétaire.
	</p>
	
	<a href="/ecosysteme" class="inline-flex items-center gap-2 bg-primary hover:bg-opacity-90 text-gold font-poppins font-semibold py-4 px-8 rounded-full transition-all hover:scale-105 shadow-lg">
		Découvrir l'écosystème
		<ArrowRight size={20} />
	</a>
	
	<!-- Placeholder pour des éléments visuels futurs (ex: GSAP, 3D) -->
	<div class="mt-16 w-full max-w-4xl h-64 bg-gray-200 rounded-2xl flex items-center justify-center border-2 border-dashed border-gray-300">
		<p class="text-gray-500 font-medium">Ici, vous pourrez intégrer des animations d'introduction ou une scène immersive.</p>
	</div>
</div>
