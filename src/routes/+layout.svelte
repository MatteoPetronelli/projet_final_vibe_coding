<script>
	import { injectSpeedInsights } from '@vercel/speed-insights/sveltekit';
	import './layout.css';

	injectSpeedInsights();

	let { children } = $props();
</script>

<div class="min-h-screen flex flex-col bg-gray-50">
	<header class="bg-primary text-white sticky top-0 z-50 shadow-md">
		<div class="container mx-auto px-4 py-4 flex flex-col md:flex-row justify-between items-center">
			<a href="/" class="text-2xl font-poppins font-bold text-gold mb-4 md:mb-0">JO Paris 2024</a>
			<nav>
				<ul class="flex flex-wrap justify-center gap-6 font-montserrat font-medium">
					<li><a href="/ecosysteme" class="hover:text-gold transition-colors">Écosystème</a></li>
					<li><a href="/performances" class="hover:text-gold transition-colors">Performances</a></li>
					<li><a href="/heritage" class="hover:text-gold transition-colors">Héritage</a></li>
					<li><a href="/innovations" class="hover:text-gold transition-colors">Innovations</a></li>
				</ul>
			</nav>
		</div>
	</header>

	<main class="flex-grow">
		{@render children()}
	</main>

	<footer class="bg-primary text-white py-8 mt-12">
		<div class="container mx-auto px-4 text-center">
			<p class="font-montserrat font-bold mb-4">Projet Vibe Coding - JO Paris 2024</p>
			<div class="flex justify-center flex-wrap gap-6 text-sm text-gray-300 mt-6 md:mt-0">
				<a href="https://www.olympics.com/fr/olympic-games/paris-2024" target="_blank" rel="noopener noreferrer" class="hover:text-gold transition-colors">Site Officiel 2024</a>
				<a href="https://www.olympics.com/cio/paris-2024" target="_blank" rel="noopener noreferrer" class="hover:text-gold transition-colors">CIO</a>
				<a href="https://www.olympics.com/cio/comites-d-organisation-des-jeux-olympiques" target="_blank" rel="noopener noreferrer" class="hover:text-gold transition-colors">COJO</a>
				<a href="https://www.ouvrages-olympiques.fr/" target="_blank" rel="noopener noreferrer" class="hover:text-gold transition-colors">SOLIDEO</a>
			</div>
		</div>
	</footer>
</div>
