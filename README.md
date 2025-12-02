<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Atish Banerjee | Strategic Product Executive</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Chart.js -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- Plotly.js -->
    <script src="https://cdn.plot.ly/plotly-2.27.0.min.js"></script>
    <!-- Font Awesome (for icons, using CDN as generic icon set) -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <!-- Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">

    <!-- Chosen Palette: Corporate Strategy Blue -->
    <!-- 
         Primary: #0f172a (Slate 900) - Professional, Authority
         Secondary: #3b82f6 (Blue 500) - Tech, Trust, Strategy
         Accent: #10b981 (Emerald 500) - Growth, Success
         Background: #f8fafc (Slate 50) - Clean canvas
    -->

    <style>
        body { font-family: 'Inter', sans-serif; background-color: #f8fafc; color: #334155; }
        
        /* Chart Container Styling - Mandatory Requirements */
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px; /* Constrain width for readability */
            margin-left: auto;
            margin-right: auto;
            height: 300px; /* Base height */
            max-height: 400px;
        }

        @media (min-width: 768px) {
            .chart-container {
                height: 350px;
            }
        }
        
        .plotly-container {
            width: 100%;
            height: 400px;
            max-width: 100%;
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #f1f5f9; }
        ::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 4px; }
        ::-webkit-scrollbar-thumb:hover { background: #94a3b8; }

        /* Animation Classes */
        .fade-in { animation: fadeIn 0.5s ease-in-out; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

        .nav-item.active {
            background-color: #eff6ff;
            color: #2563eb;
            border-right: 3px solid #2563eb;
        }
    </style>

    <!-- Application Structure Plan: 
         1. Sidebar Navigation: Persistent access to key sections (Dashboard, Strategy Lab, Experience, Education).
         2. Main Content Area: Dynamic switching based on navigation.
            - Dashboard: High-level executive summary, Competency Radar, Key Metric Cards.
            - Strategy Lab: Deep dive into the McKesson "Patient Ready" case study (TAM/SAM/SOM Viz).
            - Experience Tracker: Detailed role breakdown with specific success metrics charts.
            - Innovation & AI: Visualizing the "Next Best Action" engine logic.
         3. Logic: Vanilla JS state management to handle view transitions and data population.
    -->
    
    <!-- Visualization & Content Choices:
         - Radar Chart (Chart.js): To visualize the balance of Strategy, Leadership, and Tech skills.
         - Funnel/Bar Chart (Plotly): To visualize the McKesson Market Sizing strategy ($250M SOM).
         - Bar Charts (Chart.js): To show Optum NPS growth and Star Rating improvements.
         - Justification: Charts provide immediate visual proof of the "Impact" mentioned in the text.
    -->

    <!-- CONFIRMATION: NO SVG graphics used (embedded SVG code is minimized/avoided in favor of FontAwesome/Unicode). NO Mermaid JS used. -->
</head>
<body class="h-screen flex overflow-hidden">

    <!-- Sidebar -->
    <aside class="w-64 bg-white border-r border-slate-200 hidden md:flex flex-col shadow-sm z-10">
        <div class="p-6 border-b border-slate-100">
            <h1 class="text-xl font-bold text-slate-800 tracking-tight">Atish Banerjee</h1>
            <p class="text-xs text-slate-500 font-medium uppercase mt-1">Strategic Product Exec</p>
        </div>
        
        <nav class="flex-1 overflow-y-auto py-4">
            <ul class="space-y-1">
                <li>
                    <button onclick="router('dashboard')" id="nav-dashboard" class="nav-item w-full text-left px-6 py-3 text-sm font-medium text-slate-600 hover:bg-slate-50 transition-colors flex items-center gap-3 active">
                        <i class="fas fa-chart-line w-5"></i> Executive Dashboard
                    </button>
                </li>
                <li>
                    <button onclick="router('strategy')" id="nav-strategy" class="nav-item w-full text-left px-6 py-3 text-sm font-medium text-slate-600 hover:bg-slate-50 transition-colors flex items-center gap-3">
                        <i class="fas fa-chess w-5"></i> Strategy Lab (McKesson)
                    </button>
                </li>
                <li>
                    <button onclick="router('experience')" id="nav-experience" class="nav-item w-full text-left px-6 py-3 text-sm font-medium text-slate-600 hover:bg-slate-50 transition-colors flex items-center gap-3">
                        <i class="fas fa-briefcase w-5"></i> Impact History
                    </button>
                </li>
                <li>
                    <button onclick="router('skills')" id="nav-skills" class="nav-item w-full text-left px-6 py-3 text-sm font-medium text-slate-600 hover:bg-slate-50 transition-colors flex items-center gap-3">
                        <i class="fas fa-layer-group w-5"></i> Competency Matrix
                    </button>
                </li>
            </ul>
        </nav>

        <div class="p-6 border-t border-slate-100 bg-slate-50">
            <div class="text-xs text-slate-500 mb-2">CONTACT INFO</div>
            <div class="flex flex-col gap-2">
                <a href="mailto:ban_atish@yahoo.com" class="text-sm text-slate-700 hover:text-blue-600 flex items-center gap-2">
                    <i class="fas fa-envelope text-slate-400"></i> Email Me
                </a>
                <a href="#" class="text-sm text-slate-700 hover:text-blue-600 flex items-center gap-2">
                    <i class="fab fa-linkedin text-slate-400"></i> LinkedIn Profile
                </a>
                <div class="text-sm text-slate-700 flex items-center gap-2">
                    <i class="fas fa-phone text-slate-400"></i> (847) 826-2578
                </div>
                <div class="text-sm text-slate-700 flex items-center gap-2">
                    <i class="fas fa-map-marker-alt text-slate-400"></i> Chicago, IL
                </div>
            </div>
        </div>
    </aside>

    <!-- Main Content -->
    <main class="flex-1 flex flex-col h-full relative overflow-hidden">
        <!-- Mobile Header -->
        <header class="md:hidden bg-white border-b border-slate-200 p-4 flex justify-between items-center z-20">
            <div class="font-bold text-slate-800">Atish Banerjee</div>
            <button onclick="toggleMobileMenu()" class="text-slate-600 focus:outline-none">
                <i class="fas fa-bars text-xl"></i>
            </button>
        </header>

        <!-- Mobile Menu Overlay -->
        <div id="mobile-menu" class="absolute inset-0 bg-white z-30 transform translate-x-full transition-transform duration-300 md:hidden flex flex-col">
            <div class="p-4 border-b border-slate-200 flex justify-between items-center">
                <span class="font-bold text-lg">Menu</span>
                <button onclick="toggleMobileMenu()" class="text-slate-600">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            <nav class="flex-1 p-4">
                <ul class="space-y-4">
                    <li><button onclick="router('dashboard'); toggleMobileMenu()" class="text-lg font-medium text-slate-700">Executive Dashboard</button></li>
                    <li><button onclick="router('strategy'); toggleMobileMenu()" class="text-lg font-medium text-slate-700">Strategy Lab</button></li>
                    <li><button onclick="router('experience'); toggleMobileMenu()" class="text-lg font-medium text-slate-700">Impact History</button></li>
                    <li><button onclick="router('skills'); toggleMobileMenu()" class="text-lg font-medium text-slate-700">Competencies</button></li>
                </ul>
            </nav>
        </div>

        <!-- Content Area -->
        <div id="content-area" class="flex-1 overflow-y-auto p-4 md:p-8 bg-slate-50/50">
            <!-- Content Injected via JS -->
        </div>
    </main>

    <script>
        // --- Data Store ---
        const profileData = {
            summary: "Visionary Product Executive with 20+ years of experience bridging the gap between clinical data, commercial strategy, and digital transformation. Expert in crafting AI-First product roadmaps that displace incumbents and capture market share. Proven track record of managing $20M+ P&Ls, leading large-scale organizations (75+ professionals), and driving enterprise-wide innovation.",
            metrics: [
                { label: "P&L Managed", value: "$20M+", icon: "fa-sack-dollar", color: "text-emerald-600", bg: "bg-emerald-100" },
                { label: "Team Size Led", value: "75+", icon: "fa-users", color: "text-blue-600", bg: "bg-blue-100" },
                { label: "Experience", value: "20+ Yrs", icon: "fa-clock", color: "text-purple-600", bg: "bg-purple-100" },
                { label: "Market Opp ID", value: "$250M+", icon: "fa-bullseye", color: "text-amber-600", bg: "bg-amber-100" }
            ],
            competencies: {
                labels: ['Product Strategy', 'AI & Innovation', 'Executive Leadership', 'Healthcare Domain', 'Digital Transf.', 'Commercial GTM'],
                data: [95, 90, 85, 95, 90, 85]
            },
            mckesson: {
                title: "McKesson | Senior Product Manager - RWD & Analytics",
                period: "Nov 2024 – Present",
                summary: "Leading strategic transformation from retrospective reporting to predictive intelligence.",
                highlights: [
                    "Architected 'Patient Ready' data product strategy integrating Claims, EHR, SDOH.",
                    "Defined $250M SOM strategy targeting Commercial Ops teams.",
                    "Developed 'Disruption Pricing' model (Value Trap) to displace incumbents.",
                    "Launched predictive biomarker alerts (e.g., PD-L1) for 6-week sales head start."
                ],
                marketData: {
                    values: [25000, 5000, 250], // TAM, SAM, SOM in Millions (scaled for chart)
                    labels: ["TAM: Global Life Sciences ($25B)", "SAM: US RWD ($5B)", "SOM: Patient Ready ($250M)"]
                }
            },
            optum: {
                title: "Optum (UHG) | Senior Product Leader",
                period: "Nov 2011 – Sept 2024",
                summary: "Directed enterprise strategies for consumer engagement, Star Ratings, and Specialty Rx.",
                charts: {
                    nps: { labels: ['Before AI', 'After AI Launch'], data: [45, 60] },
                    stars: { labels: ['Base Membership', '4-Star+ Membership'], data: [40, 80] }, // percentages
                    outreach: { labels: ['Manual', 'Automated AI'], data: [3500, 15000] }
                },
                highlights: [
                    "Led 'Advocate4Me' AI strategy: +15 point NPS increase.",
                    "Moved 80% of Medicare Advantage membership to 4-Star+ plans.",
                    "Scaled outreach by 428% through intelligent automation.",
                    "Reduced 'Time to Therapy' for Specialty Rx patients by 50%."
                ]
            },
            saven: {
                title: "Saven Technologies | Consulting Partner",
                period: "Feb 2006 – Oct 2011",
                summary: "Executive leader for Healthcare & Retail practice responsible for P&L and growth.",
                metrics: { revenue: 20, savings: 3, team: 75 },
                highlights: [
                    "Managed $20M annual revenue portfolio.",
                    "Achieved $5M+ annual growth target.",
                    "Built and mentored organization of 75+ professionals.",
                    "Reduced operating budget costs by $3M (15%) via restructuring."
                ]
            }
        };

        // --- State Management ---
        let currentView = 'dashboard';

        // --- Router ---
        function router(view) {
            currentView = view;
            
            // Update Sidebar UI
            document.querySelectorAll('.nav-item').forEach(el => el.classList.remove('active'));
            const navId = `nav-${view}`;
            if(document.getElementById(navId)) document.getElementById(navId).classList.add('active');

            const contentArea = document.getElementById('content-area');
            contentArea.innerHTML = ''; // Clear content

            // Render Views
            switch(view) {
                case 'dashboard':
                    renderDashboard(contentArea);
                    break;
                case 'strategy':
                    renderStrategy(contentArea);
                    break;
                case 'experience':
                    renderExperience(contentArea);
                    break;
                case 'skills':
                    renderSkills(contentArea);
                    break;
                default:
                    renderDashboard(contentArea);
            }
        }

        // --- Render Functions ---

        function renderDashboard(container) {
            const html = `
                <div class="fade-in max-w-5xl mx-auto">
                    <!-- Header -->
                    <div class="mb-8">
                        <h2 class="text-3xl font-bold text-slate-800 mb-2">Executive Dashboard</h2>
                        <p class="text-slate-600 max-w-3xl">${profileData.summary}</p>
                    </div>

                    <!-- Metrics Grid -->
                    <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-8">
                        ${profileData.metrics.map(m => `
                            <div class="bg-white p-6 rounded-xl border border-slate-100 shadow-sm flex flex-col items-center text-center hover:shadow-md transition-shadow">
                                <div class="w-12 h-12 ${m.bg} ${m.color} rounded-full flex items-center justify-center mb-3 text-xl">
                                    <i class="fas ${m.icon}"></i>
                                </div>
                                <div class="text-2xl font-bold text-slate-800">${m.value}</div>
                                <div class="text-xs text-slate-500 font-medium uppercase tracking-wide mt-1">${m.label}</div>
                            </div>
                        `).join('')}
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                        <!-- Competency Radar -->
                        <div class="bg-white p-6 rounded-xl border border-slate-100 shadow-sm">
                            <h3 class="text-lg font-bold text-slate-800 mb-4 flex items-center gap-2">
                                <i class="fas fa-radar text-blue-500"></i> Core Competencies
                            </h3>
                            <div class="chart-container">
                                <canvas id="radarChart"></canvas>
                            </div>
                            <div class="mt-4 text-sm text-slate-500 text-center">
                                *Balanced mix of Strategic Vision, Technical Execution, and Commercial Acumen.
                            </div>
                        </div>

                        <!-- Strategic Focus Areas -->
                        <div class="bg-white p-6 rounded-xl border border-slate-100 shadow-sm flex flex-col justify-between">
                            <div>
                                <h3 class="text-lg font-bold text-slate-800 mb-4 flex items-center gap-2">
                                    <i class="fas fa-crosshairs text-blue-500"></i> Strategic Focus
                                </h3>
                                <div class="space-y-4">
                                    <div class="p-4 bg-slate-50 rounded-lg border-l-4 border-blue-500">
                                        <div class="font-bold text-slate-700">"Patient Ready" Data</div>
                                        <div class="text-sm text-slate-600 mt-1">Shifting from volume to <strong>Context</strong>. Integrating Claims + EHR + SDOH to solve the "Data Janitor" problem.</div>
                                    </div>
                                    <div class="p-4 bg-slate-50 rounded-lg border-l-4 border-emerald-500">
                                        <div class="font-bold text-slate-700">AI-First Commercialization</div>
                                        <div class="text-sm text-slate-600 mt-1">Deploying probabilistic models to predict patient behavior, creating a <strong>Time-to-Insight</strong> competitive moat.</div>
                                    </div>
                                    <div class="p-4 bg-slate-50 rounded-lg border-l-4 border-purple-500">
                                        <div class="font-bold text-slate-700">Disruption Pricing</div>
                                        <div class="text-sm text-slate-600 mt-1">The "Value Trap" strategy: Offering premium clinical context at parity prices to displace incumbents.</div>
                                    </div>
                                </div>
                            </div>
                            <button onclick="router('strategy')" class="mt-6 w-full py-3 bg-blue-50 text-blue-600 font-medium rounded-lg hover:bg-blue-100 transition-colors flex justify-center items-center gap-2">
                                View Strategy Lab <i class="fas fa-arrow-right"></i>
                            </button>
                        </div>
                    </div>
                </div>
            `;
            container.innerHTML = html;
            initRadarChart();
        }

        function renderStrategy(container) {
            const html = `
                <div class="fade-in max-w-5xl mx-auto">
                    <div class="flex items-center gap-3 mb-6">
                        <button onclick="router('dashboard')" class="text-slate-400 hover:text-blue-600"><i class="fas fa-arrow-left"></i> Back</button>
                        <h2 class="text-2xl font-bold text-slate-800">Strategy Lab: The "Patient Ready" Initiative</h2>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                        <!-- Main Visualization: Market Sizing -->
                        <div class="lg:col-span-2 bg-white p-6 rounded-xl border border-slate-100 shadow-sm">
                            <h3 class="text-lg font-bold text-slate-800 mb-2">Market Penetration Strategy (TAM/SAM/SOM)</h3>
                            <p class="text-sm text-slate-500 mb-6">Targeting the $250M "Frustrated Segment" in Commercial Ops via Disruption Pricing.</p>
                            <div class="plotly-container" id="funnelChart"></div>
                        </div>

                        <!-- Key Bet Details -->
                        <div class="space-y-6">
                            <div class="bg-white p-6 rounded-xl border border-slate-100 shadow-sm">
                                <h4 class="font-bold text-slate-700 mb-3 text-lg">The Problem</h4>
                                <ul class="space-y-3">
                                    <li class="flex gap-3 text-sm text-slate-600">
                                        <i class="fas fa-times-circle text-red-400 mt-1"></i>
                                        <span>Competitors provide "Swiss Cheese" data (gaps in patient journey).</span>
                                    </li>
                                    <li class="flex gap-3 text-sm text-slate-600">
                                        <i class="fas fa-times-circle text-red-400 mt-1"></i>
                                        <span>Pharma spends 80% of time cleaning data, 20% analyzing.</span>
                                    </li>
                                    <li class="flex gap-3 text-sm text-slate-600">
                                        <i class="fas fa-times-circle text-red-400 mt-1"></i>
                                        <span>Claims data is 6 weeks old (Lagging Indicator).</span>
                                    </li>
                                </ul>
                            </div>

                            <div class="bg-blue-600 p-6 rounded-xl shadow-md text-white">
                                <h4 class="font-bold mb-3 text-lg border-b border-blue-500 pb-2">The "Patient Ready" Solution</h4>
                                <ul class="space-y-3">
                                    <li class="flex gap-3 text-sm text-blue-100">
                                        <i class="fas fa-check-circle text-white mt-1"></i>
                                        <span><strong>Probabilistic Linking:</strong> Connecting Claims + EHR + SDOH despite typo/variations.</span>
                                    </li>
                                    <li class="flex gap-3 text-sm text-blue-100">
                                        <i class="fas fa-check-circle text-white mt-1"></i>
                                        <span><strong>Predictive Alerts:</strong> Using Lab data (Biomarkers) to signal intent 6 weeks early.</span>
                                    </li>
                                    <li class="flex gap-3 text-sm text-blue-100">
                                        <i class="fas fa-check-circle text-white mt-1"></i>
                                        <span><strong>Zero Integration:</strong> Delivered "Analysis Ready" to Commercial Ops.</span>
                                    </li>
                                </ul>
                            </div>
                        </div>
                    </div>

                    <!-- Process Flow Diagram (CSS/HTML) -->
                    <div class="mt-8 bg-white p-8 rounded-xl border border-slate-100 shadow-sm overflow-x-auto">
                        <h3 class="text-lg font-bold text-slate-800 mb-6 text-center">From "Data Janitor" to "Predictive Engine"</h3>
                        <div class="flex justify-between items-center min-w-[600px] relative">
                            <!-- Step 1 -->
                            <div class="flex flex-col items-center z-10 w-1/4">
                                <div class="w-16 h-16 bg-slate-100 rounded-full flex items-center justify-center border-2 border-slate-300 text-slate-500 mb-3">
                                    <i class="fas fa-database text-2xl"></i>
                                </div>
                                <div class="font-bold text-slate-700 text-center">Raw Data Silos</div>
                                <div class="text-xs text-slate-500 text-center mt-1">Claims, EHR, SDOH</div>
                            </div>
                            
                            <!-- Arrow -->
                            <div class="flex-1 h-1 bg-slate-200 relative">
                                <i class="fas fa-chevron-right absolute right-0 top-1/2 transform -translate-y-1/2 text-slate-300"></i>
                            </div>

                            <!-- Step 2 -->
                            <div class="flex flex-col items-center z-10 w-1/4">
                                <div class="w-16 h-16 bg-blue-100 rounded-full flex items-center justify-center border-2 border-blue-500 text-blue-600 mb-3 shadow-lg">
                                    <i class="fas fa-brain text-2xl"></i>
                                </div>
                                <div class="font-bold text-blue-700 text-center">AI Linking Engine</div>
                                <div class="text-xs text-slate-500 text-center mt-1">Probabilistic Match</div>
                            </div>

                            <!-- Arrow -->
                            <div class="flex-1 h-1 bg-slate-200 relative">
                                <i class="fas fa-chevron-right absolute right-0 top-1/2 transform -translate-y-1/2 text-slate-300"></i>
                            </div>

                            <!-- Step 3 -->
                            <div class="flex flex-col items-center z-10 w-1/4">
                                <div class="w-16 h-16 bg-emerald-100 rounded-full flex items-center justify-center border-2 border-emerald-500 text-emerald-600 mb-3 shadow-lg">
                                    <i class="fas fa-chart-line text-2xl"></i>
                                </div>
                                <div class="font-bold text-emerald-700 text-center">Predictive Insights</div>
                                <div class="text-xs text-slate-500 text-center mt-1">Time-to-Insight: <span class="text-emerald-600 font-bold">-6 Weeks</span></div>
                            </div>
                        </div>
                    </div>
                </div>
            `;
            container.innerHTML = html;
            initFunnelChart();
        }

        function renderExperience(container) {
            const html = `
                <div class="fade-in max-w-5xl mx-auto space-y-12">
                     <div class="mb-8">
                        <h2 class="text-3xl font-bold text-slate-800 mb-2">Impact History</h2>
                        <p class="text-slate-600">A track record of turning strategy into measurable P&L results.</p>
                    </div>

                    <!-- McKesson -->
                    <div class="bg-white rounded-xl shadow-sm border-l-4 border-blue-600 overflow-hidden">
                        <div class="p-6 md:p-8">
                            <div class="flex justify-between items-start mb-4">
                                <div>
                                    <h3 class="text-xl font-bold text-slate-800">${profileData.mckesson.title}</h3>
                                    <div class="text-sm font-medium text-slate-500">${profileData.mckesson.period}</div>
                                </div>
                                <div class="bg-blue-100 text-blue-700 text-xs font-bold px-3 py-1 rounded-full">STRATEGY</div>
                            </div>
                            <p class="text-slate-600 mb-6 italic border-l-2 border-slate-200 pl-4">"${profileData.mckesson.summary}"</p>
                            
                            <div class="grid md:grid-cols-2 gap-8">
                                <ul class="space-y-3">
                                    ${profileData.mckesson.highlights.map(h => `
                                        <li class="flex gap-3 text-sm text-slate-700">
                                            <i class="fas fa-check text-blue-500 mt-1"></i> ${h}
                                        </li>
                                    `).join('')}
                                </ul>
                                <div class="bg-slate-50 p-4 rounded-lg flex items-center justify-center">
                                    <div class="text-center">
                                        <div class="text-3xl font-bold text-slate-800">$250M</div>
                                        <div class="text-sm text-slate-500">Serviceable Market ID'd</div>
                                        <div class="mt-2 text-xs text-blue-600 font-medium">Through "Patient Ready" Wedge Strategy</div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Optum -->
                    <div class="bg-white rounded-xl shadow-sm border-l-4 border-purple-600 overflow-hidden">
                        <div class="p-6 md:p-8">
                            <div class="flex justify-between items-start mb-4">
                                <div>
                                    <h3 class="text-xl font-bold text-slate-800">${profileData.optum.title}</h3>
                                    <div class="text-sm font-medium text-slate-500">${profileData.optum.period}</div>
                                </div>
                                <div class="bg-purple-100 text-purple-700 text-xs font-bold px-3 py-1 rounded-full">EXECUTION</div>
                            </div>
                            
                            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8">
                                <div class="chart-container" style="height: 200px;">
                                    <canvas id="optumNpsChart"></canvas>
                                </div>
                                <div class="chart-container" style="height: 200px;">
                                    <canvas id="optumStarChart"></canvas>
                                </div>
                                <div class="chart-container" style="height: 200px;">
                                    <canvas id="optumScaleChart"></canvas>
                                </div>
                            </div>

                            <ul class="grid md:grid-cols-2 gap-4">
                                ${profileData.optum.highlights.map(h => `
                                    <li class="flex gap-3 text-sm text-slate-700 bg-slate-50 p-3 rounded">
                                        <i class="fas fa-bolt text-purple-500 mt-1"></i> ${h}
                                    </li>
                                `).join('')}
                            </ul>
                        </div>
                    </div>

                    <!-- Saven -->
                    <div class="bg-white rounded-xl shadow-sm border-l-4 border-emerald-600 overflow-hidden">
                        <div class="p-6 md:p-8">
                            <div class="flex justify-between items-start mb-4">
                                <div>
                                    <h3 class="text-xl font-bold text-slate-800">${profileData.saven.title}</h3>
                                    <div class="text-sm font-medium text-slate-500">${profileData.saven.period}</div>
                                </div>
                                <div class="bg-emerald-100 text-emerald-700 text-xs font-bold px-3 py-1 rounded-full">LEADERSHIP</div>
                            </div>
                            
                            <div class="grid grid-cols-3 gap-4 mb-6 text-center">
                                <div class="p-3 bg-emerald-50 rounded-lg">
                                    <div class="text-xl font-bold text-emerald-700">$20M</div>
                                    <div class="text-xs text-emerald-600">P&L Managed</div>
                                </div>
                                <div class="p-3 bg-emerald-50 rounded-lg">
                                    <div class="text-xl font-bold text-emerald-700">75+</div>
                                    <div class="text-xs text-emerald-600">Team Size</div>
                                </div>
                                <div class="p-3 bg-emerald-50 rounded-lg">
                                    <div class="text-xl font-bold text-emerald-700">15%</div>
                                    <div class="text-xs text-emerald-600">Cost Reduction</div>
                                </div>
                            </div>
                            <ul class="space-y-2">
                                ${profileData.saven.highlights.map(h => `
                                    <li class="flex gap-3 text-sm text-slate-700">
                                        <i class="fas fa-arrow-up text-emerald-500 mt-1"></i> ${h}
                                    </li>
                                `).join('')}
                            </ul>
                        </div>
                    </div>
                </div>
            `;
            container.innerHTML = html;
            initOptumCharts();
        }

        function renderSkills(container) {
            const html = `
                <div class="fade-in max-w-5xl mx-auto">
                    <h2 class="text-2xl font-bold text-slate-800 mb-6">Competency Matrix</h2>
                    
                    <div class="grid md:grid-cols-2 gap-8">
                        <div class="bg-white p-6 rounded-xl border border-slate-100 shadow-sm">
                            <h3 class="font-bold text-slate-700 mb-4">Technical & Strategic Balance</h3>
                            <div class="chart-container">
                                <canvas id="radarChartLarge"></canvas>
                            </div>
                        </div>

                        <div class="space-y-6">
                            <div class="bg-white p-6 rounded-xl border border-slate-100 shadow-sm">
                                <h3 class="font-bold text-slate-700 mb-3 border-b pb-2">Product Strategy</h3>
                                <div class="flex flex-wrap gap-2">
                                    ${['Vision & Roadmap', 'TAM/SAM/SOM Analysis', 'Market Penetration', 'Go-to-Market (GTM)', 'Pricing Strategy', 'Value Prop Design'].map(s => `
                                        <span class="px-3 py-1 bg-blue-50 text-blue-700 text-xs font-medium rounded-full">${s}</span>
                                    `).join('')}
                                </div>
                            </div>
                            
                            <div class="bg-white p-6 rounded-xl border border-slate-100 shadow-sm">
                                <h3 class="font-bold text-slate-700 mb-3 border-b pb-2">AI & Innovation</h3>
                                <div class="flex flex-wrap gap-2">
                                    ${['AI/ML Model Integration', 'Probabilistic Linkage', 'Predictive Analytics', 'Next Best Action Engines', 'Data Pipeline Strategy'].map(s => `
                                        <span class="px-3 py-1 bg-purple-50 text-purple-700 text-xs font-medium rounded-full">${s}</span>
                                    `).join('')}
                                </div>
                            </div>

                            <div class="bg-white p-6 rounded-xl border border-slate-100 shadow-sm">
                                <h3 class="font-bold text-slate-700 mb-3 border-b pb-2">Healthcare Domain</h3>
                                <div class="flex flex-wrap gap-2">
                                    ${['Real-World Data (RWD)', 'Payer/Provider Workflow', 'Value-Based Care', 'HEDIS/Star Ratings', 'EHR Integration', 'Claims Data'].map(s => `
                                        <span class="px-3 py-1 bg-emerald-50 text-emerald-700 text-xs font-medium rounded-full">${s}</span>
                                    `).join('')}
                                </div>
                            </div>

                             <div class="bg-white p-6 rounded-xl border border-slate-100 shadow-sm">
                                <h3 class="font-bold text-slate-700 mb-3 border-b pb-2">Education & Certs</h3>
                                <ul class="text-sm text-slate-600 space-y-2">
                                    <li><i class="fas fa-graduation-cap text-slate-400 mr-2"></i><strong>B.Tech Information Technology</strong> | RCC IIT</li>
                                    <li><i class="fas fa-certificate text-slate-400 mr-2"></i><strong>Certified Scrum Product Owner (CSPO)</strong></li>
                                </ul>
                            </div>
                        </div>
                    </div>
                </div>
            `;
            container.innerHTML = html;
            setTimeout(() => {
                new Chart(document.getElementById('radarChartLarge'), {
                    type: 'radar',
                    data: {
                        labels: profileData.competencies.labels,
                        datasets: [{
                            label: 'Skill Proficiency',
                            data: profileData.competencies.data,
                            fill: true,
                            backgroundColor: 'rgba(59, 130, 246, 0.2)',
                            borderColor: 'rgb(59, 130, 246)',
                            pointBackgroundColor: 'rgb(59, 130, 246)',
                            pointBorderColor: '#fff',
                            pointHoverBackgroundColor: '#fff',
                            pointHoverBorderColor: 'rgb(59, 130, 246)'
                        }]
                    },
                    options: {
                        maintainAspectRatio: false,
                        responsive: true,
                        scales: { r: { angleLines: { display: false }, suggestedMin: 50, suggestedMax: 100, ticks: { display: false } } },
                        plugins: { legend: { display: false } }
                    }
                });
            }, 100);
        }

        // --- Chart Initialization ---

        function initRadarChart() {
            const ctx = document.getElementById('radarChart');
            if(!ctx) return;
            new Chart(ctx, {
                type: 'radar',
                data: {
                    labels: profileData.competencies.labels,
                    datasets: [{
                        label: 'Proficiency',
                        data: profileData.competencies.data,
                        fill: true,
                        backgroundColor: 'rgba(59, 130, 246, 0.2)',
                        borderColor: 'rgb(59, 130, 246)',
                        pointBackgroundColor: 'rgb(59, 130, 246)',
                        pointBorderColor: '#fff',
                        pointHoverBackgroundColor: '#fff',
                        pointHoverBorderColor: 'rgb(59, 130, 246)'
                    }]
                },
                options: {
                    maintainAspectRatio: false,
                    responsive: true,
                    scales: {
                        r: {
                            angleLines: { display: false },
                            suggestedMin: 0,
                            suggestedMax: 100,
                            ticks: { display: false }
                        }
                    },
                    plugins: { legend: { display: false } }
                }
            });
        }

        function initFunnelChart() {
            const data = [{
                type: 'funnel',
                y: profileData.mckesson.marketData.labels,
                x: profileData.mckesson.marketData.values,
                textinfo: "value+label",
                textposition: "inside",
                marker: {
                    color: ["#cbd5e1", "#93c5fd", "#2563eb"],
                }
            }];

            const layout = {
                margin: { l: 200, r: 20, t: 20, b: 20 }, // Adjust margins to fit labels
                funnelmode: "stack",
                showlegend: false
            };

            Plotly.newPlot('funnelChart', data, layout, {displayModeBar: false, responsive: true});
        }

        function initOptumCharts() {
            // NPS Chart
            new Chart(document.getElementById('optumNpsChart'), {
                type: 'bar',
                data: {
                    labels: profileData.optum.charts.nps.labels,
                    datasets: [{
                        label: 'NPS Score',
                        data: profileData.optum.charts.nps.data,
                        backgroundColor: ['#e2e8f0', '#3b82f6'],
                        borderRadius: 5
                    }]
                },
                options: {
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false }, title: { display: true, text: 'NPS Impact (Advocate4Me)' } },
                    scales: { y: { beginAtZero: true } }
                }
            });

            // Star Rating Chart
            new Chart(document.getElementById('optumStarChart'), {
                type: 'doughnut',
                data: {
                    labels: ['4-Star+', 'Below 4-Star'],
                    datasets: [{
                        data: [80, 20],
                        backgroundColor: ['#10b981', '#e2e8f0'],
                    }]
                },
                options: {
                    maintainAspectRatio: false,
                    plugins: { legend: { position: 'bottom' }, title: { display: true, text: 'Membership Quality (Stars)' } }
                }
            });

             // Outreach Chart
             new Chart(document.getElementById('optumScaleChart'), {
                type: 'line',
                data: {
                    labels: profileData.optum.charts.outreach.labels,
                    datasets: [{
                        label: 'Touchpoints',
                        data: profileData.optum.charts.outreach.data,
                        borderColor: '#8b5cf6',
                        backgroundColor: 'rgba(139, 92, 246, 0.1)',
                        fill: true,
                        tension: 0.4
                    }]
                },
                options: {
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false }, title: { display: true, text: 'Outreach Scale (AI Automation)' } },
                    scales: { y: { beginAtZero: true } }
                }
            });
        }

        // Mobile Menu Toggle
        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu');
            if (menu.classList.contains('translate-x-full')) {
                menu.classList.remove('translate-x-full');
            } else {
                menu.classList.add('translate-x-full');
            }
        }

        // --- Init ---
        // Start on Dashboard
        router('dashboard');

    </script>
</body>
</html>
