# Legacy-Finance-Academy<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Legacy Finance Academy | Educación Financiera Premium</title>
    <!-- Fuentes Modernas y Minimalistas -->
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;700;800&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --bg-base: #060a08;
            --bg-section: #0a110d;
            --glass-bg: rgba(16, 30, 22, 0.5);
            --glass-border: rgba(212, 175, 55, 0.15);
            --primary: #00F5A0; 
            --accent-gold: #D4AF37;
            --accent-gold-gradient: linear-gradient(135deg, #F3E7E9 0%, #D4AF37 100%);
            --text-main: #FFFFFF;
            --text-muted: #9bb1a5;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Plus Jakarta Sans', sans-serif; }
        html { scroll-behavior: smooth; }
        body { background-color: var(--bg-base); color: var(--text-main); line-height: 1.6; }

        /* NAVBAR FIXED */
        nav {
            background: rgba(6, 10, 8, 0.85); backdrop-filter: blur(15px); -webkit-backdrop-filter: blur(15px);
            border-bottom: 1px solid var(--glass-border); padding: 15px 5%; position: fixed; width: 100%; top: 0; z-index: 1000;
            display: flex; justify-content: space-between; align-items: center;
        }
        .logo-text { font-size: 1.4rem; font-weight: 800; color: white; display: flex; align-items: center; gap: 10px; }
        .logo-text i { color: var(--accent-gold); }
        .nav-links a { color: var(--text-main); text-decoration: none; margin-left: 20px; font-size: 0.9rem; font-weight: 500; transition: color 0.3s; }
        .nav-links a:hover { color: var(--accent-gold); }

        /* HERO SECTION */
        .hero {
            padding: 140px 5% 80px; text-align: center; background: radial-gradient(circle at 50% 0%, rgba(27, 67, 50, 0.4) 0%, var(--bg-base) 60%);
        }
        .hero h1 { font-size: 3rem; font-weight: 800; margin-bottom: 15px; line-height: 1.2; }
        .hero h1 span { background: var(--accent-gold-gradient); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
        .hero p { font-size: 1.1rem; color: var(--text-muted); max-width: 600px; margin: 0 auto 40px; }

        /* SELECTOR DE NIVELES (TABS) */
        .profile-tabs { display: flex; justify-content: center; gap: 15px; flex-wrap: wrap; margin-bottom: 30px; }
        .tab-btn {
            background: rgba(255,255,255,0.03); border: 1px solid rgba(255,255,255,0.1); color: var(--text-muted);
            padding: 14px 28px; border-radius: 40px; cursor: pointer; font-weight: 600; font-size: 1rem;
            transition: all 0.3s ease; display: flex; align-items: center; gap: 10px;
        }
        .tab-btn:hover { background: rgba(255,255,255,0.08); }
        .tab-btn.active {
            background: rgba(212, 175, 55, 0.1); border-color: var(--accent-gold); color: var(--accent-gold);
            box-shadow: 0 0 20px rgba(212, 175, 55, 0.2); transform: translateY(-3px);
        }

        /* THEORY SECTION (SPLIT LAYOUT) */
        .theory-section { padding: 80px 5%; background: var(--bg-section); border-top: 1px solid rgba(255,255,255,0.02); border-bottom: 1px solid rgba(255,255,255,0.02); }
        .theory-grid { display: grid; grid-template-columns: 1fr; gap: 40px; max-width: 1100px; margin: auto; align-items: center; }
        @media(min-width: 900px) { .theory-grid { grid-template-columns: 1fr 1fr; } }
        
        .theory-image-container { position: relative; border-radius: 20px; overflow: hidden; box-shadow: 0 20px 50px rgba(0,0,0,0.5); }
        .theory-image-container::after { content: ''; position: absolute; top: 0; left: 0; width: 100%; height: 100%; box-shadow: inset 0 0 0 1px rgba(255,255,255,0.1); border-radius: 20px; pointer-events: none; }
        .theory-image { width: 100%; height: 450px; object-fit: cover; display: block; transition: opacity 0.5s ease; }
        
        .theory-content h2 { font-size: 2.2rem; margin-bottom: 25px; color: white; }
        .theory-card { background: rgba(0,0,0,0.3); border-left: 3px solid var(--accent-gold); padding: 20px; margin-bottom: 20px; border-radius: 0 12px 12px 0; }
        .theory-card h3 { font-size: 1.1rem; color: var(--accent-gold); margin-bottom: 8px; }
        .theory-card p { font-size: 0.95rem; color: var(--text-muted); }

        /* TOOLS SECTION (DASHBOARD) */
        .tools-section { padding: 80px 5%; max-width: 1200px; margin: auto; }
        .section-header { text-align: center; margin-bottom: 50px; }
        .section-header h2 { font-size: 2.2rem; color: white; }
        .section-header p { color: var(--text-muted); margin-top: 10px; }
        
        .dashboard-grid { display: grid; grid-template-columns: 1fr; gap: 30px; }
        @media(min-width: 800px) { .dashboard-grid { grid-template-columns: 1fr 1fr; } }

        /* GLASS CARDS */
        .glass-card {
            background: var(--glass-bg); backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.05); border-radius: 24px; padding: 35px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.4); transition: transform 0.3s ease;
        }
        .glass-card:hover { transform: translateY(-5px); border-color: rgba(212, 175, 55, 0.2); }
        .card-header { display: flex; align-items: center; gap: 15px; margin-bottom: 25px; }
        .icon-box { width: 50px; height: 50px; border-radius: 12px; background: rgba(212, 175, 55, 0.1); display: flex; justify-content: center; align-items: center; color: var(--accent-gold); font-size: 1.3rem; }
        .card-header h3 { font-size: 1.3rem; color: white; }

        /* FORMS & BUTTONS */
        .input-group { margin-bottom: 20px; }
        .input-group label { display: block; font-size: 0.85rem; color: var(--text-muted); margin-bottom: 8px; text-transform: uppercase; letter-spacing: 1px; }
        .input-with-icon { position: relative; }
        .input-with-icon i { position: absolute; left: 18px; top: 50%; transform: translateY(-50%); color: var(--text-muted); }
        .input-with-icon input { width: 100%; background: rgba(0,0,0,0.4); border: 1px solid #1a2a22; color: white; padding: 15px 15px 15px 45px; border-radius: 12px; font-size: 1rem; transition: 0.3s; }
        .input-with-icon input:focus { border-color: var(--accent-gold); outline: none; }

        .btn-primary { width: 100%; background: var(--accent-gold); color: #000; border: none; padding: 15px; border-radius: 12px; font-weight: 700; font-size: 1rem; cursor: pointer; transition: 0.3s; margin-top: 10px; }
        .btn-primary:hover { box-shadow: 0 0 20px rgba(212, 175, 55, 0.3); transform: translateY(-2px); }

        /* DATA DISPLAYS */
        .data-display { margin-top: 25px; padding: 20px; background: rgba(0,0,0,0.3); border-radius: 16px; border: 1px solid #1a2a22; }
        .data-row { display: flex; justify-content: space-between; margin-bottom: 12px; font-size: 0.95rem; }
        .data-row span:last-child { font-weight: 700; color: white; }
        .val-gold { color: var(--accent-gold) !important; }
        .progress-bar-bg { width: 100%; height: 8px; background: #1a2a22; border-radius: 10px; overflow: hidden; margin-top: 10px; }
        .progress-fill { height: 100%; background: var(--accent-gold); width: 0%; transition: width 1s ease; }

        /* FOOTER */
        footer { text-align: center; padding: 40px 20px; background: #040705; color: var(--text-muted); font-size: 0.85rem; border-top: 1px solid rgba(255,255,255,0.05); }

        /* CHATBOT FLOATING */
        .fab-chat { position: fixed; bottom: 30px; right: 30px; width: 65px; height: 65px; background: var(--accent-gold); border-radius: 50%; display: flex; justify-content: center; align-items: center; font-size: 1.8rem; color: #000; box-shadow: 0 10px 30px rgba(212, 175, 55, 0.3); cursor: pointer; z-index: 1000; transition: 0.3s; }
        .fab-chat:hover { transform: scale(1.1); }
        .chat-window { position: fixed; bottom: 110px; right: 30px; width: 350px; background: rgba(10, 18, 14, 0.98); backdrop-filter: blur(20px); border: 1px solid var(--accent-gold); border-radius: 20px; overflow: hidden; z-index: 1000; display: none; flex-direction: column; height: 450px; box-shadow: 0 20px 50px rgba(0,0,0,0.8); }
        .chat-head { padding: 18px; background: rgba(0,0,0,0.5); border-bottom: 1px solid #1a2a22; display: flex; justify-content: space-between; align-items: center; }
        .chat-body { flex: 1; padding: 15px; overflow-y: auto; display: flex; flex-direction: column; gap: 12px; font-size: 0.9rem; }
        .bubble { padding: 12px 16px; border-radius: 15px; max-width: 85%; line-height: 1.4; }
        .bubble.ai { background: #121e17; color: white; align-self: flex-start; border-bottom-left-radius: 2px; border: 1px solid #1a2a22; }
        .bubble.user { background: var(--accent-gold); color: #000; align-self: flex-end; border-bottom-right-radius: 2px; font-weight: 500; }
        .chat-foot { padding: 12px; background: rgba(0,0,0,0.5); border-top: 1px solid #1a2a22; display: flex; gap: 10px; }
        .chat-foot input { flex: 1; background: #080f0c; border: 1px solid #1a2a22; color: white; padding: 10px 15px; border-radius: 20px; outline: none; }
        .chat-foot button { background: var(--accent-gold); border: none; width: 40px; height: 40px; border-radius: 50%; color: #000; cursor: pointer; }
    </style>
</head>
<body>

    <!-- NAVEGACIÓN -->
    <nav>
        <div class="logo-text"><i class="fas fa-gem"></i> Legacy Finance</div>
        <div class="nav-links d-none d-md-block">
            <a href="#hero">Inicio</a>
            <a href="#teoria">Aprende</a>
            <a href="#herramientas">Simuladores</a>
        </div>
    </nav>

    <!-- INICIO (HERO) -->
    <section class="hero" id="hero">
        <h1>Construye tu <span>Libertad Financiera</span><br>desde Hoy Mismo.</h1>
        <p>Una academia interactiva y minimalista diseñada para que aprendas a dominar el dinero sin importar tu edad. Elige tu perfil y comencemos.</p>
        
        <div class="profile-tabs">
            <button class="tab-btn active" onclick="changeProfile('junior')"><i class="fas fa-seedling"></i> Nivel Semilla (Junior)</button>
            <button class="tab-btn" onclick="changeProfile('emprende')"><i class="fas fa-briefcase"></i> Nivel Brote (Emprendedor)</button>
            <button class="tab-btn" onclick="changeProfile('inversion')"><i class="fas fa-chart-line"></i> Nivel Legado (Inversionista)</button>
        </div>
    </section>

    <!-- TEORÍA MINIMALISTA E INTUITIVA -->
    <section class="theory-section" id="teoria">
        <div class="theory-grid">
            <div class="theory-image-container">
                <!-- Imágenes de Unsplash minimalistas y de alta calidad -->
                <img id="theory-img" class="theory-image" src="https://images.unsplash.com/photo-1579621970563-ebec7560ff3e?auto=format&fit=crop&w=800&q=80" alt="Finanzas Minimalistas">
            </div>
            <div class="theory-content">
                <h2 id="theory-title">La Magia del Ahorro 🌱</h2>
                <div id="theory-cards-container">
                    <!-- Dinámico por JS -->
                </div>
            </div>
        </div>
    </section>

    <!-- HERRAMIENTAS / DASHBOARD -->
    <section class="tools-section" id="herramientas">
        <div class="section-header">
            <h2>Laboratorio de Simuladores Financieros</h2>
            <p>Pon en práctica la teoría. Usa nuestras calculadoras interactivas para planificar tu futuro económico.</p>
        </div>

        <div class="dashboard-grid">
            
            <!-- 1. MATRIZ PRESUPUESTO -->
            <div class="glass-card">
                <div class="card-header">
                    <div class="icon-box"><i class="fas fa-wallet"></i></div>
                    <h3>Regla 50/30/20</h3>
                </div>
                <div class="input-group">
                    <label>Tus Ingresos Totales (Soles):</label>
                    <div class="input-with-icon"><i class="fas fa-money-bill-wave"></i><input type="number" id="budget-input" value="100"></div>
                </div>
                <button class="btn-primary" onclick="calcBudget()">Calcular Mi Presupuesto</button>

                <div class="data-display" id="budget-res" style="display:none;">
                    <div class="data-row"><span>🛠️ Necesidades (50%):</span><span id="res-50">S/ 0</span></div>
                    <div class="data-row"><span>🍿 Deseos (30%):</span><span id="res-30">S/ 0</span></div>
                    <div class="data-row"><span>🐷 Ahorro Intocable (20%):</span><span class="val-gold" id="res-20">S/ 0</span></div>
                    <div style="height: 160px; margin-top: 15px;"><canvas id="chartBudget"></canvas></div>
                </div>
            </div>

            <!-- 2. PLANIFICADOR DE METAS (NUEVO) -->
            <div class="glass-card">
                <div class="card-header">
                    <div class="icon-box"><i class="fas fa-bullseye"></i></div>
                    <h3>Planificador de Metas</h3>
                </div>
                <div class="input-group">
                    <label>¿Qué deseas comprar/lograr?</label>
                    <div class="input-with-icon"><i class="fas fa-star"></i><input type="text" id="goal-name" placeholder="Ej. Bicicleta, Laptop, Inventario"></div>
                </div>
                <div style="display: flex; gap: 15px;">
                    <div class="input-group" style="flex: 1;">
                        <label>Costo (S/):</label>
                        <div class="input-with-icon"><i class="fas fa-tag"></i><input type="number" id="goal-cost" value="500"></div>
                    </div>
                    <div class="input-group" style="flex: 1;">
                        <label>Ahorro Mensual (S/):</label>
                        <div class="input-with-icon"><i class="fas fa-piggy-bank"></i><input type="number" id="goal-save" value="50"></div>
                    </div>
                </div>
                <button class="btn-primary" onclick="calcGoal()">Planear mi Ruta</button>

                <div class="data-display" id="goal-res" style="display:none;">
                    <h4 id="res-goal-title" style="color: white; margin-bottom: 10px;">Meta: ---</h4>
                    <div class="data-row"><span>Tiempo Estimado de Ahorro:</span><span class="val-gold" id="res-goal-time">0 Meses</span></div>
                    <p style="font-size: 0.8rem; color: var(--text-muted); margin-top: 5px;">Progreso simulado (1 mes completado):</p>
                    <div class="progress-bar-bg"><div class="progress-fill" id="res-goal-bar"></div></div>
                </div>
            </div>

            <!-- 3. INTERÉS COMPUESTO -->
            <div class="glass-card">
                <div class="card-header">
                    <div class="icon-box"><i class="fas fa-chart-line"></i></div>
                    <h3>El Poder del Interés Compuesto</h3>
                </div>
                <div class="input-group">
                    <label>Ahorro / Inversión Inicial (S/):</label>
                    <div class="input-with-icon"><i class="fas fa-seedling"></i><input type="number" id="comp-principal" value="100"></div>
                </div>
                <div style="display: flex; gap: 15px;">
                    <div class="input-group" style="flex: 1;">
                        <label>Tasa Anual (%):</label>
                        <div class="input-with-icon"><i class="fas fa-percentage"></i><input type="number" id="comp-rate" value="10"></div>
                    </div>
                    <div class="input-group" style="flex: 1;">
                        <label>Años a esperar:</label>
                        <div class="input-with-icon"><i class="fas fa-calendar"></i><input type="number" id="comp-years" value="5"></div>
                    </div>
                </div>
                <button class="btn-primary" onclick="calcCompound()">Proyectar al Futuro</button>

                <div class="data-display" id="comp-res" style="display:none;">
                    <div class="data-row"><span>Tu dinero crecerá hasta:</span><span class="val-gold" id="res-comp-total">S/ 0</span></div>
                    <div style="height: 160px; margin-top: 15px;"><canvas id="chartCompound"></canvas></div>
                </div>
            </div>

            <!-- 4. CONVERSOR DIVISAS (NUEVO) -->
            <div class="glass-card">
                <div class="card-header">
                    <div class="icon-box"><i class="fas fa-exchange-alt"></i></div>
                    <h3>Tipo de Cambio & Devaluación</h3>
                </div>
                <p style="color: var(--text-muted); font-size: 0.85rem; margin-bottom: 20px;">Aprende por qué ahorrar en dólares puede proteger tu dinero si la moneda local pierde valor. (Ref: 1 USD = 3.75 PEN).</p>
                
                <div class="input-group">
                    <label>Monto en Soles (PEN):</label>
                    <div class="input-with-icon"><i class="fas fa-money-bill"></i><input type="number" id="fx-pen" value="100" oninput="calcFx()"></div>
                </div>
                <div class="data-display" style="margin-top:0;">
                    <div class="data-row" style="margin:0;"><span>Equivale en Dólares (USD):</span><span class="val-gold" id="fx-usd">$ 26.66</span></div>
                </div>
            </div>

        </div>
    </div>

    <!-- FOOTER -->
    <footer>
        <p><strong>Legacy Finance Academy</strong> • Proyecto para el concurso "Crea y Emprende" 3° Secundaria.</p>
        <p style="margin-top: 5px; opacity: 0.6;">Diseño Minimalista y Desarrollo potenciado por Inteligencia Artificial.</p>
    </footer>

    <!-- CHATBOT FLOTANTE -->
    <div class="fab-chat" onclick="toggleChat()"><i class="fas fa-comment-dollar"></i></div>
    <div class="chat-window" id="chatWin">
        <div class="chat-head">
            <div>
                <h3 style="font-size:1rem; color:var(--accent-gold);">Asesor Privado AI</h3>
                <p style="font-size:0.75rem; color:var(--text-muted);">En línea 🟢</p>
            </div>
            <i class="fas fa-times" style="cursor:pointer; color:white;" onclick="toggleChat()"></i>
        </div>
        <div class="chat-body" id="chatBody">
            <div class="bubble ai">¡Hola! Soy la IA de Legacy Finance. ¿Tienes dudas sobre la teoría que acabas de leer o cómo usar los simuladores?</div>
        </div>
        <div class="chat-foot">
            <input type="text" id="chatInp" placeholder="Escribe tu duda aquí..." onkeypress="if(event.key==='Enter') sendChat()">
            <button onclick="sendChat()"><i class="fas fa-paper-plane"></i></button>
        </div>
    </div>

    <script>
        // DATOS DE TEORÍA DINÁMICA POR PERFIL
        const profileData = {
            junior: {
                title: "Nivel Semilla: Domina tus Propinas 🌱",
                img: "https://images.unsplash.com/photo-1579621970563-ebec7560ff3e?auto=format&fit=crop&w=800&q=80",
                theory: [
                    { t: "1. ¿Qué es el dinero en realidad?", d: "El dinero no es magia que sale del cajero. Es una herramienta que ganamos como recompensa por aportar valor, trabajar o ayudar en casa. ¡Cuidarlo es tu primera misión!" },
                    { t: "2. La Magia del Chanchito (Ahorro)", d: "La regla de oro: Págate a ti mismo primero. Antes de comprar dulces, guarda siempre un 20% de lo que recibes. Ese dinero es intocable y te servirá para comprar lo que de verdad sueñas." },
                    { t: "3. El Truco de las 24 Horas", d: "¿Viste un juguete, ropa o un 'skin' en un juego y lo quieres YA? Espera 24 horas. Si al día siguiente ya no lo quieres tanto, ¡felicidades!, era un deseo impulsivo y acabas de salvar tu dinero." }
                ]
            },
            emprende: {
                title: "Nivel Brote: Finanzas para Negocios 🚀",
                img: "https://images.unsplash.com/photo-1454165804606-c3d57bc86b40?auto=format&fit=crop&w=800&q=80",
                theory: [
                    { t: "1. Costos vs Precio de Venta", d: "Si haces pulseras o postres para vender, primero suma cuánto gastas en materiales (Costo). Tu Precio de Venta debe ser mayor al costo para que exista ganancia real, de lo contrario, estás perdiendo plata." },
                    { t: "2. El Capital Sagrado", d: "El dinero que usas para comprar mercadería se llama 'Capital de Trabajo'. Nunca te gastes el capital en cosas personales, porque te quedarás sin fondos para volver a producir." },
                    { t: "3. Presupuesto del Emprendedor", d: "Aplica el 50/30/20 a las ganancias de tu negocio. Guarda un 20% siempre para 'reinvertir', es decir, comprar mejores herramientas o publicidad para crecer más rápido." }
                ]
            },
            inversion: {
                title: "Nivel Legado: Inversión Avanzada 💼",
                img: "https://images.unsplash.com/photo-1611974789855-9c2a0a7236a3?auto=format&fit=crop&w=800&q=80",
                theory: [
                    { t: "1. El Algoritmo del Interés Compuesto", d: "Albert Einstein la llamó la fuerza más poderosa del universo. Consiste en ganar intereses sobre tus intereses. Si no sacas tu dinero del banco y dejas que se acumule, crecerá como una bola de nieve imparable." },
                    { t: "2. Inflación: El Ladrón Invisible", d: "La inflación hace que las cosas cuesten más cada año. Si guardas S/ 100 debajo de tu colchón, en 5 años comprarás menos cosas con ese mismo billete. Por eso DEBES invertir, para ganarle a la inflación." },
                    { t: "3. Diversificación de Riesgo", d: "La regla de oro de los millonarios: 'No pongas todos los huevos en la misma canasta'. Reparte tu dinero en ahorros a plazo fijo, negocios y dólares para estar protegido si algo falla." }
                ]
            }
        };

        let chartB = null;
        let chartC = null;
        let currentProfile = 'junior';

        // FUNCIÓN PRINCIPAL PARA CAMBIAR TODO EL CONTENIDO
        function changeProfile(mode) {
            currentProfile = mode;
            
            // Actualizar botones visualmente
            document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
            event.currentTarget.classList.add('active');

            // 1. Cambiar Imagen y Título de la Teoría con efecto de opacidad
            const imgElement = document.getElementById('theory-img');
            imgElement.style.opacity = 0;
            setTimeout(() => {
                imgElement.src = profileData[mode].img;
                imgElement.style.opacity = 1;
            }, 300);
            
            document.getElementById('theory-title').innerText = profileData[mode].title;

            // 2. Generar las Tarjetas de Teoría dinámicamente
            const theoryContainer = document.getElementById('theory-cards-container');
            theoryContainer.innerHTML = "";
            profileData[mode].theory.forEach(item => {
                theoryContainer.innerHTML += `
                    <div class="theory-card">
                        <h3>${item.t}</h3>
                        <p>${item.d}</p>
                    </div>
                `;
            });
            
            // 3. Pequeño scroll automático a la sección de teoría para que el usuario empiece a leer
            document.getElementById('teoria').scrollIntoView({ behavior: 'smooth', block: 'start' });
        }

        // --- SIMULADORES JS --- //

        function calcBudget() {
            const inc = parseFloat(document.getElementById('budget-input').value) || 0;
            const n = inc * 0.5; const d = inc * 0.3; const a = inc * 0.2;
            
            document.getElementById('budget-res').style.display = 'block';
            document.getElementById('res-50').innerText = `S/ ${n.toFixed(2)}`;
            document.getElementById('res-30').innerText = `S/ ${d.toFixed(2)}`;
            document.getElementById('res-20').innerText = `S/ ${a.toFixed(2)}`;

            if(chartB) chartB.destroy();
            const ctx = document.getElementById('chartBudget').getContext('2d');
            Chart.defaults.color = '#9bb1a5';
            chartB = new Chart(ctx, {
                type: 'doughnut',
                data: {
                    labels: ['Necesidades', 'Deseos', 'Ahorro'],
                    datasets: [{ data: [n, d, a], backgroundColor: ['#1b4332', '#9bb1a5', '#D4AF37'], borderWidth: 0, hoverOffset: 4 }]
                },
                options: { responsive: true, maintainAspectRatio: false, cutout: '75%', plugins: { legend: { position: 'right' } } }
            });
        }

        function calcGoal() {
            const name = document.getElementById('goal-name').value || "Mi Meta";
            const cost = parseFloat(document.getElementById('goal-cost').value) || 0;
            const save = parseFloat(document.getElementById('goal-save').value) || 0;
            if(cost <= 0 || save <= 0) return alert("Ingresa valores válidos.");
            
            const months = Math.ceil(cost / save);
            document.getElementById('goal-res').style.display = 'block';
            document.getElementById('res-goal-title').innerText = `Meta: ${name}`;
            document.getElementById('res-goal-time').innerText = `${months} Meses`;
            
            // Lógica para llenar la barra asumiendo 1 mes de progreso inicial
            const bar = document.getElementById('res-goal-bar');
            bar.style.width = '0%';
            setTimeout(() => { 
                let progress = (1 / months) * 100;
                if(progress > 100) progress = 100;
                bar.style.width = `${progress}%`; 
            }, 200);
        }

        function calcCompound() {
            const p = parseFloat(document.getElementById('comp-principal').value) || 0;
            const r = (parseFloat(document.getElementById('comp-rate').value) || 0) / 100;
            const y = parseInt(document.getElementById('comp-years').value) || 1;

            let lbls = ['Hoy']; let dts = [p]; let bal = p;
            for(let i=1; i<=y; i++) { bal = bal * (1+r); lbls.push(`Año ${i}`); dts.push(bal.toFixed(2)); }

            document.getElementById('comp-res').style.display = 'block';
            document.getElementById('res-comp-total').innerText = `S/ ${bal.toFixed(2)}`;

            if(chartC) chartC.destroy();
            const ctx = document.getElementById('chartCompound').getContext('2d');
            chartC = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: lbls,
                    datasets: [{ label: 'Crecimiento de tu Capital', data: dts, borderColor: '#D4AF37', backgroundColor: 'rgba(212, 175, 55, 0.1)', fill: true, tension: 0.3, borderWidth: 3 }]
                },
                options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { display:false } }, scales: { x: { grid: { color: '#1a2a22' } }, y: { grid: { color: '#1a2a22' } } } }
            });
        }

        function calcFx() {
            const pen = parseFloat(document.getElementById('fx-pen').value) || 0;
            const rate = 3.75; 
            document.getElementById('fx-usd').innerText = `$ ${(pen/rate).toFixed(2)}`;
        }

        // --- CHATBOT JS --- //
        function toggleChat() {
            const win = document.getElementById('chatWin');
            win.style.display = win.style.display === 'flex' ? 'none' : 'flex';
        }

        function sendChat() {
            const inp = document.getElementById('chatInp');
            const txt = inp.value.trim();
            if(!txt) return;

            const box = document.getElementById('chatBody');
            box.innerHTML += `<div class="bubble user">${txt}</div>`;
            inp.value = "";
            box.scrollTop = box.scrollHeight;

            const loadId = "l-" + Date.now();
            box.innerHTML += `<div class="bubble ai" id="${loadId}">Analizando tu pregunta...</div>`;
            box.scrollTop = box.scrollHeight;

            // Respuesta local automática sin necesidad de API para no complicar el código
            setTimeout(() => {
                let r = "¡Excelente pregunta! En finanzas, lo importante es tener disciplina. Te recomiendo probar nuestra matriz 50/30/20 aquí abajo para ordenar tu dinero.";
                if(currentProfile === 'junior') r = "¡Oye crack! Recuerda el Truco de las 24 horas: si quieres comprar algo por impulso, espera a mañana para ver si aún lo quieres. ¡Salvarás mucha propina!";
                if(currentProfile === 'emprende') r = "En los negocios, separar el dinero de tu empresa de tu bolsillo personal es la regla de oro. Nunca te gastes el Capital de Trabajo.";
                
                document.getElementById(loadId).innerText = r;
                box.scrollTop = box.scrollHeight;
            }, 1000);
        }

        // INICIAR CON EL PERFIL JUNIOR (SEMILLA) CARGADO POR DEFECTO
        window.onload = () => {
            // Se simula un clic en el botón junior para cargar la teoría
            document.querySelector('.tab-btn.active').click();
            calcFx(); // Inicializa el conversor
        };
    </script>
</body>
</html>
