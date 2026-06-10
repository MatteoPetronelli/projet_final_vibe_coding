<script>
	import { Factory, Building2 } from 'lucide-svelte';
	let isHovered = $state(false);
</script>

<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
<div 
	class="relative w-full h-[300px] md:h-[400px] rounded-2xl overflow-hidden cursor-ew-resize border border-gray-700 shadow-2xl"
	onmouseenter={() => isHovered = true}
	onmouseleave={() => isHovered = false}
	role="img"
	aria-label="Comparaison Avant/Après : Friche industrielle vs Logements"
>
	<div 
		class="absolute inset-0 bg-gray-900 flex flex-col items-center justify-center p-8 transition-opacity duration-700 ease-in-out"
		style="opacity: {isHovered ? 0 : 1};"
	>
		<Factory size={64} class="mb-6 text-gray-600 opacity-50" />
		<h3 class="text-3xl md:text-4xl font-bold text-gray-500 mb-2 uppercase tracking-widest">Avant 2024</h3>
		<p class="text-gray-400 font-sans text-center max-w-sm">Anciens sites industriels, zones en friche et terrains délaissés de Seine-Saint-Denis.</p>
	</div>

	<div 
		class="absolute inset-0 bg-[#002654] flex flex-col items-center justify-center p-8 transition-opacity duration-700 ease-in-out"
		style="opacity: {isHovered ? 1 : 0};"
	>
		<Building2 size={64} class="mb-6 text-gold drop-shadow-md" />
		<h3 class="text-3xl md:text-4xl font-bold text-white mb-2 uppercase tracking-widest">Héritage</h3>
		<p class="text-blue-200 font-sans text-center max-w-sm">Nouveaux éco-quartiers, 6 000 logements modernes (mais seulement 25% de social).</p>
	</div>

	{#if !isHovered}
		<div class="absolute bottom-4 left-1/2 -translate-x-1/2 bg-black/50 backdrop-blur-sm text-white px-4 py-2 rounded-full text-sm font-bold animate-pulse z-20 border border-white/20">
			Survolez pour voir l'évolution
		</div>
	{/if}
</div>
