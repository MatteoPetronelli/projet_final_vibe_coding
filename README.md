# Projet Vibe Coding - Jeux Olympiques de Paris 2024

![SvelteKit](https://img.shields.io/badge/SvelteKit-FF3E00?style=for-the-badge&logo=svelte&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)
![Apache Echarts](https://img.shields.io/badge/Apache%20Echarts-AA344D?style=for-the-badge&logo=apacheecharts&logoColor=white)
![GSAP](https://img.shields.io/badge/GSAP-88CE02?style=for-the-badge&logo=greensock&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)

Ce projet est une Web Application interactive et immersive conçue pour explorer en profondeur l'écosystème entourant les Jeux Olympiques de Paris 2024. Réalisé dans un cadre académique (Évaluation Niveau B2), il s'appuie sur une approche novatrice de développement logiciel appelée "Vibe Coding", en tirant parti de l'assistance de l'Intelligence Artificielle (Antigravity et Gemini 3.1 Pro) pour accélérer et affiner le processus de développement.

## Démonstration en production

L'application est déployée de manière continue et optimisée pour des performances de production.

**[Accéder à la Web App en direct](https://projet-final-vibe-coding.vercel.app)**

---

## Architecture de l'Application et Fonctionnalités

L'application est divisée en quatre piliers thématiques distincts, chacun exploitant des concepts spécifiques de développement front-end et de data visualization.

### 1. Accueil Immersif (Landing Page)
La page de présentation a été pensée pour plonger immédiatement l'utilisateur dans l'expérience.
- **Hero Section Cinematique** : Utilisation d'animations en cascade (stagger) gérées par GSAP pour l'apparition des éléments textuels et des appels à l'action.
- **Navigation via Bento Grid** : Remplacement des menus de navigation classiques par une grille modulaire animée au défilement (ScrollTrigger). Chaque module de la grille présente des micro-interactions avancées au survol (effets de relief, ombres portées dynamiques).

### 2. Infographie Interactive (Écosystème)
Une section dédiée à la compréhension de la structure organisationnelle des Jeux.
- **Gouvernance et Acteurs** : Présentation sous forme d'organigramme réactif permettant de consulter les détails de chaque instance (CIO, COJO, SOLIDEO) via la gestion d'état interne de Svelte.
- **Répartition du Budget** : Intégration d'un graphique en anneau (Donut Chart) propulsé par Apache Echarts, illustrant la répartition des financements entre secteurs publics et privés.

### 3. Dashboard Athlète (Performances)
Un outil analytique ciblé sur le parcours sportif.
- **Filtrage Dynamique** : Utilisation des "Runes" (Svelte 5) pour filtrer en temps réel le palmarès de Teddy Riner (Jeux Olympiques, Grand Slam, Open).
- **Évolution des Points WRL** : Graphique en barres interactif avec Echarts. Le clic sur un point de données déclenche l'apparition d'un panneau d'informations détaillées concernant la compétition sélectionnée.

### 4. Récit Immersif (Héritage)
Une page narrative adoptant le format "Scroll Storytelling".
- **Déclencheurs de défilement (GSAP)** : Le contenu textuel et visuel apparaît et se dissipe progressivement à mesure que l'utilisateur défile vers le bas.
- **Composant de Comparaison Visuelle** : Intégration d'un composant de type "Avant / Après" basé sur un fondu enchaîné d'opacité, illustrant la transformation urbaine de la Seine-Saint-Denis.

### 5. Rapport Technologique (Innovations)
Un tableau de bord évaluant l'impact des déploiements technologiques.
- **Graphique Radar Multicritère** : Utilisation d'Echarts pour visualiser les scores de chaque domaine d'innovation selon 5 axes (Sécurité, Efficacité, Expérience, Durabilité, Risques Éthiques).
- **Navigation par Onglets** : Changement contextuel fluide de l'intégralité du contenu et du graphique Radar via une structure d'onglets (Tabs).

---

## Architecture Technique et Implémentation

Le projet s'appuie sur une pile technologique moderne (Stack SvelteKit) afin de garantir fluidité, maintenabilité et performances.

- **Framework Front-End** : **SvelteKit** (Configuration avec le mode expérimental Svelte 5 "Runes" activé pour une réactivité optimisée).
- **Styling et Mise en page** : **Tailwind CSS v4** pour un styling utilitaire rapide, complété par l'utilisation de variables CSS personnalisées.
- **Data Visualization** : **Apache Echarts** sélectionné pour sa légèreté, ses animations natives et la richesse de ses options de personnalisation.
- **Moteur d'Animation** : **GSAP (GreenSock Animation Platform)** couplé au plugin **ScrollTrigger** pour piloter les animations basées sur le défilement et le chargement.
- **Système d'Icônes** : **Lucide-Svelte** pour une iconographie vectorielle cohérente et performante.
- **Déploiement** : Hébergement via **Vercel** avec l'adaptateur Vercel de SvelteKit. L'application a été configurée en mode SPA (Single Page Application, `ssr = false`) afin de garantir une compatibilité parfaite des librairies de manipulation du DOM (Echarts, GSAP) avec l'environnement de production.

---

## Design System

Le design de l'application est strictement aligné sur la charte institutionnelle de l'événement Paris 2024.

- **Couleurs Principales** :
  - Bleu Institutionnel : `#002654`
  - Or : `#FFD700`
  - Rouge : `#ED2939`
  - Vert : `#00A651`
- **Typographie** : 
  - `Poppins` et `Montserrat` pour des titres modernes et impactants.
  - `Open Sans` pour une lisibilité accrue des contenus descriptifs.

---

## Déploiement Local et Installation

Pour initialiser l'environnement de développement sur une machine locale, veuillez suivre les étapes ci-dessous :

1. Cloner le dépôt :
```bash
git clone https://github.com/votre-utilisateur/projet_final_vibe_coding.git
cd projet_final_vibe_coding
```

2. Installer les paquets requis :
```bash
npm install
```

3. Lancer le serveur de développement :
```bash
npm run dev
```

L'application sera accessible localement via l'adresse `http://localhost:5173`.

---

## Monitoring et Performances de Production

Afin d'assurer le suivi de la qualité du service, ce projet embarque les solutions de télémétrie de Vercel :

- **Vercel Analytics** (`@vercel/analytics`) : Pour l'analyse quantitative du trafic et de l'engagement utilisateur.
- **Vercel Speed Insights** (`@vercel/speed-insights`) : Pour l'évaluation continue des métriques de performance web (Core Web Vitals).

---

## Contexte Académique

Ce projet a été réalisé en tant que livrable de validation (Épreuve Session 2 - Durée : 2H). Il démontre la capacité à conceptualiser, développer et déployer une architecture front-end complète en s'appuyant sur les paradigmes du développement assisté par l'IA.

**Développeur :** Petronelli Matteo
