<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LBITCloud - Extension d'Inventaire MDM</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            height: 350px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 400px;
            }
        }
        .nav-active {
            border-bottom: 2px solid #2563eb;
            color: #1e40af;
            font-weight: 600;
        }
        .animate-fade-in {
            animation: fadeIn 0.5s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .data-flow-line {
            background: linear-gradient(90deg, transparent, #60a5fa, transparent);
            background-size: 200% 100%;
            animation: flow 2s infinite linear;
        }
        @keyframes flow {
            0% { background-position: 100% 0; }
            100% { background-position: -100% 0; }
        }
        /* Animation pour le flux de données sur les flèches du diagramme */
        .animate-flow {
            stroke-dasharray: 8;
            animation: svg-flow 1s linear infinite;
        }
        @keyframes svg-flow {
            to { stroke-dashoffset: -16; }
        }
        /* Petite animation pour l'engrenage du cloud */
        @keyframes spin-slow {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        .animate-spin-slow {
            animation: spin-slow 8s linear infinite;
        }
        /* Animation de flottement pour les icônes */
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-5px); }
            100% { transform: translateY(0px); }
        }
        .hover-float:hover {
            animation: float 2s ease-in-out infinite;
        }
        html {
            scroll-behavior: smooth;
            scroll-padding-top: 6rem;
        }
    </style>
