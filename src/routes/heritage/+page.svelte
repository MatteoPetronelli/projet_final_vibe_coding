<svelte:head>
	<title>Héritage - JO Paris 2024</title>
</svelte:head>

<div class="container mx-auto px-4 py-12 min-h-[150vh]">
	<div class="mb-10 text-center">
		<h1 class="text-3xl md:text-5xl font-bold text-primary mb-4">Récit immersif - Héritage</h1>
		<p class="text-lg text-gray-600 font-sans max-w-3xl mx-auto">
			Découvrez l'impact durable des Jeux Olympiques sur la société, l'économie et l'environnement à travers ce récit interactif.
		</p>
	</div>

	<!-- TODO: Intégration future de GSAP pour le Scroll Storytelling -->
	<div class="relative mt-20">
		<!-- Point de repère pour l'animation GSAP -->
		<div class="sticky top-32 bg-white rounded-xl shadow-lg border border-gray-100 p-8 h-[60vh] flex flex-col items-center justify-center z-10">
			<div class="text-center p-6 border-2 border-dashed border-gold rounded-lg bg-yellow-50 w-full h-full flex flex-col justify-center transition-all duration-500">
				<h2 class="text-2xl font-poppins font-bold text-gold mb-4">Zone de Scroll Storytelling (GSAP)</h2>
				<p class="text-gray-600 font-sans">
					Cette zone sera animée au fil du scroll. Le contenu changera dynamiquement avec GSAP et ScrollTrigger pour raconter l'héritage des JO.
				</p>
			</div>
		</div>
		
		<!-- Espacement pour permettre le scroll -->
		<div class="h-[100vh] mt-10 p-8 flex flex-col justify-center items-center opacity-50">
			<p class="font-montserrat text-xl text-gray-400">Section de récit 1</p>
		</div>
		<div class="h-[100vh] p-8 flex flex-col justify-center items-center opacity-50">
			<p class="font-montserrat text-xl text-gray-400">Section de récit 2</p>
		</div>
	</div>
</div>
