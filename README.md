<!DOCTYPE html>

<html lang="es">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>BlasterMRX - Cybersecurity & Hacking Terminal</title>

    <script src="https://cdn.tailwindcss.com"></script>

    <style>

        @import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@300;400;500;600;700&display=swap');

        

        * {

            font-family: 'Fira Code', monospace;

        }

        

        body {

            background: #0a0a0a;

            color: #00ff00;

            overflow-x: hidden;

        }

        

        /* Matrix Rain Effect */

        .matrix-bg {

            position: fixed;

            top: 0;

            left: 0;

            width: 100%;

            height: 100%;

            z-index: -1;

            opacity: 0.1;

        }

        

        .matrix-char {

            position: absolute;

            color: #00ff00;

            font-size: 14px;

            animation: fall linear infinite;

        }

        

        @keyframes fall {

            0% { transform: translateY(-100vh); opacity: 1; }

            100% { transform: translateY(100vh); opacity: 0; }

        }

        

        /* Glitch Effects */

        .glitch {

            position: relative;

            animation: glitch 2s infinite;

        }

        

        .glitch::before,

        .glitch::after {

            content: attr(data-text);

            position: absolute;

            top: 0;

            left: 0;

            width: 100%;

            height: 100%;

        }

        

        .glitch::before {

            animation: glitch-1 0.5s infinite;

            color: #ff0000;

            z-index: -1;

        }

        

        .glitch::after {

            animation: glitch-2 0.5s infinite;

            color: #00ffff;

            z-index: -2;

        }

        

        @keyframes glitch {

            0%, 100% { transform: translate(0); }

            20% { transform: translate(-2px, 2px); }

            40% { transform: translate(-2px, -2px); }

            60% { transform: translate(2px, 2px); }

            80% { transform: translate(2px, -2px); }

        }

        

        @keyframes glitch-1 {

            0%, 100% { transform: translate(0); }

            20% { transform: translate(2px, -2px); }

            40% { transform: translate(-2px, 2px); }

            60% { transform: translate(-2px, -2px); }

            80% { transform: translate(2px, 2px); }

        }

        

        @keyframes glitch-2 {

            0%, 100% { transform: translate(0); }

            20% { transform: translate(-2px, 2px); }

            40% { transform: translate(2px, -2px); }

            60% { transform: translate(2px, 2px); }

            80% { transform: translate(-2px, -2px); }

        }

        

        /* Terminal Styles */

        .terminal {

            background: rgba(0, 0, 0, 0.9);

            border: 1px solid #00ff00;

            box-shadow: 0 0 20px rgba(0, 255, 0, 0.3);

        }

        

        .terminal-header {

            background: #1a1a1a;

            border-bottom: 1px solid #00ff00;

            padding: 8px 16px;

            font-size: 12px;

        }

        

        .typing {

            overflow: hidden;

            border-right: 2px solid #00ff00;

            white-space: nowrap;

            animation: typing 3s steps(40, end), blink-caret 0.75s step-end infinite;

        }

        

        @keyframes typing {

            from { width: 0; }

            to { width: 100%; }

        }

        

        @keyframes blink-caret {

            from, to { border-color: transparent; }

            50% { border-color: #00ff00; }

        }

        

        /* Hover Effects */

        .cyber-hover {

            transition: all 0.3s ease;

            border: 1px solid transparent;

        }

        

        .cyber-hover:hover {

            border-color: #00ff00;

            box-shadow: 0 0 15px rgba(0, 255, 0, 0.5);

            transform: translateY(-2px);

        }

        

        /* Neon Text */

        .neon-text {

            text-shadow: 0 0 5px #00ff00, 0 0 10px #00ff00, 0 0 15px #00ff00;

        }

        

        .neon-red {

            color: #ff0040;

            text-shadow: 0 0 5px #ff0040, 0 0 10px #ff0040, 0 0 15px #ff0040;

        }

        

        /* Scrollbar */

        ::-webkit-scrollbar {

            width: 8px;

        }

        

        ::-webkit-scrollbar-track {

            background: #1a1a1a;

        }

        

        ::-webkit-scrollbar-thumb {

            background: #00ff00;

            border-radius: 4px;

        }

        

        ::-webkit-scrollbar-thumb:hover {

            background: #00cc00;

        }

    </style>

</head>

<body>

    <!-- Matrix Background -->

    <div class="matrix-bg" id="matrix"></div>

    

    <!-- Navigation -->

    <nav class="terminal fixed top-0 w-full z-50">

        <div class="terminal-header">

            <span class="text-red-500">root@BlasterMRX:~$</span> <span class="text-yellow-400">navigation_menu.sh</span>

        </div>

        <div class="flex justify-between items-center p-4">

            <div class="flex items-center space-x-2">

                <span class="text-2xl">⚡</span>

                <h1 class="text-2xl font-bold neon-text glitch" data-text="BlasterMRX">BlasterMRX</h1>

            </div>

            <div class="hidden md:flex space-x-6">

                <button onclick="showSection('home')" class="cyber-hover px-3 py-1 rounded text-green-400 hover:text-white">[HOME]</button>

                <button onclick="showSection('noticias')" class="cyber-hover px-3 py-1 rounded text-green-400 hover:text-white">[NOTICIAS]</button>

                <button onclick="showSection('blog')" class="cyber-hover px-3 py-1 rounded text-green-400 hover:text-white">[BLOG]</button>

                <button onclick="showSection('tutoriales')" class="cyber-hover px-3 py-1 rounded text-green-400 hover:text-white">[TUTORIALES]</button>

                <button onclick="showSection('about')" class="cyber-hover px-3 py-1 rounded text-green-400 hover:text-white">[ABOUT]</button>

            </div>

            <button class="md:hidden text-green-400" onclick="toggleMobileMenu()">

                <span class="text-xl">☰</span>

            </button>

        </div>

        <div id="mobileMenu" class="hidden md:hidden bg-black border-t border-green-500 p-4">

            <button onclick="showSection('home')" class="block w-full text-left py-2 text-green-400 hover:text-white">[HOME]</button>

            <button onclick="showSection('noticias')" class="block w-full text-left py-2 text-green-400 hover:text-white">[NOTICIAS]</button>

            <button onclick="showSection('blog')" class="block w-full text-left py-2 text-green-400 hover:text-white">[BLOG]</button>

            <button onclick="showSection('tutoriales')" class="block w-full text-left py-2 text-green-400 hover:text-white">[TUTORIALES]</button>

            <button onclick="showSection('about')" class="block w-full text-left py-2 text-green-400 hover:text-white">[ABOUT]</button>

        </div>

    </nav>



    <!-- Main Content -->

    <main class="pt-32">

        <!-- Home Section -->

        <section id="home" class="section-content min-h-screen">

            <div class="max-w-6xl mx-auto px-4 py-16">

                <!-- Welcome Terminal -->

                <div class="terminal mb-12">

                    <div class="terminal-header">

                        <span class="text-red-500">root@BlasterMRX:~$</span> <span class="text-yellow-400">welcome.sh</span>

                    </div>

                    <div class="p-6">

                        <div class="typing text-2xl mb-4">Inicializando sistema BlasterMRX...</div>

                        <div class="text-green-400 mb-4">

                            <span class="text-red-500">[SYSTEM]</span> Conexión establecida<br>

                            <span class="text-yellow-400">[STATUS]</span> Todos los sistemas operativos<br>

                            <span class="text-blue-400">[ACCESS]</span> Nivel de privilegios: ROOT

                        </div>

                        <h1 class="text-4xl font-bold neon-text mb-6 glitch" data-text="BIENVENIDO AL TERMINAL">BIENVENIDO AL TERMINAL</h1>

                        <p class="text-lg text-gray-300 mb-8">

                            > Sistema de información de ciberseguridad y hacking ético<br>

                            > Acceso autorizado únicamente para propósitos educativos<br>

                            > "El conocimiento es poder, pero el poder conlleva responsabilidad"

                        </p>

                    </div>

                </div>



                <!-- Stats Grid -->

                <div class="grid md:grid-cols-3 gap-6 mb-12">

                    <div class="terminal cyber-hover p-6 text-center">

                        <div class="text-3xl neon-text mb-2">⚡</div>

                        <h3 class="text-xl font-bold text-green-400 mb-2">EXPLOITS</h3>

                        <p class="text-2xl neon-text">127</p>

                        <p class="text-sm text-gray-400">Vulnerabilidades documentadas</p>

                    </div>

                    <div class="terminal cyber-hover p-6 text-center">

                        <div class="text-3xl neon-text mb-2">🔐</div>

                        <h3 class="text-xl font-bold text-green-400 mb-2">SISTEMAS</h3>

                        <p class="text-2xl neon-text">89</p>

                        <p class="text-sm text-gray-400">Sistemas analizados</p>

                    </div>

                    <div class="terminal cyber-hover p-6 text-center">

                        <div class="text-3xl neon-text mb-2">🛡️</div>

                        <h3 class="text-xl font-bold text-green-400 mb-2">DEFENSES</h3>

                        <p class="text-2xl neon-text">256</p>

                        <p class="text-sm text-gray-400">Medidas de protección</p>

                    </div>

                </div>



                <!-- Hacker Manifesto -->

                <div class="terminal">

                    <div class="terminal-header">

                        <span class="text-red-500">root@BlasterMRX:~$</span> <span class="text-yellow-400">cat manifesto.txt</span>

                    </div>

                    <div class="p-6">

                        <h2 class="text-2xl font-bold neon-text mb-4">MANIFIESTO HACKER</h2>

                        <div class="text-gray-300 space-y-3">

                            <p>> La curiosidad es nuestro motor, el conocimiento nuestro combustible</p>

                            <p>> Creemos en la libertad de información y la transparencia</p>

                            <p>> El hacking ético protege, no destruye</p>

                            <p>> Cada vulnerabilidad encontrada es una oportunidad de mejora</p>

                            <p class="neon-red">> "Hack the planet, but make it better"</p>

                        </div>

                    </div>

                </div>

            </div>

        </section>



        <!-- Noticias Section -->

        <section id="noticias" class="section-content hidden min-h-screen">

            <div class="max-w-6xl mx-auto px-4 py-16">

                <div class="terminal mb-8">

                    <div class="terminal-header">

                        <span class="text-red-500">root@BlasterMRX:~$</span> <span class="text-yellow-400">ls -la /news/</span>

                    </div>

                    <div class="p-6">

                        <h2 class="text-3xl font-bold neon-text mb-4 glitch" data-text="NOTICIAS CYBERSEC">NOTICIAS CYBERSEC</h2>

                        <p class="text-gray-300">Últimas actualizaciones del mundo de la ciberseguridad y hacking</p>

                    </div>

                </div>



                <!-- News Categories -->

                <div class="grid md:grid-cols-4 gap-4 mb-8">

                    <button onclick="filterNews('all')" class="terminal cyber-hover p-4 text-center">

                        <div class="text-2xl mb-2">📡</div>

                        <div class="text-green-400 font-bold">TODAS</div>

                    </button>

                    <button onclick="filterNews('exploits')" class="terminal cyber-hover p-4 text-center">

                        <div class="text-2xl mb-2">⚡</div>

                        <div class="text-green-400 font-bold">EXPLOITS</div>

                    </button>

                    <button onclick="filterNews('breaches')" class="terminal cyber-hover p-4 text-center">

                        <div class="text-2xl mb-2">🚨</div>

                        <div class="text-green-400 font-bold">BRECHAS</div>

                    </button>

                    <button onclick="filterNews('tools')" class="terminal cyber-hover p-4 text-center">

                        <div class="text-2xl mb-2">🔧</div>

                        <div class="text-green-400 font-bold">TOOLS</div>

                    </button>

                </div>



                <!-- News Grid -->

                <div class="grid lg:grid-cols-2 gap-6" id="news-grid">

                    <article class="terminal cyber-hover p-6" data-category="exploits">

                        <div class="flex items-center mb-3">

                            <span class="text-red-500 mr-2">[CRITICAL]</span>

                            <span class="text-gray-400 text-sm">2024-12-15 14:30:00</span>

                        </div>

                        <h3 class="text-xl font-bold text-green-400 mb-3">Nueva vulnerabilidad 0-day en Apache Struts</h3>

                        <p class="text-gray-300 mb-4">Descubierta vulnerabilidad crítica que permite ejecución remota de código. CVE-2024-XXXX afecta versiones 2.5.x...</p>

                        <button onclick="showArticle('apache-struts')" class="text-yellow-400 hover:text-white transition-colors">[LEER_MÁS]</button>

                    </article>



                    <article class="terminal cyber-hover p-6" data-category="breaches">

                        <div class="flex items-center mb-3">

                            <span class="text-orange-500 mr-2">[BREACH]</span>

                            <span class="text-gray-400 text-sm">2024-12-15 12:15:00</span>

                        </div>

                        <h3 class="text-xl font-bold text-green-400 mb-3">Filtración masiva de datos en empresa tecnológica</h3>

                        <p class="text-gray-300 mb-4">Más de 2 millones de registros comprometidos incluyendo credenciales y datos personales...</p>

                        <button onclick="showArticle('data-breach')" class="text-yellow-400 hover:text-white transition-colors">[LEER_MÁS]</button>

                    </article>



                    <article class="terminal cyber-hover p-6" data-category="tools">

                        <div class="flex items-center mb-3">

                            <span class="text-blue-500 mr-2">[TOOL]</span>

                            <span class="text-gray-400 text-sm">2024-12-15 10:45:00</span>

                        </div>

                        <h3 class="text-xl font-bold text-green-400 mb-3">Nuevo framework de pentesting lanzado</h3>

                        <p class="text-gray-300 mb-4">HackFramework 3.0 incluye módulos avanzados para testing de aplicaciones web y móviles...</p>

                        <button onclick="showArticle('hack-framework')" class="text-yellow-400 hover:text-white transition-colors">[LEER_MÁS]</button>

                    </article>



                    <article class="terminal cyber-hover p-6" data-category="exploits">

                        <div class="flex items-center mb-3">

                            <span class="text-red-500 mr-2">[EXPLOIT]</span>

                            <span class="text-gray-400 text-sm">2024-12-15 08:20:00</span>

                        </div>

                        <h3 class="text-xl font-bold text-green-400 mb-3">Bypass de autenticación en sistemas Windows</h3>

                        <p class="text-gray-300 mb-4">Técnica permite escalada de privilegios en sistemas Windows 10/11 sin parches...</p>

                        <button onclick="showArticle('windows-bypass')" class="text-yellow-400 hover:text-white transition-colors">[LEER_MÁS]</button>

                    </article>

                </div>

            </div>

        </section>



        <!-- Blog Section -->

        <section id="blog" class="section-content hidden min-h-screen">

            <div class="max-w-6xl mx-auto px-4 py-16">

                <div class="terminal mb-8">

                    <div class="terminal-header">

                        <span class="text-red-500">root@BlasterMRX:~$</span> <span class="text-yellow-400">cat /var/log/hacking_journey.log</span>

                    </div>

                    <div class="p-6">

                        <h2 class="text-3xl font-bold neon-text mb-4 glitch" data-text="BLOG PERSONAL">BLOG PERSONAL</h2>

                        <p class="text-gray-300">Mis reflexiones, avances y descubrimientos en el mundo del hacking ético</p>

                    </div>

                </div>



                <!-- Blog Posts -->

                <div class="space-y-6">

                    <article class="terminal cyber-hover p-6">

                        <div class="flex items-center mb-3">

                            <span class="text-green-500 mr-2">[PERSONAL]</span>

                            <span class="text-gray-400 text-sm">2024-12-15</span>

                        </div>

                        <h3 class="text-2xl font-bold text-green-400 mb-3">Mi primer CTF: Lecciones aprendidas</h3>

                        <p class="text-gray-300 mb-4">

                            Ayer completé mi primer Capture The Flag y quiero compartir las lecciones más importantes que aprendí. 

                            La preparación mental es tan importante como el conocimiento técnico...

                        </p>

                        <div class="flex flex-wrap gap-2 mb-4">

                            <span class="bg-green-900 text-green-300 px-2 py-1 rounded text-sm">#CTF</span>

                            <span class="bg-blue-900 text-blue-300 px-2 py-1 rounded text-sm">#Aprendizaje</span>

                            <span class="bg-purple-900 text-purple-300 px-2 py-1 rounded text-sm">#Experiencia</span>

                        </div>

                        <button onclick="showBlogPost('first-ctf')" class="text-yellow-400 hover:text-white transition-colors">[LEER_COMPLETO]</button>

                    </article>



                    <article class="terminal cyber-hover p-6">

                        <div class="flex items-center mb-3">

                            <span class="text-blue-500 mr-2">[TÉCNICO]</span>

                            <span class="text-gray-400 text-sm">2024-12-12</span>

                        </div>

                        <h3 class="text-2xl font-bold text-green-400 mb-3">Automatizando reconocimiento con Python</h3>

                        <p class="text-gray-300 mb-4">

                            He estado trabajando en un script que automatiza la fase de reconocimiento en pentesting. 

                            Combina nmap, dirb y otras herramientas en un workflow eficiente...

                        </p>

                        <div class="flex flex-wrap gap-2 mb-4">

                            <span class="bg-yellow-900 text-yellow-300 px-2 py-1 rounded text-sm">#Python</span>

                            <span class="bg-red-900 text-red-300 px-2 py-1 rounded text-sm">#Pentesting</span>

                            <span class="bg-green-900 text-green-300 px-2 py-1 rounded text-sm">#Automatización</span>

                        </div>

                        <button onclick="showBlogPost('python-recon')" class="text-yellow-400 hover:text-white transition-colors">[LEER_COMPLETO]</button>

                    </article>



                    <article class="terminal cyber-hover p-6">

                        <div class="flex items-center mb-3">

                            <span class="text-purple-500 mr-2">[REFLEXIÓN]</span>

                            <span class="text-gray-400 text-sm">2024-12-10</span>

                        </div>

                        <h3 class="text-2xl font-bold text-green-400 mb-3">La ética en el hacking: Mi perspectiva</h3>

                        <p class="text-gray-300 mb-4">

                            Después de meses estudiando ciberseguridad, quiero reflexionar sobre la importancia de la ética 

                            en nuestro campo. El poder conlleva responsabilidad...

                        </p>

                        <div class="flex flex-wrap gap-2 mb-4">

                            <span class="bg-purple-900 text-purple-300 px-2 py-1 rounded text-sm">#Ética</span>

                            <span class="bg-blue-900 text-blue-300 px-2 py-1 rounded text-sm">#Filosofía</span>

                            <span class="bg-green-900 text-green-300 px-2 py-1 rounded text-sm">#Responsabilidad</span>

                        </div>

                        <button onclick="showBlogPost('hacking-ethics')" class="text-yellow-400 hover:text-white transition-colors">[LEER_COMPLETO]</button>

                    </article>

                </div>

            </div>

        </section>



        <!-- Tutoriales Section -->

        <section id="tutoriales" class="section-content hidden min-h-screen">

            <div class="max-w-6xl mx-auto px-4 py-16">

                <div class="terminal mb-8">

                    <div class="terminal-header">

                        <span class="text-red-500">root@BlasterMRX:~$</span> <span class="text-yellow-400">find /tutorials/ -type f -name "*.md"</span>

                    </div>

                    <div class="p-6">

                        <h2 class="text-3xl font-bold neon-text mb-4 glitch" data-text="TUTORIALES">TUTORIALES</h2>

                        <p class="text-gray-300">Guías paso a paso para dominar las artes del hacking ético</p>

                    </div>

                </div>



                <!-- Tutorial Categories -->

                <div class="grid md:grid-cols-4 gap-4 mb-8">

                    <button onclick="showTutorialCategory('ethical-hacking')" class="tutorial-tab terminal cyber-hover p-4 text-center">

                        <div class="text-2xl mb-2">⚡</div>

                        <div class="text-green-400 font-bold">HACKING ÉTICO</div>

                    </button>

                    <button onclick="showTutorialCategory('linux')" class="tutorial-tab terminal cyber-hover p-4 text-center">

                        <div class="text-2xl mb-2">🐧</div>

                        <div class="text-green-400 font-bold">LINUX</div>

                    </button>

                    <button onclick="showTutorialCategory('networks')" class="tutorial-tab terminal cyber-hover p-4 text-center">

                        <div class="text-2xl mb-2">🌐</div>

                        <div class="text-green-400 font-bold">REDES</div>

                    </button>

                    <button onclick="showTutorialCategory('programming')" class="tutorial-tab terminal cyber-hover p-4 text-center">

                        <div class="text-2xl mb-2">💻</div>

                        <div class="text-green-400 font-bold">PROGRAMACIÓN</div>

                    </button>

                </div>



                <!-- Ethical Hacking Tutorials -->

                <div id="ethical-hacking-tutorials" class="tutorial-category">

                    <div class="grid lg:grid-cols-2 gap-6">

                        <div class="terminal cyber-hover p-6">

                            <h3 class="text-xl font-bold text-green-400 mb-3">Introducción al Pentesting</h3>

                            <div class="bg-black p-4 rounded mb-4 text-sm">

                                <span class="text-red-500">root@kali:~$</span> <span class="text-yellow-400">nmap -sS -O target.com</span><br>

                                <span class="text-green-400">Starting Nmap scan...</span>

                            </div>

                            <p class="text-gray-300 mb-4">Aprende los fundamentos del pentesting ético desde cero</p>

                            <button onclick="showTutorial('pentesting-intro')" class="text-yellow-400 hover:text-white transition-colors">[INICIAR_TUTORIAL]</button>

                        </div>



                        <div class="terminal cyber-hover p-6">

                            <h3 class="text-xl font-bold text-green-400 mb-3">Web Application Security</h3>

                            <div class="bg-black p-4 rounded mb-4 text-sm">

                                <span class="text-red-500">root@kali:~$</span> <span class="text-yellow-400">sqlmap -u "http://target.com/page?id=1"</span><br>

                                <span class="text-green-400">Testing for SQL injection...</span>

                            </div>

                            <p class="text-gray-300 mb-4">Técnicas avanzadas para testing de aplicaciones web</p>

                            <button onclick="showTutorial('web-security')" class="text-yellow-400 hover:text-white transition-colors">[INICIAR_TUTORIAL]</button>

                        </div>

                    </div>

                </div>



                <!-- Linux Tutorials -->

                <div id="linux-tutorials" class="tutorial-category hidden">

                    <div class="grid lg:grid-cols-2 gap-6">

                        <div class="terminal cyber-hover p-6">

                            <h3 class="text-xl font-bold text-green-400 mb-3">Comandos Esenciales de Linux</h3>

                            <div class="bg-black p-4 rounded mb-4 text-sm">

                                <span class="text-green-400">user@linux:~$</span> <span class="text-yellow-400">ls -la | grep "config"</span><br>

                                <span class="text-white">-rw-r--r-- 1 user user 1024 Dec 15 config.txt</span>

                            </div>

                            <p class="text-gray-300 mb-4">Domina la línea de comandos de Linux para hacking</p>

                            <button onclick="showTutorial('linux-commands')" class="text-yellow-400 hover:text-white transition-colors">[INICIAR_TUTORIAL]</button>

                        </div>



                        <div class="terminal cyber-hover p-6">

                            <h3 class="text-xl font-bold text-green-400 mb-3">Configuración de Kali Linux</h3>

                            <div class="bg-black p-4 rounded mb-4 text-sm">

                                <span class="text-red-500">root@kali:~$</span> <span class="text-yellow-400">apt update && apt upgrade</span><br>

                                <span class="text-green-400">Updating package lists...</span>

                            </div>

                            <p class="text-gray-300 mb-4">Setup completo de Kali Linux para pentesting</p>

                            <button onclick="showTutorial('kali-setup')" class="text-yellow-400 hover:text-white transition-colors">[INICIAR_TUTORIAL]</button>

                        </div>

                    </div>

                </div>



                <!-- Networks Tutorials -->

                <div id="networks-tutorials" class="tutorial-category hidden">

                    <div class="grid lg:grid-cols-2 gap-6">

                        <div class="terminal cyber-hover p-6">

                            <h3 class="text-xl font-bold text-green-400 mb-3">Análisis de Tráfico de Red</h3>

                            <div class="bg-black p-4 rounded mb-4 text-sm">

                                <span class="text-red-500">root@kali:~$</span> <span class="text-yellow-400">wireshark -i eth0</span><br>

                                <span class="text-green-400">Capturing packets on eth0...</span>

                            </div>

                            <p class="text-gray-300 mb-4">Aprende a analizar tráfico de red con Wireshark</p>

                            <button onclick="showTutorial('network-analysis')" class="text-yellow-400 hover:text-white transition-colors">[INICIAR_TUTORIAL]</button>

                        </div>



                        <div class="terminal cyber-hover p-6">

                            <h3 class="text-xl font-bold text-green-400 mb-3">Wireless Hacking</h3>

                            <div class="bg-black p-4 rounded mb-4 text-sm">

                                <span class="text-red-500">root@kali:~$</span> <span class="text-yellow-400">aircrack-ng -w wordlist.txt capture.cap</span><br>

                                <span class="text-green-400">Cracking WPA handshake...</span>

                            </div>

                            <p class="text-gray-300 mb-4">Técnicas de auditoría de redes inalámbricas</p>

                            <button onclick="showTutorial('wireless-hacking')" class="text-yellow-400 hover:text-white transition-colors">[INICIAR_TUTORIAL]</button>

                        </div>

                    </div>

                </div>



                <!-- Programming Tutorials -->

                <div id="programming-tutorials" class="tutorial-category hidden">

                    <div class="grid lg:grid-cols-2 gap-6">

                        <div class="terminal cyber-hover p-6">

                            <h3 class="text-xl font-bold text-green-400 mb-3">Python para Hacking</h3>

                            <div class="bg-black p-4 rounded mb-4 text-sm">

                                <span class="text-blue-400">import</span> <span class="text-yellow-400">socket</span><br>

                                <span class="text-green-400">s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)</span><br>

                                <span class="text-green-400">s.connect(("target.com", 80))</span>

                            </div>

                            <p class="text-gray-300 mb-4">Desarrolla herramientas de hacking con Python</p>

                            <button onclick="showTutorial('python-hacking')" class="text-yellow-400 hover:text-white transition-colors">[INICIAR_TUTORIAL]</button>

                        </div>



                        <div class="terminal cyber-hover p-6">

                            <h3 class="text-xl font-bold text-green-400 mb-3">JavaScript para Bug Bounty</h3>

                            <div class="bg-black p-4 rounded mb-4 text-sm">

                                <span class="text-purple-400">function</span> <span class="text-yellow-400">xssPayload</span><span class="text-white">() {</span><br>

                                <span class="text-green-400">  alert('XSS Vulnerability Found!');</span><br>

                                <span class="text-white">}</span>

                            </div>

                            <p class="text-gray-300 mb-4">Explota vulnerabilidades web con JavaScript</p>

                            <button onclick="showTutorial('js-bugbounty')" class="text-yellow-400 hover:text-white transition-colors">[INICIAR_TUTORIAL]</button>

                        </div>

                    </div>

                </div>

            </div>

        </section>



        <!-- About Section -->

        <section id="about" class="section-content hidden min-h-screen">

            <div class="max-w-6xl mx-auto px-4 py-16">

                <div class="terminal mb-8">

                    <div class="terminal-header">

                        <span class="text-red-500">root@BlasterMRX:~$</span> <span class="text-yellow-400">whoami && cat /etc/passwd | grep BlasterMRX</span>

                    </div>

                    <div class="p-6">

                        <h2 class="text-3xl font-bold neon-text mb-4 glitch" data-text="ABOUT BlasterMRX">ABOUT BlasterMRX</h2>

                        <p class="text-gray-300">Información del sistema y filosofía hacker</p>

                    </div>

                </div>



                <div class="grid lg:grid-cols-2 gap-8">

                    <!-- Profile -->

                    <div class="terminal p-6">

                        <div class="terminal-header mb-4">

                            <span class="text-red-500">root@BlasterMRX:~$</span> <span class="text-yellow-400">cat profile.txt</span>

                        </div>

                        <div class="text-center mb-6">

                            <div class="w-32 h-32 mx-auto mb-4 bg-gradient-to-r from-green-400 to-blue-500 rounded-full flex items-center justify-center text-4xl">

                                👨‍💻

                            </div>

                            <h3 class="text-2xl font-bold neon-text">BlasterMRX</h3>

                            <p class="text-gray-400">Ethical Hacker & Cybersecurity Enthusiast</p>

                        </div>

                        

                        <div class="space-y-3 text-sm">

                            <div><span class="text-green-400">Status:</span> <span class="text-white">Active</span></div>

                            <div><span class="text-green-400">Level:</span> <span class="text-white">Intermediate</span></div>

                            <div><span class="text-green-400">Specialization:</span> <span class="text-white">Web App Security</span></div>

                            <div><span class="text-green-400">Location:</span> <span class="text-white">Cyberspace</span></div>

                            <div><span class="text-green-400">Mission:</span> <span class="text-white">Secure the digital world</span></div>

                        </div>

                    </div>



                    <!-- Skills -->

                    <div class="terminal p-6">

                        <div class="terminal-header mb-4">

                            <span class="text-red-500">root@BlasterMRX:~$</span> <span class="text-yellow-400">ls -la /skills/</span>

                        </div>

                        <div class="space-y-4">

                            <div>

                                <div class="flex justify-between mb-1">

                                    <span class="text-green-400">Penetration Testing</span>

                                    <span class="text-white">85%</span>

                                </div>

                                <div class="w-full bg-gray-700 rounded-full h-2">

                                    <div class="bg-green-500 h-2 rounded-full" style="width: 85%"></div>

                                </div>

                            </div>

                            <div>

                                <div class="flex justify-between mb-1">

                                    <span class="text-green-400">Python Scripting</span>

                                    <span class="text-white">90%</span>

                                </div>

                                <div class="w-full bg-gray-700 rounded-full h-2">

                                    <div class="bg-green-500 h-2 rounded-full" style="width: 90%"></div>

                                </div>

                            </div>

                            <div>

                                <div class="flex justify-between mb-1">

                                    <span class="text-green-400">Linux Administration</span>

                                    <span class="text-white">80%</span>

                                </div>

                                <div class="w-full bg-gray-700 rounded-full h-2">

                                    <div class="bg-green-500 h-2 rounded-full" style="width: 80%"></div>

                                </div>

                            </div>

                            <div>

                                <div class="flex justify-between mb-1">

                                    <span class="text-green-400">Web Security</span>

                                    <span class="text-white">88%</span>

                                </div>

                                <div class="w-full bg-gray-700 rounded-full h-2">

                                    <div class="bg-green-500 h-2 rounded-full" style="width: 88%"></div>

                                </div>

                            </div>

                        </div>

                    </div>

                </div>



                <!-- Philosophy -->

                <div class="terminal mt-8">

                    <div class="terminal-header">

                        <span class="text-red-500">root@BlasterMRX:~$</span> <span class="text-yellow-400">cat philosophy.md</span>

                    </div>

                    <div class="p-6">

                        <h3 class="text-2xl font-bold neon-text mb-4">FILOSOFÍA HACKER</h3>

                        <div class="text-gray-300 space-y-4">

                            <p>> <span class="text-green-400">Transparencia:</span> El conocimiento debe ser libre y accesible</p>

                            <p>> <span class="text-green-400">Responsabilidad:</span> Con gran poder viene gran responsabilidad</p>

                            <p>> <span class="text-green-400">Mejora continua:</span> Cada día es una oportunidad para aprender</p>

                            <p>> <span class="text-green-400">Ética:</span> Usar habilidades para proteger, no para dañar</p>

                            <p>> <span class="text-green-400">Comunidad:</span> Compartir conocimiento fortalece a todos</p>

                        </div>

                    </div>

                </div>



                <!-- Contact -->

                <div class="terminal mt-8">

                    <div class="terminal-header">

                        <span class="text-red-500">root@BlasterMRX:~$</span> <span class="text-yellow-400">cat contact.info</span>

                    </div>

                    <div class="p-6">

                        <h3 class="text-2xl font-bold neon-text mb-4">CONTACTO</h3>

                        <div class="grid md:grid-cols-2 gap-6">

                            <div>

                                <h4 class="text-green-400 font-bold mb-2">Canales Seguros:</h4>

                                <div class="space-y-2 text-sm">

                                    <div><span class="text-gray-400">Email:</span> <span class="text-white">blaster@protonmail.com</span></div>

                                    <div><span class="text-gray-400">PGP Key:</span> <span class="text-white">0x1234567890ABCDEF</span></div>

                                    <div><span class="text-gray-400">Signal:</span> <span class="text-white">+1-XXX-XXX-XXXX</span></div>

                                </div>

                            </div>

                            <div>

                                <h4 class="text-green-400 font-bold mb-2">Redes Sociales:</h4>

                                <div class="space-y-2 text-sm">

                                    <div><span class="text-gray-400">GitHub:</span> <span class="text-white">github.com/BlasterMRX</span></div>

                                    <div><span class="text-gray-400">Twitter:</span> <span class="text-white">@BlasterMRX_Sec</span></div>

                                    <div><span class="text-gray-400">LinkedIn:</span> <span class="text-white">linkedin.com/in/blastermrx</span></div>

                                </div>

                            </div>

                        </div>

                    </div>

                </div>

            </div>

        </section>

    </main>



    <!-- Footer -->

    <footer class="terminal mt-16">

        <div class="terminal-header">

            <span class="text-red-500">root@BlasterMRX:~$</span> <span class="text-yellow-400">cat footer.txt</span>

        </div>

        <div class="max-w-6xl mx-auto px-4 py-8">

            <div class="grid md:grid-cols-3 gap-8">

                <div>

                    <h3 class="text-xl font-bold neon-text mb-4">BlasterMRX Terminal</h3>

                    <p class="text-gray-400">Dedicated to ethical hacking and cybersecurity education</p>

                </div>

                <div>

                    <h4 class="font-bold text-green-400 mb-4">Quick Access</h4>

                    <div class="space-y-2 text-sm">

                        <button onclick="showSection('noticias')" class="block text-gray-400 hover:text-white transition-colors">[NOTICIAS]</button>

                        <button onclick="showSection('tutoriales')" class="block text-gray-400 hover:text-white transition-colors">[TUTORIALES]</button>

                        <button onclick="showSection('blog')" class="block text-gray-400 hover:text-white transition-colors">[BLOG]</button>

                    </div>

                </div>

                <div>

                    <h4 class="font-bold text-green-400 mb-4">System Status</h4>

                    <div class="space-y-1 text-sm">

                        <div><span class="text-green-400">●</span> All systems operational</div>

                        <div><span class="text-green-400">●</span> Security protocols active</div>

                        <div><span class="text-green-400">●</span> Firewall enabled</div>

                    </div>

                </div>

            </div>

            <div class="border-t border-green-500 mt-8 pt-4 text-center text-gray-400 text-sm">

                <p>&copy; 2024 BlasterMRX. All rights reserved. | "Knowledge is power, use it responsibly"</p>

            </div>

        </div>

    </footer>



    <script>

        // Matrix Rain Effect

        function createMatrixRain() {

            const matrix = document.getElementById('matrix');

            const chars = '01アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン';

            

            for (let i = 0; i < 50; i++) {

                const char = document.createElement('div');

                char.className = 'matrix-char';

                char.textContent = chars[Math.floor(Math.random() * chars.length)];

                char.style.left = Math.random() * 100 + '%';

                char.style.animationDuration = (Math.random() * 3 + 2) + 's';

                char.style.animationDelay = Math.random() * 2 + 's';

                matrix.appendChild(char);

            }

        }



        // Navigation

        function showSection(sectionId) {

            const sections = document.querySelectorAll('.section-content');

            sections.forEach(section => section.classList.add('hidden'));

            document.getElementById(sectionId).classList.remove('hidden');

            document.getElementById('mobileMenu').classList.add('hidden');

            window.scrollTo(0, 0);

        }



        function toggleMobileMenu() {

            const menu = document.getElementById('mobileMenu');

            menu.classList.toggle('hidden');

        }



        // Tutorial Categories

        function showTutorialCategory(category) {

            const categories = document.querySelectorAll('.tutorial-category');

            categories.forEach(cat => cat.classList.add('hidden'));

            document.getElementById(category + '-tutorials').classList.remove('hidden');

            

            // Update tab styling

            const tabs = document.querySelectorAll('.tutorial-tab');

            tabs.forEach(tab => tab.classList.remove('bg-green-900'));

            event.target.classList.add('bg-green-900');

        }



        // News Filtering

        function filterNews(category) {

            const articles = document.querySelectorAll('#news-grid article');

            articles.forEach(article => {

                if (category === 'all' || article.dataset.category === category) {

                    article.style.display = 'block';

                } else {

                    article.style.display = 'none';

                }

            });

        }



        // Show Article

        function showArticle(articleId) {

            const articles = {

                'apache-struts': 'Vulnerabilidad crítica en Apache Struts permite ejecución remota de código...',

                'data-breach': 'Filtración masiva expone datos de 2 millones de usuarios...',

                'hack-framework': 'Nuevo framework revoluciona las pruebas de penetración...',

                'windows-bypass': 'Técnica permite escalada de privilegios en Windows...'

            };

            

            alert(`[ARTÍCULO COMPLETO]\n\n${articles[articleId] || 'Contenido del artículo...'}`);

        }



        // Show Blog Post

        function showBlogPost(postId) {

            const posts = {

                'first-ctf': 'Mi experiencia en mi primer CTF fue increíble. Aprendí que la preparación mental es tan importante como el conocimiento técnico...',

                'python-recon': 'He desarrollado un script en Python que automatiza la fase de reconocimiento combinando múltiples herramientas...',

                'hacking-ethics': 'La ética en el hacking es fundamental. Debemos usar nuestras habilidades para proteger, no para dañar...'

            };

            

            alert(`[BLOG POST COMPLETO]\n\n${posts[postId] || 'Contenido del post...'}`);

        }



        // Show Tutorial

        function showTutorial(tutorialId) {

            const tutorials = {

                'pentesting-intro': 'Tutorial completo de introducción al pentesting ético...',

                'web-security': 'Aprende técnicas avanzadas de seguridad en aplicaciones web...',

                'linux-commands': 'Domina los comandos esenciales de Linux para hacking...',

                'python-hacking': 'Desarrolla herramientas de hacking con Python...'

            };

            

            alert(`[TUTORIAL INICIADO]\n\n${tutorials[tutorialId] || 'Contenido del tutorial...'}`);

        }



        // Initialize

        document.addEventListener('DOMContentLoaded', function() {

            createMatrixRain();

            showSection('home');

            

            // Auto-refresh matrix effect

            setInterval(createMatrixRain, 10000);

            

            // Initialize first tutorial category

            showTutorialCategory('ethical-hacking');

        });



        // Typing effect for dynamic content

        function typeWriter(element, text, speed = 50) {

            let i = 0;

            element.innerHTML = '';

            function type() {

                if (i < text.length) {

                    element.innerHTML += text.charAt(i);

                    i++;

                    setTimeout(type, speed);

                }

            }

            type();

        }



        // Add glitch effect to random elements

        setInterval(() => {

            const glitchElements = document.querySelectorAll('.glitch');

            const randomElement = glitchElements[Math.floor(Math.random() * glitchElements.length)];

            if (randomElement) {

                randomElement.style.animation = 'none';

                setTimeout(() => {

                    randomElement.style.animation = 'glitch 2s infinite';

                }, 100);

            }

        }, 5000);

    </script>

<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9662993110d0dd24',t:'MTc1MzY4NzA2My4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>

</html>
