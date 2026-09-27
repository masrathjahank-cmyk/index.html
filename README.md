```html
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>English Grammar Hub - Master Grammar Interactively</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        brand: {
                            50: '#eef2ff',
                            100: '#e0e7ff',
                            200: '#c7d2fe',
                            500: '#6366f1',
                            600: '#4f46e5',
                            700: '#4338ca',
                            900: '#312e81',
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <!-- Google Font & Font Awesome -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        body { font-family: 'Inter', sans-serif; }
        .glass-panel {
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(226, 232, 240, 0.8);
        }
        .dark .glass-panel {
            background: rgba(15, 23, 42, 0.85);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(51, 65, 85, 0.6);
        }
        /* Custom highlighting tags */
        .hl-subject { background-color: #dbeafe; color: #1e40af; padding: 2px 6px; border-radius: 4px; font-weight: 600; }
        .hl-verb-finite { background-color: #dcfce7; color: #166534; padding: 2px 6px; border-radius: 4px; font-weight: 600; }
        .hl-verb-nonfinite { background-color: #fef3c7; color: #92400e; padding: 2px 6px; border-radius: 4px; font-weight: 600; }
        .hl-clause { background-color: #f3e8ff; color: #6b21a8; padding: 2px 6px; border-radius: 4px; font-weight: 600; }
        
        .dark .hl-subject { background-color: #1e3a8a; color: #bfdbfe; }
        .dark .hl-verb-finite { background-color: #14532d; color: #bbf7d0; }
        .dark .hl-verb-nonfinite { background-color: #78350f; color: #fde68a; }
        .dark .hl-clause { background-color: #581c87; color: #e9d5ff; }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 dark:bg-slate-900 dark:text-slate-100 min-h-screen transition-colors duration-200">

    <header class="sticky top-0 z-50 glass-panel border-b border-slate-200 dark:border-slate-800 shadow-sm">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between">
            <!-- Brand Logo -->
            <div class="flex items-center space-x-3">
                <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-brand-600 to-indigo-400 flex items-center justify-center text-white font-black text-xl shadow-md">
                    <i class="fa-solid font-bold fa-book-open"></i>
                </div>
                <div>
                    <span class="font-extrabold text-xl tracking-tight bg-clip-text text-transparent bg-gradient-to-r from-brand-600 to-indigo-500 dark:from-brand-500 dark:to-indigo-300">
                        GrammarHub
                    </span>
                    <span class="hidden sm:inline-block text-xs bg-brand-100 dark:bg-brand-900/60 text-brand-700 dark:text-brand-300 font-semibold px-2 py-0.5 rounded-full ml-2">Interactive Guide</span>
                </div>
            </div>

            <!-- Search & Quick Navigation -->
            <div class="flex items-center space-x-3 sm:space-x-4">
                <div class="relative hidden md:block">
                    <i class="fa-solid fa-magnifying-glass absolute left-3 top-1/2 -translate-y-1/2 text-slate-400 text-sm"></i>
                    <input id="searchInput" type="text" placeholder="Search topics (e.g. noun clause, finite...)" 
                        class="w-64 pl-9 pr-4 py-1.5 text-sm rounded-xl border border-slate-300 dark:border-slate-700 bg-white/80 dark:bg-slate-800/80 focus:outline-none focus:ring-2 focus:ring-brand-500 transition-all">
                </div>

                <!-- Theme Toggle Button -->
                <button id="themeToggleBtn" aria-label="Toggle theme" class="p-2 rounded-xl bg-slate-200 dark:bg-slate-800 text-slate-600 dark:text-slate-300 hover:bg-slate-300 dark:hover:bg-slate-700 transition">
                    <i id="themeIcon" class="fa-solid fa-moon"></i>
                </button>

                <!-- Mobile Menu Button -->
                <button id="mobileMenuBtn" aria-label="Toggle navigation menu" class="md:hidden p-2 rounded-xl bg-slate-200 dark:bg-slate-800 text-slate-600 dark:text-slate-300">
                    <i class="fa-solid fa-bars"></i>
                </button>
            </div>
        </div>

        <!-- Mobile Nav Menu -->
        <div id="mobileMenu" class="hidden md:hidden border-t border-slate-200 dark:border-slate-800 px-4 py-3 bg-white dark:bg-slate-900 space-y-2">
            <input id="mobileSearchInput" type="text" placeholder="Search topic..." class="w-full pl-3 pr-3 py-1.5 text-sm rounded-lg border border-slate-300 dark:border-slate-700 bg-slate-100 dark:bg-slate-800 mb-2">
            <a href="#overview" class="block py-2 text-sm font-medium hover:text-brand-600">Overview Map</a>
            <a href="#relative-clauses" class="block py-2 text-sm font-medium hover:text-brand-600">Relative Clauses</a>
            <a href="#reduced-clauses" class="block py-2 text-sm font-medium hover:text-brand-600">Reduced Clauses</a>
            <a href="#noun-clauses" class="block py-2 text-sm font-medium hover:text-brand-600">Noun Clauses</a>
            <a href="#verbs" class="block py-2 text-sm font-medium hover:text-brand-600">Finite vs Non-Finite Verbs</a>
            <a href="#quiz-section" class="block py-2 text-sm font-semibold text-brand-600">Interactive Quiz</a>
        </div>
    </header>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 flex flex-col md:flex-row gap-8">
        
        <!-- Sidebar Navigation -->
        <aside class="w-full md:w-64 flex-shrink-0 hidden md:block sticky top-24 h-[calc(100vh-7rem)] overflow-y-auto pr-2">
            <nav class="space-y-1">
                <p class="px-3 text-xs font-bold text-slate-400 dark:text-slate-500 uppercase tracking-wider mb-2">Core Topics</p>
                <a href="#overview" class="sidebar-link flex items-center space-x-3 px-3 py-2.5 text-sm font-medium rounded-xl text-slate-700 dark:text-slate-200 hover:bg-brand-50 dark:hover:bg-brand-900/40 hover:text-brand-600 transition">
                    <i class="fa-solid fa-sitemap w-5 text-brand-500"></i>
                    <span>Grammar Map</span>
                </a>
                <a href="#relative-clauses" class="sidebar-link flex items-center space-x-3 px-3 py-2.5 text-sm font-medium rounded-xl text-slate-700 dark:text-slate-200 hover:bg-brand-50 dark:hover:bg-brand-900/40 hover:text-brand-600 transition">
                    <i class="fa-solid fa-link w-5 text-indigo-500"></i>
                    <span>Relative Clauses</span>
                </a>
                <a href="#reduced-clauses" class="sidebar-link flex items-center space-x-3 px-3 py-2.5 text-sm font-medium rounded-xl text-slate-700 dark:text-slate-200 hover:bg-brand-50 dark:hover:bg-brand-900/40 hover:text-brand-600 transition">
                    <i class="fa-solid fa-scissors w-5 text-amber-500"></i>
                    <span>Reduced Clauses</span>
                </a>
                <a href="#noun-clauses" class="sidebar-link flex items-center space-x-3 px-3 py-2.5 text-sm font-medium rounded-xl text-slate-700 dark:text-slate-200 hover:bg-brand-50 dark:hover:bg-brand-900/40 hover:text-brand-600 transition">
                    <i class="fa-solid fa-cube w-5 text-purple-500"></i>
                    <span>Noun Clauses</span>
                </a>
                <a href="#verbs" class="sidebar-link flex items-center space-x-3 px-3 py-2.5 text-sm font-medium rounded-xl text-slate-700 dark:text-slate-200 hover:bg-brand-50 dark:hover:bg-brand-900/40 hover:text-brand-600 transition">
                    <i class="fa-solid fa-bolt w-5 text-emerald-500"></i>
                    <span>Finite vs Non-Finite</span>
                </a>

                <p class="px-3 text-xs font-bold text-slate-400 dark:text-slate-500 uppercase tracking-wider mt-6 mb-2">Practice & Testing</p>
                <a href="#sentence-dissector" class="sidebar-link flex items-center space-x-3 px-3 py-2.5 text-sm font-medium rounded-xl text-slate-700 dark:text-slate-200 hover:bg-brand-50 dark:hover:bg-brand-900/40 hover:text-brand-600 transition">
                    <i class="fa-solid fa-magnifying-glass-chart w-5 text-rose-500"></i>
                    <span>Sentence Dissector</span>
                </a>
                <a href="#quiz-section" class="sidebar-link flex items-center space-x-3 px-3 py-2.5 text-sm font-medium rounded-xl bg-gradient-to-r from-brand-600 to-indigo-600 text-white shadow-md hover:opacity-95 transition mt-2">
                    <i class="fa-solid fa-graduation-cap w-5"></i>
                    <span>Mastery Quiz</span>
                </a>
            </nav>
        </aside>

        <!-- Main Content Area -->
        <main class="flex-1 space-y-12 min-w-0">

            <section id="overview" class="relative overflow-hidden rounded-3xl bg-gradient-to-br from-brand-600 via-indigo-600 to-purple-700 text-white p-8 sm:p-10 shadow-xl">
                <div class="relative z-10 space-y-4">
                    <span class="inline-block px-3 py-1 bg-white/20 backdrop-blur-md rounded-full text-xs font-semibold uppercase tracking-wider text-brand-100">Interactive Learning Environment</span>
                    <h1 class="text-3xl sm:text-5xl font-extrabold tracking-tight leading-tight">Master English Grammar Clauses & Verbs</h1>
                    <p class="text-indigo-100 max-w-2xl text-base sm:text-lg leading-relaxed">
                        Explore essential syntax structures with live interactive sentence builders, real-time tense simulators, visual clause breakdowns, and practice quizzes.
                    </p>
                    
                    <div class="flex flex-wrap gap-3 pt-2">
                        <a href="#quiz-section" class="px-5 py-2.5 rounded-xl bg-white text-brand-700 font-bold hover:bg-indigo-50 transition shadow-lg text-sm flex items-center space-x-2">
                            <i class="fa-solid fa-play"></i>
                            <span>Take Practice Quiz</span>
                        </a>
                        <a href="#sentence-dissector" class="px-5 py-2.5 rounded-xl bg-white/10 hover:bg-white/20 border border-white/30 font-semibold transition text-sm flex items-center space-x-2">
                            <i class="fa-solid fa-wand-magic-sparkles"></i>
                            <span>Try Sentence Dissector</span>
                        </a>
                    </div>
                </div>

                <!-- Decorative Background Circles -->
                <div class="absolute -right-12 -bottom-12 w-64 h-64 bg-white/10 rounded-full blur-2xl pointer-events-none"></div>
                <div class="absolute right-1/3 -top-12 w-48 h-48 bg-indigo-400/20 rounded-full blur-xl pointer-events-none"></div>
            </section>

            <!-- Quick Key Legend -->
            <div class="glass-panel p-4 rounded-2xl flex flex-wrap items-center justify-between gap-3 text-xs sm:text-sm">
                <span class="font-bold text-slate-500 uppercase tracking-wider">Grammar Color Key:</span>
                <div class="flex flex-wrap items-center gap-2">
                    <span class="hl-subject">Subject</span>
                    <span class="hl-verb-finite">Finite Verb</span>
                    <span class="hl-verb-nonfinite">Non-Finite Verb</span>
                    <span class="hl-clause">Dependent Clause</span>
                </div>
            </div>

            <section id="relative-clauses" class="glass-panel rounded-3xl p-6 sm:p-8 space-y-6 shadow-sm">
                <div class="flex items-center space-x-3">
                    <div class="p-3 bg-indigo-100 dark:bg-indigo-950 text-indigo-600 dark:text-indigo-400 rounded-2xl text-xl">
                        <i class="fa-solid fa-link"></i>
                    </div>
                    <div>
                        <h2 class="text-2xl font-bold">1. Relative Clauses (Adjective Clauses)</h2>
                        <p class="text-sm text-slate-500 dark:text-slate-400">Modifies a preceding noun to specify or add extra details.</p>
                    </div>
                </div>

                <!-- Concept Breakdown Grid -->
                <div class="grid md:grid-cols-2 gap-6">
                    <!-- Defining -->
                    <div class="border border-slate-200 dark:border-slate-800 rounded-2xl p-5 bg-white dark:bg-slate-800/50 space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold px-2.5 py-1 rounded-md bg-emerald-100 dark:bg-emerald-950 text-emerald-700 dark:text-emerald-300">Defining (Restrictive)</span>
                            <span class="text-xs text-slate-400">Essential Details</span>
                        </div>
                        <h3 class="font-semibold text-base">Identifies WHICH noun you mean</h3>
                        <p class="text-sm text-slate-600 dark:text-slate-300">Without this clause, the sentence becomes incomplete or vague. **No commas are used.**</p>
                        <div class="p-3 rounded-xl bg-slate-100 dark:bg-slate-900 text-sm space-y-1">
                            <p class="font-mono text-xs text-slate-400">// Example:</p>
                            <p><span class="hl-subject">The student</span> <span class="hl-clause">who studied hardest</span> <span class="hl-verb-finite">passed</span> the exam.</p>
                        </div>
                        <p class="text-xs text-slate-500">✔ Can use <em>that</em> instead of <em>who/which</em>.<br>✔ Relative pronoun can be dropped if it's the object.</p>
                    </div>

                    <!-- Non-Defining -->
                    <div class="border border-slate-200 dark:border-slate-800 rounded-2xl p-5 bg-white dark:bg-slate-800/50 space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-bold px-2.5 py-1 rounded-md bg-purple-100 dark:bg-purple-950 text-purple-700 dark:text-purple-300">Non-Defining (Non-Restrictive)</span>
                            <span class="text-xs text-slate-400">Extra Details</span>
                        </div>
                        <h3 class="font-semibold text-base">Adds optional extra information</h3>
                        <p class="text-sm text-slate-600 dark:text-slate-300">The noun is already specific. **Always set off with commas.**</p>
                        <div class="p-3 rounded-xl bg-slate-100 dark:bg-slate-900 text-sm space-y-1">
                            <p class="font-mono text-xs text-slate-400">// Example:</p>
                            <p><span class="hl-subject">My brother</span>, <span class="hl-clause">who lives in Seattle</span>, <span class="hl-verb-finite">is</span> a civil engineer.</p>
                        </div>
                        <p class="text-xs text-slate-500">❌ CANNOT use <em>that</em>.<br>❌ CANNOT drop the relative pronoun.</p>
                    </div>
                </div>

                <!-- Interactive Relative Pronoun Omission Lab -->
                <div class="bg-gradient-to-r from-indigo-500/10 to-purple-500/10 border border-indigo-200 dark:border-indigo-900 rounded-2xl p-6 space-y-4">
                    <h3 class="font-bold text-lg flex items-center space-x-2">
                        <i class="fa-solid fa-lightbulb text-amber-500"></i>
                        <span>Interactive Rule: When Can You Drop the Pronoun?</span>
                    </h3>
                    <p class="text-sm text-slate-600 dark:text-slate-300">
                        In <strong>defining clauses</strong>, you can omit the relative pronoun <em>only</em> when it functions as the <strong>object</strong> of the verb in the clause.
                    </p>

                    <div id="omissionInteractive" class="space-y-4">
                        <div class="flex flex-wrap gap-2">
                            <button onclick="setOmissionExample(1)" id="omitBtn1" class="px-3 py-1.5 rounded-lg text-xs font-bold bg-indigo-600 text-white">Example 1: Object (Can Drop)</button>
                            <button onclick="setOmissionExample(2)" id="omitBtn2" class="px-3 py-1.5 rounded-lg text-xs font-bold bg-slate-200 dark:bg-slate-800 text-slate-700 dark:text-slate-300">Example 2: Subject (Cannot Drop)</button>
                        </div>

                        <div class="p-4 bg-white dark:bg-slate-900 rounded-xl border border-slate-200 dark:border-slate-800 space-y-3">
                            <p id="omitSentence" class="text-base sm:text-lg font-medium">The restaurant <span id="omitTarget" class="bg-amber-200 dark:bg-amber-900 px-1 py-0.5 rounded font-bold underline">that</span> we visited last night served delicious pasta.</p>
                            
                            <div class="flex items-center space-x-3">
                                <label class="inline-flex items-center cursor-pointer">
                                    <input type="checkbox" id="omitToggle" class="sr-only peer" onchange="togglePronounOmission()">
                                    <div class="w-11 h-6 bg-slate-300 peer-focus:outline-none rounded-full peer dark:bg-slate-700 peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-slate-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-indigo-600"></div>
                                    <span class="ml-3 text-sm font-semibold text-slate-700 dark:text-slate-300">Omit Pronoun</span>
                                </label>
                            </div>

                            <p id="omitExplanation" class="text-xs sm:text-sm text-indigo-600 dark:text-indigo-400 font-medium">
                                "that" is the object of "visited" (subject = we). Dropping it produces: "The restaurant we visited last night served delicious pasta." (Perfectly natural!)
                            </p>
                        </div>
                    </div>
                </div>
            </section>

            <section id="reduced-clauses" class="glass-panel rounded-3xl p-6 sm:p-8 space-y-6 shadow-sm">
                <div class="flex items-center space-x-3">
                    <div class="p-3 bg-amber-100 dark:bg-amber-950 text-amber-600 dark:text-amber-400 rounded-2xl text-xl">
                        <i class="fa-solid fa-scissors"></i>
                    </div>
                    <div>
                        <h2 class="text-2xl font-bold">2. Reduced Relative Clauses</h2>
                        <p class="text-sm text-slate-500 dark:text-slate-400">Shorten relative clauses by removing relative pronouns and auxiliary verbs.</p>
                    </div>
                </div>

                <div class="grid md:grid-cols-3 gap-4">
                    <div class="p-4 rounded-2xl border border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-800/40 space-y-2">
                        <span class="text-xs font-bold text-amber-600 dark:text-amber-400 uppercase">1. Active Voice</span>
                        <h4 class="font-bold text-sm">Present Participle (-ing)</h4>
                        <p class="text-xs text-slate-500">The boy <s class="text-rose-400">who is</s> <strong>sitting</strong> near the door is my cousin.</p>
                    </div>
                    <div class="p-4 rounded-2xl border border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-800/40 space-y-2">
                        <span class="text-xs font-bold text-amber-600 dark:text-amber-400 uppercase">2. Passive Voice</span>
                        <h4 class="font-bold text-sm">Past Participle (-ed / V3)</h4>
                        <p class="text-xs text-slate-500">The report <s class="text-rose-400">which was</s> <strong>submitted</strong> yesterday was approved.</p>
                    </div>
                    <div class="p-4 rounded-2xl border border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-800/40 space-y-2">
                        <span class="text-xs font-bold text-amber-600 dark:text-amber-400 uppercase">3. Preposition / Adj</span>
                        <h4 class="font-bold text-sm">Direct Phrase</h4>
                        <p class="text-xs text-slate-500">The books <s class="text-rose-400">that are</s> <strong>on the shelf</strong> belong to the instructor.</p>
                    </div>
                </div>

                <!-- Interactive Reduction Transformer -->
                <div class="bg-slate-100 dark:bg-slate-800/80 p-5 rounded-2xl space-y-4">
                    <h3 class="font-bold text-base flex items-center space-x-2">
                        <i class="fa-solid fa-wand-magic"></i>
                        <span>Clause Reduction Simulator</span>
                    </h3>
                    
                    <div class="flex flex-col sm:flex-row items-center justify-between gap-4 bg-white dark:bg-slate-900 p-4 rounded-xl border border-slate-200 dark:border-slate-700">
                        <div class="space-y-1 w-full">
                            <span class="text-xs font-semibold text-slate-400 uppercase">Original Full Clause:</span>
                            <p id="fullClauseText" class="text-base font-semibold">The painting <span class="text-purple-600 dark:text-purple-400 font-bold">that was restored by experts</span> will be displayed tomorrow.</p>
                        </div>
                        <button onclick="toggleClauseReduction()" id="reduceToggleBtn" class="w-full sm:w-auto px-5 py-2.5 bg-amber-500 hover:bg-amber-600 text-white font-bold text-xs rounded-xl shadow-md transition flex items-center justify-center space-x-2 whitespace-nowrap">
                            <i class="fa-solid fa-compress"></i>
                            <span id="reduceBtnText">Reduce Clause</span>
                        </button>
                    </div>
                </div>
            </section>

            <section id="noun-clauses" class="glass-panel rounded-3xl p-6 sm:p-8 space-y-6 shadow-sm">
                <div class="flex items-center space-x-3">
                    <div class="p-3 bg-purple-100 dark:bg-purple-950 text-purple-600 dark:text-purple-400 rounded-2xl text-xl">
                        <i class="fa-solid fa-cube"></i>
                    </div>
                    <div>
                        <h2 class="text-2xl font-bold">3. Noun Clauses</h2>
                        <p class="text-sm text-slate-500 dark:text-slate-400">A dependent clause that acts as a single noun entity.</p>
                    </div>
                </div>

                <!-- Four Roles Grid -->
                <div class="grid sm:grid-cols-2 gap-4">
                    <div class="p-4 rounded-2xl border border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-800/50 space-y-1">
                        <span class="text-xs font-bold text-purple-600 dark:text-purple-400">Subject of Sentence</span>
                        <p class="text-sm font-medium"><span class="hl-clause">What you said</span> surprised everyone.</p>
                    </div>
                    <div class="p-4 rounded-2xl border border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-800/50 space-y-1">
                        <span class="text-xs font-bold text-purple-600 dark:text-purple-400">Direct Object</span>
                        <p class="text-sm font-medium">I know <span class="hl-clause">that she will succeed</span>.</p>
                    </div>
                    <div class="p-4 rounded-2xl border border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-800/50 space-y-1">
                        <span class="text-xs font-bold text-purple-600 dark:text-purple-400">Object of Preposition</span>
                        <p class="text-sm font-medium">I was surprised by <span class="hl-clause">what she said</span>.</p>
                    </div>
                    <div class="p-4 rounded-2xl border border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-800/50 space-y-1">
                        <span class="text-xs font-bold text-purple-600 dark:text-purple-400">Subject Complement</span>
                        <p class="text-sm font-medium">The main issue is <span class="hl-clause">that we lack funding</span>.</p>
                    </div>
                </div>

                <!-- The "Something" Test Interactive Box -->
                <div class="bg-purple-900/10 border border-purple-200 dark:border-purple-800 rounded-2xl p-5 space-y-4">
                    <div class="flex items-center justify-between">
                        <h3 class="font-bold text-base text-purple-800 dark:text-purple-300">The "Something / Someone" Test Tool</h3>
                        <span class="text-xs bg-purple-200 dark:bg-purple-900 text-purple-800 dark:text-purple-200 font-bold px-2.5 py-1 rounded-full">Quick Test</span>
                    </div>
                    <p class="text-xs sm:text-sm text-slate-600 dark:text-slate-300">
                        Replace any clause with the word <strong>"SOMETHING"</strong> or <strong>"SOMEONE"</strong>. If the sentence is still grammatical, it's a <strong>Noun Clause</strong>! If it becomes nonsense, it's a Relative Clause.
                    </p>

                    <div class="space-y-3 bg-white dark:bg-slate-900 p-4 rounded-xl border border-slate-200 dark:border-slate-800">
                        <div class="flex flex-wrap gap-2 text-xs">
                            <button onclick="runSomethingTest('noun')" class="px-3 py-1 rounded-lg bg-purple-600 text-white font-bold">Test Noun Clause</button>
                            <button onclick="runSomethingTest('relative')" class="px-3 py-1 rounded-lg bg-slate-200 dark:bg-slate-800 text-slate-700 dark:text-slate-300 font-bold">Test Relative Clause</button>
                        </div>
                        <p id="somethingTestSentence" class="text-sm sm:text-base font-semibold text-slate-800 dark:text-slate-100">
                            I don't remember <span class="bg-purple-100 dark:bg-purple-950 text-purple-700 dark:text-purple-300 px-1 py-0.5 rounded font-mono">where I parked the car</span>.
                        </p>
                        <div id="somethingResult" class="p-3 bg-emerald-50 dark:bg-emerald-950/60 border border-emerald-200 dark:border-emerald-800 rounded-lg text-xs sm:text-sm text-emerald-800 dark:text-emerald-300 font-medium">
                            ➡ Test: "I don't remember <strong>SOMETHING</strong>." (Valid English! Confirming Noun Clause).
                        </div>
                    </div>
                </div>
            </section>

            <section id="verbs" class="glass-panel rounded-3xl p-6 sm:p-8 space-y-6 shadow-sm">
                <div class="flex items-center space-x-3">
                    <div class="p-3 bg-emerald-100 dark:bg-emerald-950 text-emerald-600 dark:text-emerald-400 rounded-2xl text-xl">
                        <i class="fa-solid fa-bolt"></i>
                    </div>
                    <div>
                        <h2 class="text-2xl font-bold">4. Finite vs Non-Finite Verbs</h2>
                        <p class="text-sm text-slate-500 dark:text-slate-400">Distinguishing working verbs bound by time from fixed non-finite forms.</p>
                    </div>
                </div>

                <div class="grid sm:grid-cols-2 gap-6">
                    <!-- Finite -->
                    <div class="p-5 rounded-2xl border border-emerald-200 dark:border-emerald-900 bg-emerald-500/5 space-y-3">
                        <span class="text-xs font-bold px-2.5 py-1 rounded-md bg-emerald-100 dark:bg-emerald-950 text-emerald-700 dark:text-emerald-300">Finite Verb</span>
                        <h3 class="font-bold text-lg">Tense-Bound & Subject-Driven</h3>
                        <ul class="text-xs sm:text-sm text-slate-600 dark:text-slate-300 space-y-1.5 list-disc pl-4">
                            <li>Changes form when time (past/present/future) changes.</li>
                            <li>Agrees with subject (singular vs. plural / I, He, They).</li>
                            <li>Acts as the primary main predicate verb of a sentence.</li>
                        </ul>
                    </div>

                    <!-- Non-Finite -->
                    <div class="p-5 rounded-2xl border border-amber-200 dark:border-amber-900 bg-amber-500/5 space-y-3">
                        <span class="text-xs font-bold px-2.5 py-1 rounded-md bg-amber-100 dark:bg-amber-950 text-amber-700 dark:text-amber-300">Non-Finite Verb</span>
                        <h3 class="font-bold text-lg">Fixed Form (Time Neutral)</h3>
                        <ul class="text-xs sm:text-sm text-slate-600 dark:text-slate-300 space-y-1.5 list-disc pl-4">
                            <li>Does NOT change form when tense or subject changes.</li>
                            <li>Includes <strong>Infinitives</strong> (<em>to run</em>), <strong>Gerunds</strong> (<em>running</em>), and <strong>Participles</strong> (<em>broken</em>).</li>
                        </ul>
                    </div>
                </div>

                <!-- Interactive Tense Simulator -->
                <div class="p-6 bg-slate-900 text-white rounded-2xl space-y-4 shadow-lg">
                    <div class="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-2">
                        <h3 class="font-bold text-base flex items-center space-x-2">
                            <i class="fa-solid fa-clock text-amber-400"></i>
                            <span>The Time Test Simulator</span>
                        </h3>
                        <span class="text-xs text-slate-400">Watch which verb changes form!</span>
                    </div>

                    <div class="flex flex-wrap gap-2 pt-2">
                        <button onclick="setTense('present')" id="tensePresentBtn" class="px-3 py-1.5 rounded-lg text-xs font-bold bg-emerald-600 text-white">Present Tense</button>
                        <button onclick="setTense('past')" id="tensePastBtn" class="px-3 py-1.5 rounded-lg text-xs font-bold bg-slate-800 text-slate-300">Past Tense</button>
                        <button onclick="setTense('plural')" id="tensePluralBtn" class="px-3 py-1.5 rounded-lg text-xs font-bold bg-slate-800 text-slate-300">Plural Subject</button>
                    </div>

                    <div class="p-4 bg-slate-800/90 rounded-xl border border-slate-700 space-y-2">
                        <p id="tenseSentenceDisplay" class="text-lg font-mono tracking-wide">
                            She <span class="text-emerald-400 font-bold underline underline-offset-4">wants</span> <span class="text-amber-300 font-bold">to learn</span> Spanish.
                        </p>
                        <div id="tenseAnalysis" class="text-xs text-slate-300 pt-2 border-t border-slate-700 flex flex-col sm:flex-row sm:items-center justify-between gap-2">
                            <div><span class="inline-block w-3 h-3 bg-emerald-400 rounded-full mr-1"></span><strong>wants:</strong> FINITE verb (Changes for tense/subject)</div>
                            <div><span class="inline-block w-3 h-3 bg-amber-300 rounded-full mr-1"></span><strong>to learn:</strong> NON-FINITE verb (Stays fixed)</div>
                        </div>
                    </div>
                </div>
            </section>

            <section id="sentence-dissector" class="glass-panel rounded-3xl p-6 sm:p-8 space-y-6 shadow-sm">
                <div class="flex items-center space-x-3">
                    <div class="p-3 bg-rose-100 dark:bg-rose-950 text-rose-600 dark:text-rose-400 rounded-2xl text-xl">
                        <i class="fa-solid fa-magnifying-glass-chart"></i>
                    </div>
                    <div>
                        <h2 class="text-2xl font-bold">Interactive Sentence Dissector</h2>
                        <p class="text-sm text-slate-500 dark:text-slate-400">Click individual sentences to break down clauses, subject, finite, and non-finite verbs.</p>
                    </div>
                </div>

                <div class="space-y-3">
                    <!-- Selector dropdown -->
                    <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-3">
                        <label for="dissectSelect" class="text-sm font-semibold text-slate-700 dark:text-slate-300">Select Example Sentence:</label>
                        <select id="dissectSelect" onchange="loadDissectSentence()" class="px-3 py-2 text-sm rounded-xl border border-slate-300 dark:border-slate-700 bg-white dark:bg-slate-800 font-medium">
                            <option value="0">Sentence 1: Relative Clause + Reduced Clause</option>
                            <option value="1">Sentence 2: Noun Clause as Subject</option>
                            <option value="3">Sentence 3: Non-Finite Participle + Finite Main Verb</option>
                        </select>
                    </div>

                    <!-- Dissect Display -->
                    <div class="p-6 bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-800 rounded-2xl space-y-4">
                        <div id="dissectOutput" class="text-lg sm:text-xl font-medium leading-relaxed">
                            <!-- Injected by JS -->
                        </div>

                        <div id="dissectDetails" class="grid sm:grid-cols-2 gap-3 pt-4 border-t border-slate-100 dark:border-slate-800 text-xs sm:text-sm">
                            <!-- Injected by JS -->
                        </div>
                    </div>
                </div>
            </section>

            <section id="quiz-section" class="glass-panel rounded-3xl p-6 sm:p-8 space-y-6 shadow-md border-2 border-brand-200 dark:border-brand-900">
                <div class="flex items-center justify-between">
                    <div class="flex items-center space-x-3">
                        <div class="p-3 bg-brand-600 text-white rounded-2xl text-xl shadow-md">
                            <i class="fa-solid fa-graduation-cap"></i>
                        </div>
                        <div>
                            <h2 class="text-2xl font-extrabold">Grammar Mastery Quiz</h2>
                            <p class="text-sm text-slate-500 dark:text-slate-400">Test your mastery of relative clauses, noun clauses, and verb types.</p>
                        </div>
                    </div>
                    <div class="text-right">
                        <span id="quizScoreBadge" class="px-3 py-1.5 bg-brand-100 dark:bg-brand-950 text-brand-700 dark:text-brand-300 font-extrabold text-sm rounded-xl">Score: 0 / 5</span>
                    </div>
                </div>

                <!-- Quiz Progress Bar -->
                <div class="w-full bg-slate-200 dark:bg-slate-800 h-2 rounded-full overflow-hidden">
                    <div id="quizProgressBar" class="bg-brand-600 h-full w-1/5 transition-all duration-300"></div>
                </div>

                <!-- Quiz Card -->
                <div id="quizCard" class="bg-white dark:bg-slate-900 p-6 rounded-2xl border border-slate-200 dark:border-slate-800 space-y-5">
                    <div class="flex justify-between items-center text-xs font-bold text-slate-400">
                        <span id="quizQuestionNum">Question 1 of 5</span>
                        <span id="quizCategory" class="px-2 py-0.5 rounded bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300">Relative Clauses</span>
                    </div>

                    <h3 id="quizQuestionText" class="text-base sm:text-lg font-bold text-slate-800 dark:text-slate-100">
                        <!-- Question Text -->
                    </h3>

                    <div id="quizOptionsContainer" class="space-y-3">
                        <!-- Options injected dynamically -->
                    </div>

                    <div id="quizFeedback" class="hidden p-4 rounded-xl text-xs sm:text-sm font-medium space-y-1">
                        <!-- Feedback injected dynamically -->
                    </div>

                    <div class="flex justify-end pt-2">
                        <button id="nextQuestionBtn" onclick="nextQuizQuestion()" class="hidden px-6 py-2.5 bg-brand-600 hover:bg-brand-700 text-white font-bold text-sm rounded-xl shadow-md transition">
                            Next Question <i class="fa-solid fa-arrow-right ml-1"></i>
                        </button>
                    </div>
                </div>
            </section>

        </main>
    </div>

    <script>
        // State Variables
        let currentOmissionIndex = 1;
        let isReduced = false;
        let currentQuizIndex = 0;
        let quizScore = 0;

        // Quiz Questions Array
        const quizData = [
            {
                category: "Relative Clauses",
                question: "Which sentence contains a Non-Defining (non-restrictive) relative clause?",
                options: [
                    "The teacher who helped me was very kind.",
                    "My eldest brother, who lives in Chicago, is a surgeon.",
                    "The book that you recommended was outstanding.",
                    "Students who submit work late lose points."
                ],
                correct: 1,
                explanation: "Option B is non-defining because it adds extra information set off by commas. Notice that removing the clause still leaves a full sentence."
            },
            {
                category: "Relative Pronoun Omission",
                question: "In which of the following sentences can the relative pronoun 'that' be grammatically omitted?",
                options: [
                    "The document that was emailed yesterday was lost.",
                    "The woman that called you left a voice message.",
                    "The cake that she baked was delicious.",
                    "The computer that broke down was brand new."
                ],
                correct: 2,
                explanation: "In 'The cake that she baked was delicious', 'that' is the OBJECT of 'baked' (subject = she). Therefore, 'that' can be dropped!"
            },
            {
                category: "Reduced Relative Clauses",
                question: "What is the correct reduced form of: 'The proposal that was submitted yesterday was approved'?",
                options: [
                    "The proposal submitting yesterday was approved.",
                    "The proposal submitted yesterday was approved.",
                    "The proposal to submit yesterday was approved.",
                    "The proposal was submitted yesterday was approved."
                ],
                correct: 1,
                explanation: "Because the full clause is passive ('was submitted'), removing 'that was' leaves the past participle 'submitted'."
            },
            {
                category: "Noun Clauses",
                question: "Identify the grammatical role of the noun clause in: 'What you said surprised everyone.'",
                options: [
                    "Direct Object",
                    "Subject Complement",
                    "Subject of the sentence",
                    "Object of a preposition"
                ],
                correct: 2,
                explanation: "'What you said' performs the action of surprising everyone, making it the Subject of the sentence."
            },
            {
                category: "Finite vs Non-Finite Verbs",
                question: "In the sentence 'She decided to study abroad', what type of verb is 'to study'?",
                options: [
                    "Finite verb",
                    "Non-finite verb (Infinitive)",
                    "Modal auxiliary verb",
                    "Main predicate verb"
                ],
                correct: 1,
                explanation: "'to study' is an infinitive non-finite verb. It does not change form regardless of tense (e.g. 'She decides to study')."
            }
        ];

        // Sentence Dissector Data
        const dissectData = [
            {
                sentence: `<span class="hl-subject">The scientist</span> <span class="hl-clause">[who discovered the vaccine]</span> <span class="hl-verb-finite">received</span> an award <span class="hl-verb-nonfinite">[honoring her work]</span>.`,
                details: [
                    `<strong>Subject:</strong> The scientist`,
                    `<strong>Finite Verb:</strong> received (Past Tense)`,
                    `<strong>Relative Clause:</strong> who discovered the vaccine`,
                    `<strong>Reduced Clause / Participle:</strong> honoring her work`
                ]
            },
            {
                sentence: `<span class="hl-clause">[What she announced during the conference]</span> <span class="hl-verb-finite">is</span> standard practice.`,
                details: [
                    `<strong>Subject (Noun Clause):</strong> What she announced during the conference`,
                    `<strong>Finite Verb:</strong> is (Present Tense)`,
                    `<strong>Subject Complement:</strong> standard practice`
                ]
            },
            {
                sentence: `<span class="hl-verb-nonfinite">[Having finished his homework]</span>, <span class="hl-subject">Marcus</span> <span class="hl-verb-finite">decided</span> <span class="hl-verb-nonfinite">[to relax]</span>.`,
                details: [
                    `<strong>Non-Finite Participle:</strong> Having finished his homework`,
                    `<strong>Finite Verb:</strong> decided`,
                    `<strong>Non-Finite Infinitive:</strong> to relax`
                ]
            }
        ];

        // Mobile Menu Toggle
        document.getElementById('mobileMenuBtn').addEventListener('click', () => {
            const menu = document.getElementById('mobileMenu');
            menu.classList.toggle('hidden');
        });

        // Dark Theme Toggle
        const themeToggleBtn = document.getElementById('themeToggleBtn');
        const themeIcon = document.getElementById('themeIcon');

        themeToggleBtn.addEventListener('click', () => {
            document.documentElement.classList.toggle('dark');
            if (document.documentElement.classList.contains('dark')) {
                themeIcon.className = 'fa-solid fa-sun text-amber-400';
            } else {
                themeIcon.className = 'fa-solid fa-moon';
            }
        });

        // Relative Pronoun Omission Lab Logic
        function setOmissionExample(index) {
            currentOmissionIndex = index;
            const btn1 = document.getElementById('omitBtn1');
            const btn2 = document.getElementById('omitBtn2');
            const toggle = document.getElementById('omitToggle');
            toggle.checked = false;

            if (index === 1) {
                btn1.className = 'px-3 py-1.5 rounded-lg text-xs font-bold bg-indigo-600 text-white';
                btn2.className = 'px-3 py-1.5 rounded-lg text-xs font-bold bg-slate-200 dark:bg-slate-800 text-slate-700 dark:text-slate-300';
                document.getElementById('omitSentence').innerHTML = `The restaurant <span id="omitTarget" class="bg-amber-200 dark:bg-amber-900 px-1 py-0.5 rounded font-bold underline">that</span> we visited last night served delicious pasta.`;
                document.getElementById('omitExplanation').innerText = `"that" is the object of "visited" (subject = we). It can be safely dropped!`;
            } else {
                btn2.className = 'px-3 py-1.5 rounded-lg text-xs font-bold bg-indigo-600 text-white';
                btn1.className = 'px-3 py-1.5 rounded-lg text-xs font-bold bg-slate-200 dark:bg-slate-800 text-slate-700 dark:text-slate-300';
                document.getElementById('omitSentence').innerHTML = `The document <span id="omitTarget" class="bg-amber-200 dark:bg-amber-900 px-1 py-0.5 rounded font-bold underline">that</span> was emailed to you contains all details.`;
                document.getElementById('omitExplanation').innerText = `"that" is the SUBJECT of "was emailed". It CANNOT be dropped!`;
            }
        }

        function togglePronounOmission() {
            const isChecked = document.getElementById('omitToggle').checked;
            const target = document.getElementById('omitTarget');
            const exp = document.getElementById('omitExplanation');

            if (currentOmissionIndex === 1) {
                if (isChecked) {
                    target.style.display = 'none';
                    exp.innerHTML = `✔ <strong>Grammatical!</strong> "The restaurant we visited last night served delicious pasta."`;
                } else {
                    target.style.display = 'inline';
                    exp.innerText = `"that" is the object of "visited" (subject = we). It can be safely dropped!`;
                }
            } else {
                if (isChecked) {
                    target.style.display = 'none';
                    exp.innerHTML = `❌ <strong>Ungrammatical!</strong> "The document was emailed to you contains all details" (Missing relative pronoun subject!).`;
                } else {
                    target.style.display = 'inline';
                    exp.innerText = `"that" is the SUBJECT of "was emailed". It CANNOT be dropped!`;
                }
            }
        }

        // Clause Reduction Simulator
        function toggleClauseReduction() {
            isReduced = !isReduced;
            const fullText = document.getElementById('fullClauseText');
            const btnText = document.getElementById('reduceBtnText');

            if (isReduced) {
                fullText.innerHTML = `The painting <span class="text-amber-600 dark:text-amber-400 font-bold bg-amber-100 dark:bg-amber-950 px-2 py-0.5 rounded">restored by experts</span> will be displayed tomorrow.`;
                btnText.innerText = "Expand Clause";
            } else {
                fullText.innerHTML = `The painting <span class="text-purple-600 dark:text-purple-400 font-bold">that was restored by experts</span> will be displayed tomorrow.`;
                btnText.innerText = "Reduce Clause";
            }
        }

        // The "Something" Test Tool
        function runSomethingTest(type) {
            const sentence = document.getElementById('somethingTestSentence');
            const result = document.getElementById('somethingResult');

            if (type === 'noun') {
                sentence.innerHTML = `I don't remember <span class="bg-purple-100 dark:bg-purple-950 text-purple-700 dark:text-purple-300 px-1 py-0.5 rounded font-mono">where I parked the car</span>.`;
                result.className = "p-3 bg-emerald-50 dark:bg-emerald-950/60 border border-emerald-200 dark:border-emerald-800 rounded-lg text-xs sm:text-sm text-emerald-800 dark:text-emerald-300 font-medium";
                result.innerHTML = `➡ Test: "I don't remember <strong>SOMETHING</strong>." (Valid English! Confirms Noun Clause).`;
            } else {
                sentence.innerHTML = `This is the city <span class="bg-indigo-100 dark:bg-indigo-950 text-indigo-700 dark:text-indigo-300 px-1 py-0.5 rounded font-mono">where I was born</span>.`;
                result.className = "p-3 bg-rose-50 dark:bg-rose-950/60 border border-rose-200 dark:border-rose-800 rounded-lg text-xs sm:text-sm text-rose-800 dark:text-rose-300 font-medium";
                result.innerHTML = `➡ Test: "This is the city <strong>SOMETHING</strong>." (Nonsense! "where I was born" modifies city, making it a Relative Clause).`;
            }
        }

        // Tense Simulator
        function setTense(tense) {
            const btnPres = document.getElementById('tensePresentBtn');
            const btnPast = document.getElementById('tensePastBtn');
            const btnPlur = document.getElementById('tensePluralBtn');
            const display = document.getElementById('tenseSentenceDisplay');

            btnPres.className = 'px-3 py-1.5 rounded-lg text-xs font-bold bg-slate-800 text-slate-300';
            btnPast.className = 'px-3 py-1.5 rounded-lg text-xs font-bold bg-slate-800 text-slate-300';
            btnPlur.className = 'px-3 py-1.5 rounded-lg text-xs font-bold bg-slate-800 text-slate-300';

            if (tense === 'present') {
                btnPres.className = 'px-3 py-1.5 rounded-lg text-xs font-bold bg-emerald-600 text-white';
                display.innerHTML = `She <span class="text-emerald-400 font-bold underline underline-offset-4">wants</span> <span class="text-amber-300 font-bold">to learn</span> Spanish.`;
            } else if (tense === 'past') {
                btnPast.className = 'px-3 py-1.5 rounded-lg text-xs font-bold bg-emerald-600 text-white';
                display.innerHTML = `She <span class="text-emerald-400 font-bold underline underline-offset-4">wanted</span> <span class="text-amber-300 font-bold">to learn</span> Spanish.`;
            } else {
                btnPlur.className = 'px-3 py-1.5 rounded-lg text-xs font-bold bg-emerald-600 text-white';
                display.innerHTML = `They <span class="text-emerald-400 font-bold underline underline-offset-4">want</span> <span class="text-amber-300 font-bold">to learn</span> Spanish.`;
            }
        }

        // Load Sentence Dissector
        function loadDissectSentence() {
            const idx = document.getElementById('dissectSelect').value;
            const data = dissectData[idx];
            document.getElementById('dissectOutput').innerHTML = data.sentence;

            const detailsContainer = document.getElementById('dissectDetails');
            detailsContainer.innerHTML = data.details.map(item => `<div class="p-2 bg-slate-50 dark:bg-slate-800 rounded-lg">${item}</div>`).join('');
        }

        // Quiz Module Logic
        function renderQuizQuestion() {
            const data = quizData[currentQuizIndex];
            document.getElementById('quizQuestionNum').innerText = `Question ${currentQuizIndex + 1} of ${quizData.length}`;
            document.getElementById('quizCategory').innerText = data.category;
            document.getElementById('quizQuestionText').innerText = data.question;

            const container = document.getElementById('quizOptionsContainer');
            container.innerHTML = '';

            data.options.forEach((opt, index) => {
                const button = document.createElement('button');
                button.className = `w-full text-left p-3.5 rounded-xl border border-slate-200 dark:border-slate-800 hover:border-brand-500 hover:bg-brand-50/50 dark:hover:bg-brand-950/40 text-sm font-medium transition flex items-center justify-between`;
                button.innerHTML = `<span>${opt}</span> <i class="fa-regular fa-circle text-slate-300"></i>`;
                button.onclick = () => handleQuizAnswer(index);
                container.appendChild(button);
            });

            document.getElementById('quizFeedback').className = 'hidden';
            document.getElementById('nextQuestionBtn').classList.add('hidden');
            
            // Progress Bar
            const percent = ((currentQuizIndex + 1) / quizData.length) * 100;
            document.getElementById('quizProgressBar').style.width = `${percent}%`;
        }

        function handleQuizAnswer(selectedIndex) {
            const data = quizData[currentQuizIndex];
            const options = document.getElementById('quizOptionsContainer').children;
            const feedback = document.getElementById('quizFeedback');

            for (let i = 0; i < options.length; i++) {
                options[i].disabled = true;
                if (i === data.correct) {
                    options[i].className = 'w-full text-left p-3.5 rounded-xl border-2 border-emerald-500 bg-emerald-50 dark:bg-emerald-950/50 text-emerald-900 dark:text-emerald-200 text-sm font-bold flex items-center justify-between';
                } else if (i === selectedIndex) {
                    options[i].className = 'w-full text-left p-3.5 rounded-xl border-2 border-rose-500 bg-rose-50 dark:bg-rose-950/50 text-rose-900 dark:text-rose-200 text-sm font-medium flex items-center justify-between';
                }
            }

            if (selectedIndex === data.correct) {
                quizScore++;
                feedback.className = 'p-4 rounded-xl text-xs sm:text-sm font-medium bg-emerald-100 dark:bg-emerald-950 text-emerald-800 dark:text-emerald-200 block';
                feedback.innerHTML = `<strong><i class="fa-solid fa-circle-check"></i> Correct!</strong> ${data.explanation}`;
            } else {
                feedback.className = 'p-4 rounded-xl text-xs sm:text-sm font-medium bg-rose-100 dark:bg-rose-950 text-rose-800 dark:text-rose-200 block';
                feedback.innerHTML = `<strong><i class="fa-solid fa-circle-xmark"></i> Incorrect.</strong> ${data.explanation}`;
            }

            document.getElementById('quizScoreBadge').innerText = `Score: ${quizScore} / ${quizData.length}`;
            document.getElementById('nextQuestionBtn').classList.remove('hidden');
        }

        function nextQuizQuestion() {
            if (currentQuizIndex < quizData.length - 1) {
                currentQuizIndex++;
                renderQuizQuestion();
            } else {
                // Quiz Complete
                document.getElementById('quizCard').innerHTML = `
                    <div class="text-center py-8 space-y-4">
                        <div class="w-16 h-16 bg-brand-100 dark:bg-brand-900 text-brand-600 dark:text-brand-300 rounded-full flex items-center justify-center text-3xl mx-auto">
                            <i class="fa-solid fa-trophy"></i>
                        </div>
                        <h3 class="text-2xl font-bold">Quiz Completed!</h3>
                        <p class="text-slate-500">Your final score is <strong>${quizScore} out of ${quizData.length}</strong>.</p>
                        <button onclick="restartQuiz()" class="px-6 py-2.5 bg-brand-600 text-white font-bold text-sm rounded-xl hover:bg-brand-700 transition">
                            Restart Quiz
                        </button>
                    </div>
                `;
            }
        }

        function restartQuiz() {
            currentQuizIndex = 0;
            quizScore = 0;
            document.getElementById('quizScoreBadge').innerText = `Score: 0 / ${quizData.length}`;
            location.reload();
        }

        // Initialize App on Load
        window.onload = function() {
            loadDissectSentence();
            renderQuizQuestion();
        }
    </script>
</body>
</html>
```
