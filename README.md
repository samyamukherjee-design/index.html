<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LAA POLITI | Strategic Command Center</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;600;900&family=Inter:wght@300;400;500;700&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; background-color: #0f172a; color: #f8fafc; overflow: hidden; }
        .font-outfit { font-family: 'Outfit', sans-serif; }
        .glass { background: rgba(30, 41, 59, 0.7); backdrop-filter: blur(12px); border: 1px solid rgba(255, 255, 255, 0.05); }
        .sidebar-link.active { background: linear-gradient(90deg, rgba(99, 102, 241, 0.2) 0%, rgba(99, 102, 241, 0) 100%); border-left: 4px solid #6366f1; color: white; }
        .text-primary { color: #6366f1; }
        .bg-primary { background-color: #6366f1; }
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: #0f172a; }
        ::-webkit-scrollbar-thumb { background: #334155; border-radius: 10px; }
    </style>
</head>
<body class="h-screen flex">

    <!-- Sidebar -->
    <aside class="w-72 glass flex flex-col h-full hidden md:flex z-20 border-r border-slate-800">
        <div class="h-24 flex items-center px-8 border-b border-slate-800">
            <h1 class="text-3xl font-black font-outfit text-white tracking-tight">
                LAA <span class="text-primary">POLITI</span>
            </h1>
        </div>
        
        <nav class="flex-1 px-4 py-8 space-y-2 overflow-y-auto" id="sidebarMenu">
            <a href="#" data-target="view-command" class="sidebar-link active flex items-center gap-4 px-4 py-3 rounded-lg transition-all duration-200">
                <i class="fas fa-chart-pie text-lg w-6"></i>
                <span class="font-semibold">Command Center</span>
            </a>
            <a href="#" data-target="view-ajeya" class="sidebar-link flex items-center gap-4 px-4 py-3 rounded-lg transition-all duration-200 text-slate-400">
                <i class="fas fa-chess-queen text-lg w-6"></i>
                <span class="font-semibold">'Ajeya' Campaign</span>
            </a>
            <a href="#" data-target="view-shield" class="sidebar-link flex items-center gap-4 px-4 py-3 rounded-lg transition-all duration-200 text-slate-400">
                <i class="fas fa-shield-heart text-lg w-6"></i>
                <span class="font-semibold">Citizen Shield</span>
            </a>
            <a href="#" data-target="view-booth" class="sidebar-link flex items-center gap-4 px-4 py-3 rounded-lg transition-all duration-200 text-slate-400">
                <i class="fas fa-map-marked-alt text-lg w-6"></i>
                <span class="font-semibold">WB Booth 2026</span>
            </a>
            <a href="#" data-target="view-legal" class="sidebar-link flex items-center gap-4 px-4 py-3 rounded-lg transition-all duration-200 text-slate-400">
                <i class="fas fa-scale-balanced text-lg w-6"></i>
                <span class="font-semibold">Legal & ECI</span>
            </a>
            <a href="#" data-target="view-leader" class="sidebar-link flex items-center gap-4 px-4 py-3 rounded-lg transition-all duration-200 text-slate-400">
                <i class="fas fa-user-tie text-lg w-6"></i>
                <span class="font-semibold">Leader Directory</span>
            </a>
        </nav>

        <div class="p-6 border-t border-slate-800">
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-full bg-slate-700 flex items-center justify-center text-primary">
                    <i class="fas fa-user-secret"></i>
                </div>
                <div>
                    <p class="text-sm font-bold text-white">Central Admin</p>
                    <p class="text-xs text-slate-500 uppercase tracking-widest">Master Access</p>
                </div>
            </div>
        </div>
    </aside>

    <!-- Main Content -->
    <main class="flex-1 flex flex-col h-full overflow-hidden">
        <!-- Header -->
        <header class="h-20 glass border-b border-slate-800 flex items-center justify-between px-8 z-10">
            <div class="flex items-center gap-4">
                <button class="md:hidden text-white"><i class="fas fa-bars"></i></button>
                <div class="bg-slate-900 border border-slate-700 rounded-full px-4 py-2 flex items-center gap-2">
                    <div class="w-2 h-2 bg-green-500 rounded-full animate-pulse"></div>
                    <span class="text-xs font-bold text-slate-300 uppercase tracking-tighter">System Live: WB-2026 Node</span>
                </div>
            </div>
            <div class="flex items-center gap-6">
                <div class="relative hidden sm:block">
                    <input type="text" placeholder="Global Search..." class="bg-slate-900/50 border border-slate-700 rounded-lg px-4 py-2 text-sm focus:outline-none focus:border-primary w-64">
                    <i class="fas fa-search absolute right-3 top-3 text-slate-500"></i>
                </div>
                <div class="flex gap-4">
                    <button class="text-slate-400 hover:text-white transition-colors relative">
                        <i class="fas fa-bell"></i>
                        <span class="absolute -top-1 -right-1 w-2 h-2 bg-red-500 rounded-full"></span>
                    </button>
                    <button class="text-slate-400 hover:text-white transition-colors"><i class="fas fa-cog"></i></button>
                </div>
            </div>
        </header>

        <!-- Viewport -->
        <div class="flex-1 overflow-y-auto p-8 relative" id="mainViewport">
            <!-- Background Glows -->
            <div class="fixed top-0 right-0 w-96 h-96 bg-primary opacity-5 rounded-full blur-[120px] pointer-events-none"></div>
            <div class="fixed bottom-0 left-72 w-96 h-96 bg-blue-500 opacity-5 rounded-full blur-[120px] pointer-events-none"></div>

            <!-- VIEW: Command Center -->
            <div id="view-command" class="view-content block">
                <div class="mb-10">
                    <h2 class="text-4xl font-black font-outfit text-white mb-2">Executive Overview</h2>
                    <p class="text-slate-400">West Bengal 2026 Assembly Elections | Strategy & Audit Analytics</p>
                </div>

                <!-- Stats -->
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-10">
                    <div class="glass p-6 rounded-2xl border-l-4 border-primary">
                        <div class="flex justify-between items-start mb-4">
                            <div class="p-2 bg-primary/10 rounded-lg text-primary"><i class="fas fa-users"></i></div>
                            <span class="text-xs font-bold text-green-400">+12%</span>
                        </div>
                        <h3 class="text-slate-400 text-xs font-bold uppercase tracking-widest mb-1">Total Reach</h3>
                        <p class="text-3xl font-black text-white">4.2M</p>
                    </div>
                    <div class="glass p-6 rounded-2xl border-l-4 border-purple-500">
                        <div class="flex justify-between items-start mb-4">
                            <div class="p-2 bg-purple-500/10 rounded-lg text-purple-500"><i class="fas fa-bullhorn"></i></div>
                            <span class="text-xs font-bold text-green-400">Active</span>
                        </div>
                        <h3 class="text-slate-400 text-xs font-bold uppercase tracking-widest mb-1">'Ajeya' Units</h3>
                        <p class="text-3xl font-black text-white">294/294</p>
                    </div>
                    <div class="glass p-6 rounded-2xl border-l-4 border-blue-500">
                        <div class="flex justify-between items-start mb-4">
                            <div class="p-2 bg-blue-500/10 rounded-lg text-blue-500"><i class="fas fa-shield-alt"></i></div>
                            <span class="text-xs font-bold text-slate-400">Verified</span>
                        </div>
                        <h3 class="text-slate-400 text-xs font-bold uppercase tracking-widest mb-1">Shield Cases</h3>
                        <p class="text-3xl font-black text-white">1,842</p>
                    </div>
                    <div class="glass p-6 rounded-2xl border-l-4 border-amber-500">
                        <div class="flex justify-between items-start mb-4">
                            <div class="p-2 bg-amber-500/10 rounded-lg text-amber-500"><i class="fas fa-triangle-exclamation"></i></div>
                            <span class="text-xs font-bold text-red-500">High</span>
                        </div>
                        <h3 class="text-slate-400 text-xs font-bold uppercase tracking-widest mb-1">Critical Booths</h3>
                        <p class="text-3xl font-black text-white">12,403</p>
                    </div>
                </div>

                <!-- Charts & Activity Area -->
                <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                    <div class="lg:col-span-2 glass p-8 rounded-3xl">
                        <h3 class="text-xl font-bold mb-6 flex items-center gap-2">
                            <i class="fas fa-chart-line text-primary"></i> Campaign Performance Trend
                        </h3>
                        <div class="h-80">
                            <canvas id="mainTrendChart"></canvas>
                        </div>
                    </div>
                    <div class="glass p-8 rounded-3xl">
                        <h3 class="text-xl font-bold mb-6">Recent Intelligence</h3>
                        <div class="space-y-6">
                            <div class="flex gap-4 border-l-2 border-primary pl-4 py-1">
                                <div>
                                    <p class="text-sm font-bold text-white">Booth Violation Reported</p>
                                    <p class="text-xs text-slate-500">2 mins ago | Nandigram AC</p>
                                </div>
                            </div>
                            <div class="flex gap-4 border-l-2 border-slate-700 pl-4 py-1">
                                <div>
                                    <p class="text-sm font-bold text-white">Ajeya Saree Visual #4 Published</p>
                                    <p class="text-xs text-slate-500">1 hour ago | Social Node</p>
                                </div>
                            </div>
                            <div class="flex gap-4 border-l-2 border-amber-500 pl-4 py-1">
                                <div>
                                    <p class="text-sm font-bold text-white">Legal Alert: ECI Response</p>
                                    <p class="text-xs text-slate-500">3 hours ago | Central HQ</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- VIEW: 'Ajeya' Campaign -->
            <div id="view-ajeya" class="view-content hidden">
                <div class="mb-10">
                    <h2 class="text-4xl font-black font-outfit text-white mb-2">'Ajeya' Campaign Strategy</h2>
                    <p class="text-slate-400">Master Chessboard Saree & Visual Asset Management</p>
                </div>
                <div class="glass p-12 rounded-3xl text-center">
                    <div class="w-24 h-24 bg-purple-500/20 text-purple-500 rounded-full flex items-center justify-center text-4xl mx-auto mb-6">
                        <i class="fas fa-chess-queen"></i>
                    </div>
                    <h3 class="text-2xl font-bold mb-4">Module Initializing</h3>
                    <p class="text-slate-400 max-w-md mx-auto mb-8">Asset distribution network for the 'Ajeya' campaign is currently syncing with regional nodes.</p>
                    <div class="flex justify-center gap-4">
                        <div class="bg-slate-800 px-6 py-3 rounded-xl border border-slate-700">Digital Assets: 14</div>
                        <div class="bg-slate-800 px-6 py-3 rounded-xl border border-slate-700">Physical Units: 294</div>
                    </div>
                </div>
            </div>

            <!-- VIEW: Citizen Shield -->
            <div id="view-shield" class="view-content hidden">
                <div class="mb-10">
                    <h2 class="text-4xl font-black font-outfit text-white mb-2">Citizen Shield Protection</h2>
                    <p class="text-slate-400">Kolkata Incident Tracking & Legal Response Center</p>
                </div>
                <div class="glass p-12 rounded-3xl border border-blue-500/20">
                    <div class="w-24 h-24 bg-blue-500/20 text-blue-500 rounded-full flex items-center justify-center text-4xl mx-auto mb-6">
                        <i class="fas fa-shield-heart"></i>
                    </div>
                    <h3 class="text-2xl font-bold mb-4">Protecting the Voice of People</h3>
                    <p class="text-slate-400 mb-8">Real-time tracking of cases and support mechanisms for victims.</p>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                        <div class="bg-slate-900/50 p-6 rounded-2xl border border-slate-800">
                            <p class="text-blue-400 font-bold mb-2">Legal Team</p>
                            <p class="text-2xl text-white">Ready</p>
                        </div>
                        <div class="bg-slate-900/50 p-6 rounded-2xl border border-slate-800">
                            <p class="text-blue-400 font-bold mb-2">Documentation</p>
                            <p class="text-2xl text-white">Encrypted</p>
                        </div>
                        <div class="bg-slate-900/50 p-6 rounded-2xl border border-slate-800">
                            <p class="text-blue-400 font-bold mb-2">Support Cases</p>
                            <p class="text-2xl text-white">Live</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Placeholder for other views -->
            <div id="view-booth" class="view-content hidden py-20 text-center">
                 <i class="fas fa-person-digging text-6xl text-slate-700 mb-6"></i>
                 <h2 class="text-3xl font-bold text-white mb-2 italic">Building Booth Intelligence...</h2>
                 <p class="text-slate-500 uppercase tracking-widest text-sm font-bold">Data Module: WB-BOOTH-2026</p>
            </div>
            <div id="view-legal" class="view-content hidden py-20 text-center">
                 <i class="fas fa-gavel text-6xl text-slate-700 mb-6"></i>
                 <h2 class="text-3xl font-bold text-white mb-2">Legal Compliance Suite</h2>
                 <p class="text-slate-500 uppercase tracking-widest text-sm font-bold">Legal & ECI Complaints Node</p>
            </div>
            <div id="view-leader" class="view-content hidden py-20 text-center">
                 <i class="fas fa-users-viewfinder text-6xl text-slate-700 mb-6"></i>
                 <h2 class="text-3xl font-bold text-white mb-2">Leader Directory</h2>
                 <p class="text-slate-500 uppercase tracking-widest text-sm font-bold">Identity & Role Mapping</p>
            </div>

        </div>
    </main>

    <script>
        // Tab Switching Logic
        const sidebarLinks = document.querySelectorAll('.sidebar-link');
        const viewContents = document.querySelectorAll('.view-content');

        sidebarLinks.forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                
                // Active link style
                sidebarLinks.forEach(l => {
                    l.classList.remove('active');
                    l.classList.add('text-slate-400');
                });
                this.classList.add('active');
                this.classList.remove('text-slate-400');
                
                // Show/Hide Views
                viewContents.forEach(view => {
                    view.classList.add('hidden');
                    view.classList.remove('block');
                });
                
                const targetId = this.getAttribute('data-target');
                const targetView = document.getElementById(targetId);
                if(targetView) {
                    targetView.classList.remove('hidden');
                    targetView.classList.add('block');
                }
            });
        });

        // Initialize Charts
        window.onload = function() {
            const ctx = document.getElementById('mainTrendChart').getContext('2d');
            new Chart(ctx, {
                type: 'line',
                data: {
                    labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
                    datasets: [{
                        label: 'Campaign Reach (Millions)',
                        data: [1.2, 1.9, 2.8, 3.5, 3.9, 4.2],
                        borderColor: '#6366f1',
                        backgroundColor: 'rgba(99, 102, 241, 0.1)',
                        borderWidth: 4,
                        fill: true,
                        tension: 0.4,
                        pointBackgroundColor: '#6366f1'
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false } },
                    scales: {
                        y: { grid: { color: 'rgba(255,255,255,0.05)' }, ticks: { color: '#64748b' } },
                        x: { grid: { display: false }, ticks: { color: '#64748b' } }
                    }
                }
            });
        };
    </script>
</body>
</html>