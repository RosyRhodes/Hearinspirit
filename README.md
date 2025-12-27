<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rosy†Rhodes | Sonic Ecosystem Analysis</title>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Chart.js -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Syne:wght@400;700;800&display=swap" rel="stylesheet">

    <!-- Palette Configuration -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        'mono': ['"Space Mono"', 'monospace'],
                        'display': ['"Syne"', 'sans-serif'],
                    },
                    colors: {
                        'rr-bg': '#EBEAE4',       /* Warm Light Grey/Sand */
                        'rr-dark': '#2A2A28',     /* Soft Charcoal */
                        'rr-accent': '#C68E8B',   /* Muted Rose */
                        'rr-green': '#8FA38F',    /* Sage/Organic */
                        'rr-card': '#F5F5F0',     /* Lighter Card BG */
                        'rr-border': '#D1D1C7',
                    }
                }
            }
        }
    </script>

    <style>
        body {
            background-color: #EBEAE4;
            color: #2A2A28;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            height: 350px;
            max-height: 400px;
        }
        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #EBEAE4; 
        }
        ::-webkit-scrollbar-thumb {
            background: #D1D1C7; 
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #C68E8B; 
        }
        .active-release {
            border-left: 4px solid #C68E8B;
            background-color: #ffffff;
        }
    </style>

    <!-- Chosen Palette: "Organic Ritual" - Warm neutrals (#EBEAE4) with Muted Rose (#C68E8B) and Sage (#8FA38F) accents to reflect the "Electronic + Organic" theme. -->
    
    <!-- Application Structure Plan:
         1. Header: Artist Identity & Mission Statement.
         2. Interactive Dashboard (The Core): 
            - Left Col: "Sonic Signature" Radar Chart (Dynamic). Visualizes the "Vibe" (Energy, Ritual, Organic, Tech) of the selected release.
            - Right Col: "The Catalog" List. Clickable timeline items that drive the chart.
         3. Ecosystem Analysis: 
            - "Genre Alchemy" Doughnut Chart. Shows the distribution of tags (Solfeggio, DnB, etc.).
         4. Textual Context: "The Signal" (Bio) broken into readable pillars.
         
         Logic: Users explore the "sound" by clicking tracks. The Radar chart immediately reveals the shift from "Ambient" (2015) to "Bass" (2023).
    -->

    <!-- Visualization & Content Choices:
         - Radar Chart: Best for showing the *shape* of a sound profile (multivariate data: Energy, Organic-ness, Ritual-factor). Confirms NO SVG.
         - Doughnut Chart: To visualize the "Tag" distribution.
         - Interaction: List click -> Chart Update. Simple, effective exploration.
    -->
    
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->

</head>
<body class="font-mono text-rr-dark antialiased overflow-x-hidden selection:bg-rr-accent selection:text-white">

    <!-- Navigation / Header -->
    <header class="w-full border-b border-rr-border bg-rr-bg/95 backdrop-blur sticky top-0 z-50">
        <div class="max-w-6xl mx-auto px-4 py-4 flex justify-between items-center">
            <div>
                <h1 class="font-display font-bold text-2xl tracking-tight">ROSY†RHODES</h1>
                <p class="text-xs uppercase tracking-widest text-rr-accent">Roadside Recording // HearinSpirit</p>
            </div>
            <div class="hidden md:flex space-x-6 text-sm">
                <a href="#dashboard" class="hover:text-rr-accent transition-colors">Data</a>
                <a href="#catalog" class="hover:text-rr-accent transition-colors">Catalog</a>
                <a href="#signal" class="hover:text-rr-accent transition-colors">Signal</a>
            </div>
            <div class="text-xl">☊</div>
        </div>
    </header>

    <!-- Main Content Wrapper -->
    <main class="max-w-6xl mx-auto px-4 py-8 space-y-16">

        <!-- Intro Section -->
        <section class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
            <div class="space-y-6">
                <div class="inline-block px-3 py-1 border border-rr-dark rounded-full text-xs uppercase font-bold">New Ecosystem Analysis</div>
                <h2 class="font-display text-5xl md:text-6xl font-bold leading-tight">
                    Tuning Sound <br>
                    <span class="text-rr-accent italic">Into Ritual.</span>
                </h2>
                <p class="text-lg leading-relaxed opacity-80">
                    A genre-fluid producer tuning modern electronic and organic sound into accessibility-first sessions. From Solfeggio centers to 7-string textures, we map the arc from ambient experiments to transformational bass.
                </p>
                <div class="flex items-center space-x-4 pt-4">
                    <button onclick="scrollToCatalog()" class="bg-rr-dark text-rr-bg px-6 py-3 font-bold hover:bg-rr-accent transition-colors">
                        Explore Catalog
                    </button>
                    <div class="text-2xl opacity-50">
                        † Δ ⏀
                    </div>
                </div>
            </div>
            <div class="bg-rr-card p-6 border border-rr-border rounded-lg shadow-sm">
                <div class="border-b border-rr-border pb-4 mb-4">
                    <h3 class="font-bold uppercase tracking-widest text-sm">Current Frequency</h3>
                    <p class="text-xs text-rr-accent mt-1">System Status: ONLINE</p>
                </div>
                <div class="grid grid-cols-2 gap-4 text-center">
                    <div class="p-4 bg-rr-bg rounded">
                        <div class="text-3xl font-display font-bold">417<span class="text-sm font-mono font-normal">Hz</span></div>
                        <div class="text-xs uppercase mt-1 opacity-60">Release / Transform</div>
                    </div>
                    <div class="p-4 bg-rr-bg rounded">
                        <div class="text-3xl font-display font-bold">11:11</div>
                        <div class="text-xs uppercase mt-1 opacity-60">Numerology</div>
                    </div>
                    <div class="p-4 bg-rr-bg rounded col-span-2">
                        <div class="text-xl font-display font-bold">Mobile Studio</div>
                        <div class="text-xs uppercase mt-1 opacity-60">Accessibility First</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- DASHBOARD SECTION -->
        <section id="dashboard" class="scroll-mt-24">
            <div class="mb-8">
                <h3 class="font-display text-3xl font-bold mb-2">Sonic Profile Analysis</h3>
                <p class="text-sm max-w-2xl opacity-75">
                    Interactive visualization of the discography. Select a release from the list to analyze its specific "Vibe Architecture"—mapping the balance between Organic textures, Electronic drive, Ritualistic atmosphere, and Kinetic Energy.
                </p>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
                
                <!-- LEFT COL: The Chart (Sticky) -->
                <div class="lg:col-span-5 lg:sticky lg:top-24 h-fit space-y-6">
                    <div class="bg-white p-6 rounded-xl border border-rr-border shadow-sm">
                        <div class="flex justify-between items-center mb-4">
                            <h4 id="chart-title" class="font-bold uppercase tracking-wider text-sm">Aggregate Profile</h4>
                            <span class="text-xs text-rr-accent font-mono">Radar Analysis</span>
                        </div>
                        
                        <!-- Chart Container -->
                        <div class="chart-container">
                            <canvas id="radarChart"></canvas>
                        </div>

                        <div id="chart-caption" class="text-xs text-center mt-4 opacity-60 font-mono">
                            Select a track to view specific parameters.
                        </div>
                    </div>

                    <!-- Mini Stat Box (Dynamic) -->
                    <div class="grid grid-cols-2 gap-4">
                        <div class="bg-rr-card p-4 rounded border border-rr-border text-center">
                            <div class="text-xs uppercase opacity-50">Primary Genre</div>
                            <div id="dynamic-genre" class="font-bold text-rr-accent mt-1">Multi-Genre</div>
                        </div>
                        <div class="bg-rr-card p-4 rounded border border-rr-border text-center">
                            <div class="text-xs uppercase opacity-50">Era</div>
                            <div id="dynamic-year" class="font-bold mt-1">2015–2023</div>
                        </div>
                    </div>
                </div>

                <!-- RIGHT COL: The List -->
                <div id="catalog" class="lg:col-span-7 space-y-4">
                    <div class="flex justify-between items-end border-b border-rr-border pb-2 mb-4">
                        <span class="text-xs uppercase font-bold text-rr-dark">Release Log</span>
                        <span class="text-xs font-mono opacity-50">5 Items Found</span>
                    </div>

                    <!-- Container for generated catalog items -->
                    <div id="catalog-list" class="space-y-3">
                        <!-- JS will populate this -->
                    </div>
                </div>
            </div>
        </section>

        <!-- TAG & TEXT ANALYSIS -->
        <section id="signal" class="grid grid-cols-1 md:grid-cols-2 gap-12 pt-12 border-t border-rr-border">
            
            <!-- Text Content -->
            <div class="space-y-8 order-2 md:order-1">
                <h3 class="font-display text-3xl font-bold">The Signal Transmissions</h3>
                <p class="text-sm opacity-70 italic mb-4">
                    "Sound healing that still slaps on a good system."
                </p>
                
                <div class="space-y-6">
                    <div class="group">
                        <h4 class="font-bold text-lg mb-2 flex items-center">
                            <span class="text-rr-accent mr-2">01.</span> Origin Point
                        </h4>
                        <p class="text-sm leading-relaxed opacity-80 pl-8 border-l border-rr-border group-hover:border-rr-accent transition-colors">
                            The HearinSpirit (2015–2023) arc maps the journey. It began with "Blinking Out Algol"—lo-ambient rituals and early glyph play. This was the seed of the philosophy: sound as a tool for grounding and connection.
                        </p>
                    </div>

                    <div class="group">
                        <h4 class="font-bold text-lg mb-2 flex items-center">
                            <span class="text-rr-accent mr-2">02.</span> Organic Engines
                        </h4>
                        <p class="text-sm leading-relaxed opacity-80 pl-8 border-l border-rr-border group-hover:border-rr-accent transition-colors">
                            Systems music for bodies. The transition into "Organic Engines" and "Seeds of Drus" introduced movement-minded arrangements. Field-recorded breath, pulse, and 7-string textures began to merge with electronic sequencing.
                        </p>
                    </div>

                    <div class="group">
                        <h4 class="font-bold text-lg mb-2 flex items-center">
                            <span class="text-rr-accent mr-2">03.</span> Frequency Awareness
                        </h4>
                        <p class="text-sm leading-relaxed opacity-80 pl-8 border-l border-rr-border group-hover:border-rr-accent transition-colors">
                            Modern releases like "Pisces (417 Hz)" and "Battery Killer 11:11" represent the current evolution: Frequency-aware releases. Using specific tunings (Solfeggio) to target intuition and release, riding on top of halftime drums and transformational bass.
                        </p>
                    </div>
                </div>
            </div>

            <!-- Tag Visualization -->
            <div class="order-1 md:order-2 bg-white p-6 rounded-xl border border-rr-border shadow-sm h-fit">
                <h4 class="font-bold uppercase tracking-wider text-sm mb-6 text-center">Ecosystem Composition</h4>
                
                <!-- Chart Container -->
                <div class="chart-container" style="height: 300px;">
                    <canvas id="doughnutChart"></canvas>
                </div>

                <div class="mt-8 flex flex-wrap gap-2 justify-center">
                    <!-- Interactive Tag Cloud (Static for now, but visually connected) -->
                    <span class="px-2 py-1 bg-rr-card text-xs border border-rr-border rounded hover:bg-rr-accent hover:text-white transition cursor-default">Transformational Bass</span>
                    <span class="px-2 py-1 bg-rr-card text-xs border border-rr-border rounded hover:bg-rr-accent hover:text-white transition cursor-default">417 Hz</span>
                    <span class="px-2 py-1 bg-rr-card text-xs border border-rr-border rounded hover:bg-rr-accent hover:text-white transition cursor-default">Field Recording</span>
                    <span class="px-2 py-1 bg-rr-card text-xs border border-rr-border rounded hover:bg-rr-accent hover:text-white transition cursor-default">Ritual</span>
                    <span class="px-2 py-1 bg-rr-card text-xs border border-rr-border rounded hover:bg-rr-accent hover:text-white transition cursor-default">Ambient</span>
                </div>
            </div>
        </section>

        <!-- CTA / Footer -->
        <section class="bg-rr-dark text-rr-bg rounded-xl p-8 md:p-12 text-center space-y-6">
            <h2 class="font-display text-3xl md:text-4xl font-bold">Raise The Collective Vibe.</h2>
            <p class="max-w-xl mx-auto opacity-70">
                Stream the catalog on Bandcamp, SoundCloud, Spotify, or YouTube. <br>
                Co-create from anywhere or book an on-site session.
            </p>
            <div class="pt-4 flex justify-center space-x-4">
                <a href="https://playlist.link/hearinspirit" target="_blank" class="px-6 py-3 border border-rr-bg hover:bg-rr-accent hover:border-rr-accent hover:text-white transition-all rounded-sm uppercase text-sm font-bold tracking-widest">
                    Stream Catalog
                </a>
            </div>
            <div class="text-sm opacity-40 font-mono mt-8">
                Anchor-heart-cross. Breathe in. Press play.
            </div>
        </section>

    </main>

    <!-- Footer -->
    <footer class="text-center py-6 text-xs opacity-50 border-t border-rr-border mt-12">
        <p>&copy; 2025 Rosy Roadside Recording. Generated Interface.</p>
    </footer>

    <!-- LOGIC -->
    <script>
        // --- 1. DATA STORAGE ---
        // Data derived from the user provided JSON.
        // "Stats" are inferred values (0-10) to quantify the "Notes" and "Tags".
        // Energy: Kinetic/Danceability | Organic: Acoustic/Field Recs | Tech: Electronic/Synthesis | Ritual: Spiritual/Meditative Focus
        const ecosystemData = [
            {
                id: 1,
                year: "2023",
                title: "Battery Killer 11:11",
                notes: "Numerological symmetry, low-end devotion, eyes-closed dance floor.",
                tags: ["11:11", "Transformational Bass"],
                stats: { energy: 9, organic: 2, tech: 8, ritual: 7 },
                desc: "High-energy bass music designed for devotional movement."
            },
            {
                id: 2,
                year: "2023",
                title: "Pisces (417 Hz DnB Remix)",
                notes: "Intuition meets propulsion—417’s 'release/transform' riding halftime drums.",
                tags: ["417 Hz", "DnB", "Ecstatic-dance"],
                stats: { energy: 8, organic: 3, tech: 9, ritual: 8 },
                desc: "Drum and Bass rhythms tuned to healing frequencies."
            },
            {
                id: 3,
                year: "2022–2023",
                title: "Organic Engines I–III",
                notes: "Systems music for bodies—movement-minded arrangements, ritual semiotics.",
                tags: ["EDM/Healing", "Mobile Studio"],
                stats: { energy: 6, organic: 7, tech: 6, ritual: 8 },
                desc: "A trilogy of systems music designed to engage the body."
            },
            {
                id: 4,
                year: "2020",
                title: "Seeds of Drus",
                notes: "Organic engines warming up—field textures, breath, and pulse.",
                tags: ["Electro-organic", "Studio/Field"],
                stats: { energy: 4, organic: 10, tech: 4, ritual: 6 },
                desc: "Heavy use of field recordings, breath, and organic pulse."
            },
            {
                id: 5,
                year: "2015",
                title: "Hearin’Spirit Pt. 1",
                subtitle: "Blinking Out Algol",
                notes: "The seed. Lo-ambient rituals, early glyph play, first anchor-heart-cross sightings.",
                tags: ["Solfeggio", "Ambient", "Bandcamp"],
                stats: { energy: 2, organic: 6, tech: 3, ritual: 10 },
                desc: "The ambient origin point. Pure ritual and atmosphere."
            }
        ];

        // --- 2. CHART INITIALIZATION ---
        let radarChartInstance = null;
        let doughnutChartInstance = null;

        document.addEventListener('DOMContentLoaded', () => {
            initCatalogList();
            initRadarChart();
            initDoughnutChart();
            
            // Select the most recent release by default
            selectRelease(0);
        });

        function scrollToCatalog() {
            document.getElementById('dashboard').scrollIntoView({ behavior: 'smooth' });
        }

        // --- 3. DOM MANIPULATION ---

        function initCatalogList() {
            const listContainer = document.getElementById('catalog-list');
            
            ecosystemData.forEach((item, index) => {
                const el = document.createElement('div');
                el.className = `p-4 rounded border border-rr-border hover:border-rr-accent cursor-pointer transition-all duration-300 release-item`;
                el.dataset.index = index;
                el.onclick = () => selectRelease(index);
                
                // Construct Tag HTML
                const tagsHtml = item.tags.map(tag => 
                    `<span class="text-[10px] uppercase border border-rr-dark/20 px-1 rounded text-rr-dark/60 mr-1">${tag}</span>`
                ).join('');

                el.innerHTML = `
                    <div class="flex justify-between items-start">
                        <div>
                            <div class="text-xs font-mono text-rr-accent mb-1">${item.year}</div>
                            <h4 class="font-bold text-lg font-display leading-tight">${item.title}</h4>
                            ${item.subtitle ? `<span class="text-sm opacity-80 block">${item.subtitle}</span>` : ''}
                        </div>
                        <div class="text-xl opacity-20">⏀</div>
                    </div>
                    <p class="text-sm opacity-70 mt-2 mb-3 line-clamp-2">${item.notes}</p>
                    <div class="flex flex-wrap gap-y-1">
                        ${tagsHtml}
                    </div>
                `;
                listContainer.appendChild(el);
            });
        }

        function selectRelease(index) {
            const item = ecosystemData[index];
            
            // Update UI Highlight
            document.querySelectorAll('.release-item').forEach(el => {
                el.classList.remove('active-release', 'shadow-md');
                if(parseInt(el.dataset.index) === index) {
                    el.classList.add('active-release', 'shadow-md');
                }
            });

            // Update Text Details
            document.getElementById('chart-title').innerText = item.title;
            document.getElementById('chart-caption').innerText = item.notes;
            document.getElementById('dynamic-genre').innerText = item.tags[0]; // Primary tag
            document.getElementById('dynamic-year').innerText = item.year;

            // Update Chart
            updateRadarChart(item.stats);
        }

        // --- 4. CHART.JS LOGIC ---

        function initRadarChart() {
            const ctx = document.getElementById('radarChart').getContext('2d');
            
            radarChartInstance = new Chart(ctx, {
                type: 'radar',
                data: {
                    labels: ['Kinetic Energy', 'Organic Texture', 'Ritual Focus', 'Tech/Synthesis'],
                    datasets: [{
                        label: 'Vibe Profile',
                        data: [0, 0, 0, 0], // Initial empty state
                        backgroundColor: 'rgba(198, 142, 139, 0.4)', // Accent color with opacity
                        borderColor: '#C68E8B',
                        pointBackgroundColor: '#2A2A28',
                        pointBorderColor: '#fff',
                        pointHoverBackgroundColor: '#fff',
                        pointHoverBorderColor: '#C68E8B',
                        borderWidth: 2
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        r: {
                            angleLines: { color: '#D1D1C7' },
                            grid: { color: '#EBEAE4' },
                            pointLabels: {
                                font: { family: '"Space Mono"', size: 11 },
                                color: '#2A2A28'
                            },
                            suggestedMin: 0,
                            suggestedMax: 10,
                            ticks: { display: false } // Hide numbers on axis for cleaner look
                        }
                    },
                    plugins: {
                        legend: { display: false },
                        tooltip: {
                            backgroundColor: '#2A2A28',
                            titleFont: { family: '"Syne"' },
                            bodyFont: { family: '"Space Mono"' },
                            callbacks: {
                                label: function(context) {
                                    return context.label + ': ' + context.raw + '/10';
                                }
                            }
                        }
                    }
                }
            });
        }

        function updateRadarChart(stats) {
            if(!radarChartInstance) return;
            
            const newData = [stats.energy, stats.organic, stats.ritual, stats.tech];
            radarChartInstance.data.datasets[0].data = newData;
            radarChartInstance.update();
        }

        function initDoughnutChart() {
            // Calculate Genre Counts
            const tagCounts = {};
            ecosystemData.forEach(item => {
                // Just taking the first tag as "Primary Genre" for simple visualization
                // Or we could count all tags. Let's count all unique tags.
                item.tags.forEach(tag => {
                    // Grouping similar tags for cleaner chart
                    let key = tag;
                    if(tag.includes("Bass") || tag.includes("DnB")) key = "Bass/DnB";
                    if(tag.includes("Ambient") || tag.includes("Solfeggio")) key = "Ambient/Healing";
                    if(tag.includes("Organic") || tag.includes("Field")) key = "Organic/Field";
                    
                    tagCounts[key] = (tagCounts[key] || 0) + 1;
                });
            });

            const ctx = document.getElementById('doughnutChart').getContext('2d');
            
            doughnutChartInstance = new Chart(ctx, {
                type: 'doughnut',
                data: {
                    labels: Object.keys(tagCounts),
                    datasets: [{
                        data: Object.values(tagCounts),
                        backgroundColor: [
                            '#C68E8B', // Accent
                            '#8FA38F', // Green
                            '#2A2A28', // Dark
                            '#D1D1C7', // Grey
                            '#EBEAE4'  // Light
                        ],
                        borderWidth: 0,
                        hoverOffset: 4
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    cutout: '65%',
                    plugins: {
                        legend: {
                            position: 'bottom',
                            labels: {
                                font: { family: '"Space Mono"', size: 10 },
                                usePointStyle: true,
                                padding: 20
                            }
                        }
                    }
                }
            });
        }
    </script>
</body>
</html>