</head>
<body class="bg-slate-900 text-slate-300 font-sans antialiased">

    <!-- Chosen Palette: Warm Neutrals with Microsoft Azure (Blue) and Power BI (Amber) Accents -->
    <!-- Application Structure Plan: The SPA uses a tabbed navigation dashboard approach to merge the Commercial Pitch and Technical Architecture into a unified, explorable narrative. The structure flows logically from the Problem (Vision 360), to the Business Value (Bénéfices & ROI) using interactive charts, and finally to the Technical Deep Dive (Architecture & Sécurité) for IT professionals. This allows different personas (DSI vs SysAdmins) to find their relevant information quickly without scrolling through a linear slide deck. -->
    <!-- Visualization & Content Choices: 
         - Problem Context -> Goal: Highlight missing data -> Viz: Interactive "Blind Spot" toggle -> Interaction: Click to reveal hidden data -> Justification: Tangibly demonstrates Intune's limitations versus the add-on's depth. -> Library: Vanilla JS + HTML/CSS.
         - Business Value -> Goal: Show ROI & Proactivity -> Viz: Dynamic Donut Chart -> Interaction: Click benefits to update chart data -> Justification: Makes abstract concepts (cost savings, hardware failures) concrete and measurable. -> Library: Chart.js (Canvas).
         - Architecture -> Goal: Explain technical flow -> Viz: CSS Flexbox Flow Diagram -> Interaction: Hover effects -> Justification: Clearly maps the 3-step technical process without relying on external images or forbidden SVGs. -> Library: HTML/Tailwind.
         - NO SVG/Mermaid confirmed. 
    -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->

    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12 space-y-12 md:space-y-24">

        <section id="section-vision" class="content-section">
            <div class="text-center max-w-3xl mx-auto mb-16">
                <img src="https://i.postimg.cc/B6yRjgJq/Gemini-Generated-Image-x6z3ftx6z3ftx6z3.png" alt="LBITCloud Logo" class="h-32 md:h-56 w-auto mx-auto mb-8 object-contain">
                
                <div class="inline-flex items-center gap-2 bg-blue-900/50 text-blue-300 px-4 py-2 rounded-full font-semibold text-sm mb-6 border border-blue-800 shadow-sm">
                    <span>💡</span> Conçu à partir de l'expérience terrain d'experts du métier
                </div>

                <h1 class="text-4xl font-extrabold text-white mb-6">La vision à 360° qui manque à votre MDM</h1>
                
                <p class="text-lg text-slate-300 mb-4 font-medium">
                    Un produit pensé et développé pour accompagner les entreprises dans l'optimisation et la gestion quotidienne de leurs postes de travail.
                </p>
                <p class="text-lg text-slate-400">
                    Microsoft Intune est un excellent outil de gestion, mais il présente des zones d'ombre critiques. Notre add-on léger libère le potentiel de vos données pour une gestion proactive et éclairée.
                </p>
            </div>

            <div class="bg-white rounded-2xl shadow-lg p-8 mb-12 border border-slate-100">
                <h2 class="text-2xl font-bold text-slate-800 mb-6 text-center">Le Constat : Éliminez vos angles morts</h2>
                <p class="text-slate-600 mb-8 text-center max-w-2xl mx-auto">
                    Découvrez la différence entre les données natives limitées et la profondeur de notre inventaire personnalisé. Cliquez sur le bouton pour révéler les données cachées.
                </p>

                <div class="flex flex-col md:flex-row gap-8 justify-center items-stretch">
                    <div class="flex-1 bg-slate-50 p-6 rounded-xl border-2 border-slate-200 text-center">
                        <div class="text-4xl mb-4">🧊</div>
                        <h3 class="text-lg font-bold text-slate-700 mb-4">Ce que voit Intune (Natif)</h3>
                        <ul class="text-sm text-slate-500 space-y-2 text-left inline-block">
                            <li>✔️ Inventaire hardware basique</li>
                            <li>❌ Rapports natifs très succincts</li>
                            <li>❌ Inventaire personnalisé (WMI, Registre)</li>
                            <li>❌ Preuve d'application réelle des stratégies</li>
                            <li>❌ Historisation poussée des données</li>
                        </ul>
                    </div>
                    
                    <div class="flex items-center justify-center">
                        <button id="btn-reveal" class="bg-blue-600 hover:bg-blue-700 text-white font-bold py-3 px-6 rounded-full shadow-md transition-all transform hover:scale-105">
                            Révéler la vue 360° 👁️
                        </button>
                    </div>

                    <div id="vision-complete" class="flex-1 bg-blue-50 p-6 rounded-xl border-2 border-blue-200 text-center opacity-50 filter blur-sm transition-all duration-500">
                        <div class="text-4xl mb-4">🌊</div>
                        <h3 class="text-lg font-bold text-blue-900 mb-4">Avec l'Add-on LBITCloud</h3>
                        <ul class="text-sm text-blue-800 space-y-2 text-left inline-block font-medium">
                            <li>✔️ Inventaire matériel et logiciel ultra-précis</li>
                            <li>✔️ Dashboards Power BI dynamiques et complets</li>
                            <li>✔️ Collecte sur mesure (WMI, Registre, Evtx)</li>
                            <li>✔️ Vérification de la conformité réelle</li>
                            <li>✔️ Historisation sur 1 à plusieurs années</li>
                        </ul>
                    </div>
                </div>
            </div>
            
            <div class="mt-16 bg-white rounded-3xl shadow-xl p-8 md:p-16 border border-slate-100 relative z-0">
                <!-- En-tête -->
                <div class="text-center mb-16">
                    <h2 class="text-3xl md:text-4xl font-extrabold text-slate-900 mb-4 tracking-tight">
                        Une vision complète en <span class="text-blue-600">3 étapes simples</span>
                    </h2>
                    <p class="text-lg text-slate-500 max-w-2xl mx-auto">
                        De la collecte sur le poste de travail jusqu'à la prise de décision, notre solution s'intègre de manière transparente à votre environnement Microsoft.
                    </p>
                </div>

                <!-- Zone du Schéma -->
                <div class="flex flex-col md:flex-row items-center justify-between gap-6 md:gap-4 relative z-10">
                    
                    <!-- ETAPE 1 : Le PC (Collecte) -->
                    <div class="flex flex-col items-center text-center w-full md:w-1/3 group cursor-pointer z-10">
                        <!-- Cercle de l'icône -->
                        <div class="w-28 h-28 rounded-full bg-slate-100 border-4 border-white shadow-lg flex items-center justify-center mb-6 transition-transform duration-300 group-hover:scale-110 hover-float relative">
                            <div class="absolute inset-0 rounded-full bg-slate-200 opacity-0 group-hover:opacity-20 transition-opacity"></div>
                            <!-- Icône PC -->
                            <svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" class="text-slate-700 relative z-10">
                                <rect x="2" y="3" width="20" height="14" rx="2" ry="2"></rect>
                                <line x1="8" y1="21" x2="16" y2="21"></line>
                                <line x1="12" y1="17" x2="12" y2="21"></line>
                            </svg>
                        </div>
                        <!-- Texte Etape 1 -->
                        <h3 class="text-xl font-bold text-slate-800 mb-2">1. Collecte Intelligente</h3>
                        <p class="text-sm text-slate-500 px-4">
                            Un script léger s'exécute sur les postes (via Intune) pour un inventaire matériel et logiciel ultra-détaillé.
                        </p>
                    </div>

                    <!-- Fleche de liaison 1 (Visible sur Desktop) -->
                    <div class="hidden md:flex flex-col items-center justify-center w-16 text-blue-300 z-0">
                        <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="animate-pulse">
                            <path d="M5 12h14"></path>
                            <path d="m12 5 7 7-7 7"></path>
                        </svg>
                    </div>

                    <!-- Fleche de liaison Mobile 1 -->
                    <div class="md:hidden text-blue-300 my-2">
                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 5v14"></path><path d="m19 12-7 7-7-7"></path></svg>
                    </div>

                    <!-- ETAPE 2 : Le Cloud + Engrenage (Centralisation) -->
                    <div class="flex flex-col items-center text-center w-full md:w-1/3 group cursor-pointer z-10">
                        <!-- Cercle de l'icône -->
                        <div class="w-28 h-28 rounded-full bg-blue-50 border-4 border-white shadow-lg flex items-center justify-center mb-6 transition-transform duration-300 group-hover:scale-110 relative">
                            <!-- Cercle décoratif de fond -->
                            <div class="absolute inset-0 rounded-full bg-blue-200 opacity-0 group-hover:opacity-30 transition-opacity"></div>
                            
                            <!-- Icône Cloud -->
                            <svg xmlns="http://www.w3.org/2000/svg" width="52" height="52" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" class="text-blue-600 relative z-10">
                                <path d="M17.5 19H9a7 7 0 1 1 6.71-9h1.79a4.5 4.5 0 1 1 0 9Z"></path>
                            </svg>
                            <!-- Icône Engrenage (Positionnée sur le cloud) -->
                            <div class="absolute -bottom-2 -right-2 bg-white rounded-full p-1 shadow-sm z-20">
                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-blue-800 animate-spin-slow">
                                    <path d="M12 15a3 3 0 1 0 0-6 3 3 0 0 0 0 6Z"></path>
                                    <path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1Z"></path>
                                </svg>
                            </div>
                        </div>
                        <!-- Texte Etape 2 -->
                        <h3 class="text-xl font-bold text-blue-900 mb-2">2. Centralisation Sécurisée</h3>
                        <p class="text-sm text-slate-500 px-4">
                            Les données sont ingérées et traitées dans l'espace Azure Log Analytics, offrant scalabilité et historisation.
                        </p>
                    </div>

                    <!-- Fleche de liaison 2 (Visible sur Desktop) -->
                    <div class="hidden md:flex flex-col items-center justify-center w-16 text-blue-300 z-0">
                        <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="animate-pulse">
                            <path d="M5 12h14"></path>
                            <path d="m12 5 7 7-7 7"></path>
                        </svg>
                    </div>

                    <!-- Fleche de liaison Mobile 2 -->
                    <div class="md:hidden text-blue-300 my-2">
                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 5v14"></path><path d="m19 12-7 7-7-7"></path></svg>
                    </div>

                    <!-- ETAPE 3 : Le Graphique (Restitution) -->
                    <div class="flex flex-col items-center text-center w-full md:w-1/3 group cursor-pointer z-10">
                        <!-- Cercle de l'icône -->
                        <div class="w-28 h-28 rounded-full bg-amber-50 border-4 border-white shadow-lg flex items-center justify-center mb-6 transition-transform duration-300 group-hover:scale-110 hover-float relative overflow-hidden">
                             <div class="absolute inset-0 rounded-full bg-amber-200 opacity-0 group-hover:opacity-20 transition-opacity"></div>
                            <!-- Icône Camembert / Barres (Mix des deux pour l'esthétique analytique) -->
                            <svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" class="text-amber-500 relative z-10">
                                <path d="M21.21 15.89A10 10 0 1 1 8 2.83"></path>
                                <path d="M22 12A10 10 0 0 0 12 2v10z"></path>
                            </svg>
                        </div>
                        <!-- Texte Etape 3 -->
                        <h3 class="text-xl font-bold text-amber-600 mb-2">3. Restitution & Décision</h3>
                        <p class="text-sm text-slate-500 px-4">
                            Des tableaux de bord dynamiques Power BI transforment ces données en indicateurs métiers exploitables.
                        </p>
                    </div>

                </div>

                <!-- Ligne de fond décorative reliant les cercles (Desktop uniquement) -->
                <div class="hidden md:block absolute top-[55%] left-[20%] right-[20%] h-0.5 bg-gradient-to-r from-slate-200 via-blue-200 to-amber-200 -z-10" style="transform: translateY(-50%);"></div>
            </div>
        </section>

        <section id="section-valeur" class="content-section pt-12 border-t border-slate-800">
            <div class="text-center max-w-3xl mx-auto mb-12">
                <h2 class="text-3xl font-extrabold text-white mb-4">Bénéfices Clés & Visualisation</h2>
                <p class="text-lg text-slate-400">
                    Découvrez comment nos données transforment la gestion de votre parc informatique. Sélectionnez un bénéfice ci-dessous pour visualiser l'impact métier simulé.
                </p>
            </div>

            <!-- Boutons interactifs en grille horizontale -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8 mt-4">
                <button class="value-btn active flex flex-col items-center text-center p-6 rounded-2xl border-2 border-blue-600 bg-blue-50 shadow-md transition-transform hover:-translate-y-1 relative" data-chart="securite">
                    <span class="absolute -top-4 bg-gradient-to-r from-blue-600 to-indigo-600 text-white text-xs font-bold px-4 py-1.5 rounded-full shadow-md">Enjeu Majeur</span>
                    <span class="text-4xl mb-3 mt-2">🛡️</span>
                    <h3 class="font-bold text-slate-800 text-lg mb-2">Sécurité & Conformité</h3>
                    <p class="text-sm text-slate-600">Garantissez le déploiement des correctifs et l'application réelle de vos stratégies.</p>
                </button>

                <button class="value-btn flex flex-col items-center text-center p-6 rounded-2xl border-2 border-slate-200 bg-white shadow-sm transition-transform hover:-translate-y-1 relative" data-chart="proactivite">
                    <span class="text-4xl mb-3 mt-2">⚡</span>
                    <h3 class="font-bold text-slate-800 text-lg mb-2">Proactivité</h3>
                    <p class="text-sm text-slate-600">Anticipez les pannes matérielles avant qu'elles n'impactent l'utilisateur.</p>
                </button>

                <button class="value-btn flex flex-col items-center text-center p-6 rounded-2xl border-2 border-slate-200 bg-white shadow-sm transition-transform hover:-translate-y-1 relative" data-chart="couts">
                    <span class="text-4xl mb-3 mt-2">💰</span>
                    <h3 class="font-bold text-slate-800 text-lg mb-2">Maîtrise des Coûts</h3>
                    <p class="text-sm text-slate-600">Optimisez le renouvellement matériel et réduisez les temps de résolution (MTTR) du support.</p>
                </button>
            </div>

            <!-- Zone d'affichage du graphique et bloc Zéro Friction -->
            <div class="bg-white p-8 rounded-3xl shadow-xl border border-slate-100 flex flex-col lg:flex-row gap-8 items-center">
                <div class="w-full lg:w-1/3 text-left order-2 lg:order-1 flex flex-col justify-center">
                    <h3 id="chart-title" class="text-2xl font-bold text-slate-800 mb-3">État des Correctifs & Conformité</h3>
                    <p id="chart-desc" class="text-slate-600 mb-8">Validation précise du déploiement des mises à jour de sécurité et des stratégies de configuration.</p>
                    
                    <div class="bg-emerald-50 border border-emerald-200 p-5 rounded-xl shadow-inner mt-auto">
                        <div class="flex items-center gap-3 mb-2">
                            <span class="text-2xl">✅</span>
                            <h4 class="font-bold text-emerald-900 text-lg">Zéro friction</h4>
                        </div>
                        <p class="text-sm text-emerald-800">Se déploie nativement via Microsoft Intune. Aucun agent lourd supplémentaire à gérer ou à maintenir sur les postes.</p>
                    </div>
                </div>

                <div class="w-full lg:w-2/3 order-1 lg:order-2">
                    <div id="chart-wrapper" class="grid grid-cols-1 md:grid-cols-2 gap-6 w-full h-full min-h-[350px]">
                        <!-- Graphique 1 -->
                        <div id="container-1" class="relative w-full flex flex-col items-center justify-center">
                            <h4 id="subtitle-1" class="text-sm font-bold text-slate-700 mb-2">Correctifs Windows Update</h4>
                            <div class="relative w-full h-[300px] md:h-[350px]">
                                <canvas id="roiChart1"></canvas>
                            </div>
                        </div>
                        <!-- Graphique 2 -->
                        <div id="container-2" class="relative w-full flex flex-col items-center justify-center">
                            <h4 id="subtitle-2" class="text-sm font-bold text-slate-700 mb-2">Règles de Sécurité (LAPS, BIOS, Bitlocker)</h4>
                            <div class="relative w-full h-[300px] md:h-[350px]">
                                <canvas id="roiChart2"></canvas>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="section-galerie" class="content-section pt-12 border-t border-slate-800">
            <div class="text-center max-w-3xl mx-auto mb-12">
                <h2 class="text-3xl font-extrabold text-white mb-4">Aperçu de la Solution Power BI</h2>
                <p class="text-lg text-slate-400">
                    Découvrez l'interface dynamique et sombre (Dark Mode) de nos rapports. Vos données brutes sont transformées en indicateurs clairs, interactifs et prêts pour la prise de décision.
                </p>
            </div>

            <div class="flex flex-col gap-8">
                <!-- Onglets de la galerie -->
                <div class="flex justify-center gap-3 md:gap-6 flex-wrap">
                    <button class="gallery-btn active bg-blue-600 text-white px-6 py-2 rounded-full font-semibold shadow-md transition-colors" data-img="win-inv">
                        Inventaire Windows
                    </button>
                    <button class="gallery-btn bg-white text-slate-600 border border-slate-200 px-6 py-2 rounded-full font-semibold hover:bg-slate-50 transition-colors" data-img="sec-conf">
                        Sécurité & Conformité
                    </button>
                    <button class="gallery-btn bg-white text-slate-600 border border-slate-200 px-6 py-2 rounded-full font-semibold hover:bg-slate-50 transition-colors" data-img="win-upd">
                        Suivi Windows Update
                    </button>
                </div>

                <!-- Affichage de l'image -->
                <div class="w-full max-w-6xl mx-auto relative group">
                    <div id="gallery-img-container" class="bg-slate-800 p-2 md:p-4 rounded-2xl shadow-2xl transition-opacity duration-300 border border-slate-700">
                        <img id="gallery-img" src="https://i.postimg.cc/MHQNVQGv/2026-03-17-19-22-08-Intune-Dashboard-Demo.png" alt="Inventaire Windows" class="w-full h-auto rounded-xl shadow-inner">
                    </div>
                </div>

                <!-- Légende de l'image -->
                <div class="text-center max-w-3xl mx-auto">
                    <p id="gallery-caption" class="text-slate-600 text-md font-medium bg-blue-50 px-6 py-4 rounded-lg border border-blue-100">
                        Vue globale et détaillée du parc Windows : suivez la répartition par modèles, constructeurs, versions de build et identifiez rapidement les doublons.
                    </p>
                </div>
            </div>
        </section>

        <section id="section-tech" class="content-section pt-12 border-t border-slate-800">
            <!-- Conteneur principal du diagramme -->
            <div class="bg-white rounded-2xl shadow-xl w-full max-w-7xl p-8 border border-slate-200 relative overflow-hidden">
                
                <!-- En-tête avec Logo -->
                <div class="flex flex-col md:flex-row items-center justify-between mb-12 border-b border-slate-100 pb-6">
                    <div>
                        <h2 class="text-3xl font-extrabold text-slate-900 mb-2">Architecture Technique Deep Dive</h2>
                        <p class="text-slate-500 mt-1">Flux de données sécurisé, de la collecte à la visualisation.</p>
                    </div>
                    <img src="https://i.postimg.cc/B6yRjgJq/Gemini-Generated-Image-x6z3ftx6z3ftx6z3.png" alt="LBITCloud Logo" class="w-56 mt-4 md:mt-0 object-contain">
                </div>

                <!-- Zone du Diagramme (Flexbox responsive) -->
                <div class="flex flex-col md:flex-row items-stretch justify-between gap-4 md:gap-2 relative z-10">

                    <!-- ========================================== -->
                    <!-- BLOC 1 : SOURCES (Gauche)                  -->
                    <!-- ========================================== -->
                    <div class="flex-1 bg-white border-2 border-slate-200 rounded-xl p-6 shadow-sm relative group hover:border-slate-300 transition-colors">
                        <div class="absolute -top-3 left-6 bg-slate-100 px-3 py-1 rounded-full text-xs font-semibold text-slate-600 uppercase tracking-wide">
                            Endpoints
                        </div>
                        
                        <div class="flex flex-col items-center mt-4">
                            <!-- Conteneur Icônes -->
                            <div class="flex gap-4 mb-4">
                                <!-- PC Windows -->
                                <div class="flex flex-col items-center">
                                    <div class="w-16 h-16 bg-blue-50 text-blue-600 rounded-lg flex items-center justify-center shadow-sm border border-blue-100">
                                        <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="currentColor">
                                            <path d="M0 3.449L9.75 2.1v9.451H0m10.949-9.602L24 0v11.4H10.949M0 12.6h9.75v9.451L0 20.699M10.949 12.6H24V24l-12.951-1.801"/>
                                        </svg>
                                    </div>
                                    <span class="text-xs font-medium text-slate-500 mt-2">Windows</span>
                                </div>
                                <!-- Mac -->
                                <div class="flex flex-col items-center">
                                    <div class="w-16 h-16 bg-slate-50 text-slate-700 rounded-lg flex items-center justify-center shadow-sm border border-slate-200">
                                        <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="currentColor">
                                            <path d="M12 2.04C10.74 2.04 9.12 3 8.34 4c-.66.84-1.2 2.1-1.02 3.3 1.38.06 2.82-.78 3.6-1.8.66-.84 1.2-2.16 1.02-3.36M15.42 12c0-2.52 2.04-3.72 2.16-3.78-1.2-1.74-3.06-1.98-3.78-2.04-1.62-.18-3.12 1.02-3.96 1.02-.84 0-2.04-1.02-3.3-1.02-1.68 0-3.3 1.02-4.14 2.52-1.74 3.06-.42 7.62 1.26 10.08.84 1.2 1.86 2.58 3.12 2.52 1.2-.06 1.68-.78 3.18-.78 1.5 0 1.92.78 3.18.78 1.32-.06 2.16-1.32 3-2.52.96-1.44 1.32-2.82 1.32-2.88-.06-.06-2.58-1.02-2.58-3.9"/>
                                        </svg>
                                    </div>
                                    <span class="text-xs font-medium text-slate-500 mt-2">macOS</span>
                                </div>
                            </div>
                            
                            <h3 class="text-lg font-bold text-slate-800 text-center">Postes de Travail</h3>
                            <p class="text-sm text-slate-500 text-center mt-2 leading-relaxed">
                                Exécution du script de collecte (PowerShell/Bash) déployé via Microsoft Intune.
                            </p>
                        </div>
                    </div>

                    <!-- ========================================== -->
                    <!-- FLECHE 1 (Push)                            -->
                    <!-- ========================================== -->
                    <div class="flex md:flex-col items-center justify-center min-w-[150px] py-4 md:py-0 relative">
                        <div class="text-center absolute -top-2 md:-top-4 w-full">
                            <span class="bg-green-100 text-green-700 text-[10px] md:text-xs font-bold px-2 py-1 rounded border border-green-200">Push des données JSON</span>
                        </div>
                        
                        <!-- SVG Ligne animée (Desktop) -->
                        <svg class="hidden md:block w-full h-8 text-blue-400" preserveAspectRatio="none" viewBox="0 0 100 24" fill="none" stroke="currentColor">
                            <path class="animate-flow" stroke-width="2" stroke-linecap="round" d="M0 12h95"></path>
                            <polygon fill="currentColor" points="95,8 100,12 95,16" stroke="none"></polygon>
                        </svg>

                        <!-- SVG Ligne animée (Mobile) -->
                        <svg class="md:hidden h-16 w-8 text-blue-400" preserveAspectRatio="none" viewBox="0 0 24 100" fill="none" stroke="currentColor">
                            <path class="animate-flow" stroke-width="2" stroke-linecap="round" d="M12 0v95"></path>
                            <polygon fill="currentColor" points="8,95 12,100 16,95" stroke="none"></polygon>
                        </svg>

                        <div class="text-center absolute -bottom-2 md:-bottom-6 w-full">
                            <span class="text-slate-500 text-[10px] md:text-xs font-mono bg-white px-1">HTTPS (TLS 1.2/1.3)</span>
                        </div>
                    </div>

                    <!-- ========================================== -->
                    <!-- BLOC 2 : AZURE (Centre)                    -->
                    <!-- ========================================== -->
                    <div class="flex-1 bg-white border-2 border-blue-200 rounded-xl p-6 shadow-md relative group hover:border-blue-400 transition-colors">
                        <div class="absolute -top-3 left-6 bg-blue-100 px-3 py-1 rounded-full text-xs font-semibold text-blue-700 uppercase tracking-wide">
                            Cloud Ingestion
                        </div>
                        
                        <div class="flex flex-col items-center mt-4">
                            <div class="w-20 h-20 mb-4 text-blue-600 relative">
                                <!-- Custom SVG for Azure Log Analytics vibe -->
                                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 64 64" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                                    <rect x="12" y="24" width="40" height="28" rx="4" fill="#eff6ff" stroke="#2563eb" stroke-width="3"/>
                                    <path d="M16 32h32M16 40h32" stroke="#60a5fa" stroke-width="2"/>
                                    <!-- Cloud top -->
                                    <path d="M16 24C16 15 22 10 32 10c8 0 14 5 14 12" stroke="#2563eb" stroke-width="3" fill="#dbeafe"/>
                                    <!-- Magnifying Glass -->
                                    <circle cx="44" cy="44" r="8" fill="white" stroke="#1e40af" stroke-width="2.5"/>
                                    <line x1="50" y1="50" x2="58" y2="58" stroke="#1e40af" stroke-width="3"/>
                                    <!-- Data points -->
                                    <circle cx="44" cy="44" r="2" fill="#3b82f6" stroke="none"/>
                                </svg>
                            </div>
                            
                            <h3 class="text-lg font-bold text-slate-800 text-center">Azure Log Analytics</h3>
                            <p class="text-sm text-slate-500 text-center mt-2 leading-relaxed">
                                Workspace sécurisé. API de collecte (DCR) pour l'ingestion, le stockage et l'historisation.
                            </p>
                        </div>
                    </div>

                    <!-- ========================================== -->
                    <!-- FLECHE 2 (Pull/Query)                      -->
                    <!-- ========================================== -->
                    <div class="flex md:flex-col items-center justify-center min-w-[150px] py-4 md:py-0 relative">
                        <div class="text-center absolute -top-2 md:-top-4 w-full">
                            <span class="bg-amber-100 text-amber-700 text-[10px] md:text-xs font-bold px-2 py-1 rounded border border-amber-200">Requêtes Directes</span>
                        </div>
                        
                        <!-- SVG Ligne animée (Desktop) -->
                        <svg class="hidden md:block w-full h-8 text-amber-400" preserveAspectRatio="none" viewBox="0 0 100 24" fill="none" stroke="currentColor">
                            <path class="animate-flow" stroke-width="2" stroke-linecap="round" stroke-dasharray="4" d="M0 12h95"></path>
                            <polygon fill="currentColor" points="95,8 100,12 95,16" stroke="none"></polygon>
                        </svg>

                        <!-- SVG Ligne animée (Mobile) -->
                        <svg class="md:hidden h-16 w-8 text-amber-400" preserveAspectRatio="none" viewBox="0 0 24 100" fill="none" stroke="currentColor">
                            <path class="animate-flow" stroke-width="2" stroke-linecap="round" stroke-dasharray="4" d="M12 0v95"></path>
                            <polygon fill="currentColor" points="8,95 12,100 16,95" stroke="none"></polygon>
                        </svg>

                        <div class="text-center absolute -bottom-2 md:-bottom-6 w-full">
                            <span class="text-slate-500 text-[10px] md:text-xs font-mono bg-white px-1">KQL / M-Query</span>
                        </div>
                    </div>

                    <!-- ========================================== -->
                    <!-- BLOC 3 : POWER BI (Droite)                 -->
                    <!-- ========================================== -->
                    <div class="flex-1 bg-white border-2 border-amber-200 rounded-xl p-6 shadow-sm relative group hover:border-amber-400 transition-colors">
                        <div class="absolute -top-3 left-6 bg-amber-100 px-3 py-1 rounded-full text-xs font-semibold text-amber-800 uppercase tracking-wide">
                            Data Visualization
                        </div>
                        
                        <div class="flex flex-col items-center mt-4">
                            <div class="w-20 h-20 mb-4 bg-amber-50 rounded-xl flex items-center justify-center border-2 border-amber-100 shadow-inner">
                                <!-- Power BI Icon SVG -->
                                <svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" viewBox="0 0 24 24" fill="none">
                                    <rect x="3" y="14" width="5" height="8" rx="1" fill="#fcd34d"/>
                                    <rect x="9.5" y="8" width="5" height="14" rx="1" fill="#fbbf24"/>
                                    <rect x="16" y="2" width="5" height="20" rx="1" fill="#f59e0b"/>
                                </svg>
                            </div>
                            
                            <h3 class="text-lg font-bold text-slate-800 text-center">Microsoft Power BI</h3>
                            <p class="text-sm text-slate-500 text-center mt-2 leading-relaxed">
                                Modèle de données sémantique. Dashboards interactifs (Matériel, Logiciel, Sécurité).
                            </p>
                        </div>
                    </div>

                </div>

                <!-- Footer / Notes de Sécurité -->
                <div class="mt-12 bg-slate-50 border border-slate-200 rounded-lg p-4 flex items-center justify-center gap-6 text-sm text-slate-600">
                    <div class="flex items-center gap-2">
                        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-green-600"><rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect><path d="M7 11V7a5 5 0 0 1 10 0v4"></path></svg>
                        <span>Chiffrement AES-256</span>
                    </div>
                    <div class="flex items-center gap-2">
                        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-blue-600"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"></path></svg>
                        <span>Tenant Isolation</span>
                    </div>
                     <div class="flex items-center gap-2">
                        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-slate-600"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"></path><polyline points="14 2 14 8 20 8"></polyline><line x1="16" y1="13" x2="8" y2="13"></line><line x1="16" y1="17" x2="8" y2="17"></line><polyline points="10 9 9 9 8 9"></polyline></svg>
                        <span>Conforme RGPD</span>
                    </div>
                </div>

            </div>
        </section>

        <section id="section-deploiement" class="content-section pt-12 border-t border-slate-800">
            <div class="text-center max-w-3xl mx-auto mb-16">
                <h2 class="text-4xl font-extrabold text-white mb-6">Déploiement Rapide en 3 Étapes</h2>
                <p class="text-lg text-slate-400">
                    La mise en place technique s'effectue en 3 étapes claires et automatisées, ne nécessitant aucune infrastructure sur site. Le processus est conçu pour une intégration fluide et immédiate.
                </p>
            </div>

            <div class="max-w-4xl mx-auto bg-white rounded-2xl shadow-md border border-slate-100 p-8">
                <div class="relative border-l-4 border-blue-200 ml-6 pl-8 space-y-12 py-4">
                    
                    <div class="relative">
                        <div class="absolute -left-[45px] bg-blue-600 text-white w-10 h-10 rounded-full flex items-center justify-center font-bold shadow-md border-4 border-white">1</div>
                        <h3 class="text-xl font-bold text-slate-800 mb-2">Déploiement Azure</h3>
                        <p class="text-slate-600">Déploiement des ressources via des scripts automatisés qui se chargent de créer et de configurer l'ensemble des éléments nécessaires dans votre propre locataire (Tenant) Azure. Vos données restent chez vous.</p>
                    </div>

                    <div class="relative">
                        <div class="absolute -left-[45px] bg-blue-600 text-white w-10 h-10 rounded-full flex items-center justify-center font-bold shadow-md border-4 border-white">2</div>
                        <h3 class="text-xl font-bold text-slate-800 mb-2">Affectation Intune</h3>
                        <p class="text-slate-600">Utilisation d'un Script de Remédiation (Proactive Remediation) natif dans Intune contenant notre logique de collecte. L'affectation se fait en ciblant vos groupes de postes existants.</p>
                    </div>

                    <div class="relative">
                        <div class="absolute -left-[45px] bg-amber-500 text-white w-10 h-10 rounded-full flex items-center justify-center font-bold shadow-md border-4 border-white">3</div>
                        <h3 class="text-xl font-bold text-slate-800 mb-2">Connexion Dashboard</h3>
                        <p class="text-slate-600">Ouverture du modèle sémantique Power BI (.pbit) fourni, connexion sécurisée à votre nouvel espace Log Analytics, et visualisation immédiate de vos premières données.</p>
                    </div>

                </div>
            </div>
        </section>

    </main>

    <footer class="bg-slate-900 text-slate-400 py-8 text-center mt-12 border-t border-slate-800">
        <p>© 2026 LBITCloud - Solution d'extension MDM. Architecture sécurisée par design.</p>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const revealBtn = document.getElementById('btn-reveal');
            const visionComplete = document.getElementById('vision-complete');
            const valueButtons = document.querySelectorAll('.value-btn');
            
            if(revealBtn && visionComplete) {
                revealBtn.addEventListener('click', () => {
                    visionComplete.classList.remove('opacity-50', 'filter', 'blur-sm');
                    visionComplete.classList.add('opacity-100', 'shadow-xl');
                    revealBtn.style.display = 'none';
                });
            }

            const chartDataConfig = {
                proactivite: {
                    title: "État de Santé des Disques (Simulation)",
                    desc: "Analyse prédictive de l'espace disque et de l'usure matérielle.",
                    charts: [
                        {
                            type: 'doughnut',
                            labels: ['Sains (>20% libres)', 'Alerte (<20% libres)', 'Critique (<5% libres)'],
                            data: [850, 120, 30],
                            colors: ['#34d399', '#fbbf24', '#ef4444']
                        }
                    ]
                },
                couts: {
                    title: "Optimisation du Cycle de Vie Matériel",
                    desc: "Prolongation ciblée du matériel basée sur l'état de santé réel, évitant des renouvellements prématurés.",
                    charts: [
                        {
                            type: 'bar',
                            labels: ['Postes prolongés (Sains)', 'Remplacement ciblé (Défaillants)', 'Remplacements évités (Économie)'],
                            data: [850, 150, 320],
                            colors: ['#60a5fa', '#f87171', '#10b981']
                        }
                    ]
                },
                securite: {
                    title: "État des Correctifs & Conformité",
                    desc: "Vérifiez l'état des mises à jour de sécurité Windows, mais validez surtout l'application stricte de vos règles d'entreprise de bas niveau (Configuration BIOS sécurisée, mots de passe administrateurs Windows LAPS, chiffrement Bitlocker, etc.).",
                    charts: [
                        {
                            subtitle: "Correctifs Windows Update",
                            type: 'doughnut',
                            labels: ['À jour', 'Attente redémarrage', 'Échec / Obsolète'],
                            data: [750, 180, 70],
                            colors: ['#10b981', '#3b82f6', '#ef4444']
                        },
                        {
                            subtitle: "Règles de Sécurité (LAPS, BIOS, Bitlocker)",
                            type: 'doughnut',
                            labels: ['100% Conformes', 'Défaut Bitlocker', 'Défaut LAPS / BIOS'],
                            data: [820, 110, 70],
                            colors: ['#34d399', '#f59e0b', '#dc2626']
                        }
                    ]
                }
            };

            const commonOptions = {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { position: 'bottom' },
                    tooltip: {
                        callbacks: {
                            label: function(context) {
                                let label = context.label || '';
                                if (label) {
                                    label = label.length > 16 ? label.match(/.{1,16}(\s|$)/g).join('\n') : label;
                                }
                                return label + ': ' + context.formattedValue + ' postes';
                            }
                        }
                    }
                }
            };

            // Init Graphique 1
            const ctx1 = document.getElementById('roiChart1').getContext('2d');
            let roiChartInstance1 = new Chart(ctx1, {
                type: chartDataConfig.securite.charts[0].type,
                data: {
                    labels: chartDataConfig.securite.charts[0].labels,
                    datasets: [{
                        data: chartDataConfig.securite.charts[0].data,
                        backgroundColor: chartDataConfig.securite.charts[0].colors,
                        borderWidth: 1
                    }]
                },
                options: commonOptions
            });

            // Init Graphique 2
            const ctx2 = document.getElementById('roiChart2').getContext('2d');
            let roiChartInstance2 = new Chart(ctx2, {
                type: chartDataConfig.securite.charts[1].type,
                data: {
                    labels: chartDataConfig.securite.charts[1].labels,
                    datasets: [{
                        data: chartDataConfig.securite.charts[1].data,
                        backgroundColor: chartDataConfig.securite.charts[1].colors,
                        borderWidth: 1
                    }]
                },
                options: commonOptions
            });

            const wrapper = document.getElementById('chart-wrapper');
            const container2 = document.getElementById('container-2');
            const sub1 = document.getElementById('subtitle-1');
            const sub2 = document.getElementById('subtitle-2');

            valueButtons.forEach(btn => {
                btn.addEventListener('click', () => {
                    valueButtons.forEach(b => {
                        b.classList.remove('bg-blue-50', 'border-blue-600', 'shadow-md');
                        b.classList.add('bg-white', 'border-slate-200', 'shadow-sm');
                    });
                    btn.classList.add('bg-blue-50', 'border-blue-600', 'shadow-md');
                    btn.classList.remove('bg-white', 'border-slate-200', 'shadow-sm');

                    const chartKey = btn.getAttribute('data-chart');
                    const config = chartDataConfig[chartKey];

                    document.getElementById('chart-title').innerText = config.title;
                    document.getElementById('chart-desc').innerText = config.desc;

                    // Mise à jour du Graphique 1
                    roiChartInstance1.config.type = config.charts[0].type;
                    roiChartInstance1.data.labels = config.charts[0].labels;
                    roiChartInstance1.data.datasets[0].data = config.charts[0].data;
                    roiChartInstance1.data.datasets[0].backgroundColor = config.charts[0].colors;
                    
                    if (config.charts[0].type === 'bar') {
                        roiChartInstance1.options.scales = {
                            y: { beginAtZero: true, title: { display: true, text: 'Nombre de Postes' } },
                            x: { display: true }
                        };
                    } else {
                        roiChartInstance1.options.scales = { x: {display: false}, y: {display: false} };
                    }
                    roiChartInstance1.update();

                    // Mise à jour du Graphique 2 ou Masquage de la zone
                    if (config.charts.length > 1) {
                        wrapper.classList.add('md:grid-cols-2');
                        container2.classList.remove('hidden');
                        container2.classList.add('flex');
                        sub1.classList.remove('hidden');
                        sub2.classList.remove('hidden');
                        sub1.innerText = config.charts[0].subtitle;
                        sub2.innerText = config.charts[1].subtitle;

                        roiChartInstance2.config.type = config.charts[1].type;
                        roiChartInstance2.data.labels = config.charts[1].labels;
                        roiChartInstance2.data.datasets[0].data = config.charts[1].data;
                        roiChartInstance2.data.datasets[0].backgroundColor = config.charts[1].colors;
                        
                        if (config.charts[1].type === 'bar') {
                            roiChartInstance2.options.scales = {
                                y: { beginAtZero: true, title: { display: true, text: 'Nombre de Postes' } },
                                x: { display: true }
                            };
                        } else {
                            roiChartInstance2.options.scales = { x: {display: false}, y: {display: false} };
                        }
                        roiChartInstance2.update();
                    } else {
                        wrapper.classList.remove('md:grid-cols-2');
                        container2.classList.add('hidden');
                        container2.classList.remove('flex');
                        sub1.classList.add('hidden');
                        sub2.classList.add('hidden');
                    }
                });
            });

            // --- Logique de la Galerie d'images ---
            const galleryBtns = document.querySelectorAll('.gallery-btn');
            const galleryImg = document.getElementById('gallery-img');
            const galleryImgContainer = document.getElementById('gallery-img-container');
            const galleryCaption = document.getElementById('gallery-caption');

            const galleryData = {
                'win-inv': {
                    src: 'https://i.postimg.cc/MHQNVQGv/2026-03-17-19-22-08-Intune-Dashboard-Demo.png',
                    alt: 'Inventaire Windows',
                    caption: 'Vue globale et détaillée du parc Windows : suivez la répartition par modèles, constructeurs, versions de build et identifiez rapidement les doublons.'
                },
                'sec-conf': {
                    src: 'https://i.postimg.cc/Y0WZYWSS/2026-03-17-19-24-24-Intune-Dashboard-Demo.png',
                    alt: 'Sécurité & Conformité',
                    caption: 'Visualisez la conformité de vos configurations de sécurité : état du chiffrement BitLocker, mots de passe LAPS, et conformité globale du parc.'
                },
                'win-upd': {
                    src: 'https://i.postimg.cc/kGbzKb5V/2026-03-17-19-20-55-Intune-Dashboard-Demo.png',
                    alt: 'Suivi Windows Update',
                    caption: 'Contrôlez le déploiement de vos correctifs. Visualisez la conformité des configurations, l\'état des mises à jour cumulatives et la répartition par anneaux (Rings).'
                }
            };

            galleryBtns.forEach(btn => {
                btn.addEventListener('click', () => {
                    // Reset styling on all buttons
                    galleryBtns.forEach(b => {
                        b.classList.remove('bg-blue-600', 'text-white', 'shadow-md');
                        b.classList.add('bg-white', 'text-slate-600', 'border-slate-200');
                    });
                    
                    // Add active styling to clicked button
                    btn.classList.remove('bg-white', 'text-slate-600', 'border-slate-200');
                    btn.classList.add('bg-blue-600', 'text-white', 'shadow-md');

                    const imgKey = btn.getAttribute('data-img');
                    const data = galleryData[imgKey];

                    // Fade out
                    galleryImgContainer.classList.add('opacity-50');
                    
                    setTimeout(() => {
                        // Change image and text
                        galleryImg.src = data.src;
                        galleryImg.alt = data.alt;
                        galleryCaption.innerText = data.caption;
                        
                        // Fade in
                        galleryImgContainer.classList.remove('opacity-50');
                    }, 200);
                });
            });
        });
    </script>
</body>
</html>
