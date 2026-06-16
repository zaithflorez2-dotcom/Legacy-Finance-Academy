<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Legacy Finance Academy - Edición Maestra</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --bg-deep: #020604;
            --panel-glass: #09120e;
            --primary-emerald: #0f3621;
            --primary-light: #1b5335;
            --accent-gold: #d4af37;
            --accent-gold-glow: rgba(212, 175, 55, 0.15);
            --text-pure: #f4f7f5;
            --text-dim: #8fa598;
            --success-green: #4bb543;
        }
        
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Roboto, Helvetica, sans-serif; }
        body { background-color: var(--bg-deep); color: var(--text-pure); line-height: 1.6; -webkit-tap-highlight-color: transparent; }

        /* HERO HEADER */
        .hero-banner {
            background: linear-gradient(180deg, #07170e 0%, var(--bg-deep) 100%);
            padding: 50px 20px 40px 20px;
            text-align: center;
            border-bottom: 1px solid rgba(212, 175, 55, 0.15);
        }
        .hero-banner .badge-top { display: inline-block; padding: 4px 12px; background: rgba(212, 175, 55, 0.1); border: 1px solid var(--accent-gold); border-radius: 20px; color: var(--accent-gold); font-size: 0.75rem; font-weight: 700; text-transform: uppercase; margin-bottom: 15px; letter-spacing: 1px; }
        .hero-banner h1 { font-size: 2.1rem; font-weight: 900; letter-spacing: 0.5px; background: linear-gradient(135deg, #ffffff 30%, var(--accent-gold) 100%); -webkit-background-clip: text; -webkit-text-fill-color: transparent; margin-bottom: 8px; }
        .hero-banner p { color: var(--text-dim); font-size: 0.95rem; max-width: 550px; margin: auto; }

        /* NAV STICKY */
        .nav-wrapper { max-width: 850px; margin: -22px auto 25px auto; padding: 0 15px; position: sticky; top: 10px; z-index: 100; }
        .level-navbar { display: flex; gap: 8px; overflow-x: auto; padding: 6px; background: rgba(9, 18, 14, 0.95); border-radius: 14px; border: 1px solid rgba(31, 95, 62, 0.3); backdrop-filter: blur(12px); box-shadow: 0 8px 24px rgba(0,0,0,0.5); }
        .level-navbar::-webkit-scrollbar { display: none; }
        .nav-btn { flex: 1; min-width: 125px; background: transparent; border: none; padding: 12px 8px; color: var(--text-dim); font-weight: 700; cursor: pointer; border-radius: 10px; transition: all 0.3s ease; text-align: center; font-size: 0.8rem; display: flex; flex-direction: column; align-items: center; gap: 4px; }
        .nav-btn.active { background: linear-gradient(135deg, var(--primary-emerald) 0%, var(--primary-light) 100%); color: white; border: 1px solid var(--accent-gold); box-shadow: 0 4px 15px var(--accent-gold-glow); }

        /* LAYOUT PRINCIPAL */
        .main-layout { max-width: 850px; margin: auto; padding: 0 15px 50px 15px; display: flex; flex-direction: column; gap: 30px; }
        
        .content-card { background: var(--panel-glass); border-radius: 20px; padding: 25px; border: 1px solid #102117; box-shadow: 0 10px 30px rgba(0,0,0,0.3); }
        .section-title { font-size: 1.25rem; color: white; margin-bottom: 20px; display: flex; align-items: center; gap: 10px; font-weight: 700; }
        .section-title i { color: var(--accent-gold); }

        /* VITRINA DE TROFEOS */
        .shelf-container { display: flex; justify-content: space-around; background: #040906; padding: 18px 10px; border-radius: 14px; border: 1px solid #0a140f; }
        .shelf-item { text-align: center; opacity: 0.2; transition: all 0.6s ease; width: 30%; font-size: 0.75rem; color: var(--text-dim); }
        .shelf-item i { font-size: 2.2rem; display: block; margin-bottom: 6px; color: #4e5f54; }
        .shelf-item.unlocked { opacity: 1; color: white; transform: scale(1.03); }
        .shelf-item.unlocked i { color: var(--accent-gold); text-shadow: 0 0 15px var(--accent-gold-glow); }

        /* ILUSTRACIÓN VECTORIAL */
        .graphic-display { width: 100%; height: 130px; background: linear-gradient(135deg, #030705 0%, #0d2116 100%); border-radius: 14px; margin-bottom: 22px; display: flex; justify-content: center; align-items: center; border: 1px dashed #143321; }
        .graphic-display i { font-size: 3.5rem; color: var(--accent-gold); text-shadow: 0 0 25px rgba(212,175,55,0.4); }

        /* FRASES DESTACADAS */
        .quote-box { background: rgba(212, 175, 55, 0.05); border-left: 3px solid var(--accent-gold); padding: 15px; border-radius: 8px; margin-bottom: 20px; font-style: italic; color: #e1c775; font-size: 0.95rem; }
        .quote-author { display: block; text-align: right; font-size: 0.8rem; color: var(--text-dim); font-style: normal; margin-top: 5px; font-weight: bold; }

        /* FLASHCARDS TEORÍA */
        .theory-deck { display: flex; flex-direction: column; gap: 16px; }
        .theory-flashcard { background: #050a07; border: 1px solid #0f2115; padding: 20px; border-radius: 12px; transition: all 0.3s ease; }
        .theory-flashcard:hover { border-color: var(--primary-light); background: #07120c; }
        .theory-flashcard h3 { color: var(--accent-gold); font-size: 1.1rem; margin-bottom: 8px; display: flex; align-items: center; gap: 8px; }
        .theory-flashcard h3 span { font-size: 0.75rem; background: rgba(255,255,255,0.05); padding: 2px 8px; border-radius: 4px; color: var(--text-dim); border: 1px solid rgba(255,255,255,0.1); }
        .theory-flashcard p { color: var(--text-dim); font-size: 0.92rem; line-height: 1.6; }

        /* FORMULARIOS */
        .input-block { margin-bottom: 16px; }
        .input-block label { display: block; margin-bottom: 6px; font-size: 0.85rem; color: var(--text-dim); font-weight: 500; }
        input, select { width: 100%; background: #030604; border: 1px solid #12291a; padding: 13px 12px; color: white; border-radius: 10px; font-size: 0.95rem; transition: all 0.3s ease; }
        input:focus, select:focus { border-color: var(--accent-gold); outline: none; }
        
        /* BOTONES */
        .action-buttons { display: flex; flex-direction: column; gap: 10px; margin-top: 15px; }
        button.btn-main { width: 100%; background: linear-gradient(135deg, var(--primary-emerald) 0%, var(--primary-light) 100%); color: white; border: none; padding: 14px; border-radius: 10px; font-size: 0.95rem; font-weight: 700; cursor: pointer; transition: all 0.3s ease; display: flex; justify-content: center; align-items: center; gap: 8px; }
        button.btn-main:hover { transform: translateY(-1px); filter: brightness(1.1); }
        button.btn-accent-gold { background: linear-gradient(135deg, #bda031 0%, var(--accent-gold) 100%); color: #020604; }

        /* RESPUESTAS */
        .response-panel { background: #030604; border-left: 4px solid var(--accent-gold); padding: 18px; border-radius: 10px; margin-top: 18px; display: none; font-size: 0.92rem; }
        .response-panel ul { list-style: none; }
        .response-panel li { display: flex; justify-content: space-between; padding: 8px 0; border-bottom: 1px solid #0a140f; }
        .response-panel li:last-child { border: none; }

        /* TEST INTERFAZ */
        .option-item { background: #030604; padding: 14px; margin-bottom: 10px; border-radius: 10px; cursor: pointer; border: 1px solid #0f2115; font-size: 0.9rem; transition: all 0.2s ease; display: flex; align-items: center; gap: 10px; color: var(--text-dim); }
        .option-item:hover { border-color: var(--primary-light); background: #050a07; }
        .option-item.selected { background: #081a10; border-color: var(--accent-gold); font-weight: bold; color: white; }
        .badge-alert { text-align: center; margin-top: 15px; font-size: 0.95rem; font-weight: bold; padding: 14px; border-radius: 10px; display: none; }

        /* CHAT FLOJANTE */
        .chat-circle-trigger { position: fixed; bottom: 20px; right: 20px; background: linear-gradient(135deg, var(--primary-emerald) 0%, var(--primary-light) 100%); color: white; width: 58px; height: 58px; border-radius: 50%; display: flex; justify-content: center; align-items: center; font-size: 1.4rem; cursor: pointer; box-shadow: 0 4px 16px rgba(0,0,0,0.5); border: 1px solid var(--accent-gold); z-index: 999; }
        .chat-window { position: fixed; bottom: 90px; right: 20px; width: calc(100% - 40px); max-width: 360px; height: 400px; background: var(--panel-glass); border-radius: 16px; box-shadow: 0 10px 30px rgba(0,0,0,0.6); border: 1px solid #1f5f3e; display: none; flex-direction: column; overflow: hidden; z-index: 999; }
        .chat-title-bar { background: var(--primary-emerald); color: white; padding: 14px; font-weight: bold; display: flex; justify-content: space-between; align-items: center; font-size: 0.88rem; border-bottom: 1px solid var(--accent-gold); }
        .chat-body-stream { flex: 1; padding: 14px; overflow-y: auto; display: flex; flex-direction: column; gap: 10px; background: #040806; font-size: 0.88rem; }
        .chat-bubble { padding: 10px 14px; border-radius: 12px; max-width: 82%; }
        .chat-bubble.user { background: var(--primary-emerald); color: white; align-self: flex-end; border-bottom-right-radius: 1px; }
        .chat-bubble.ia { background: var(--panel-glass); color: var(--text-pure); align-self: flex-start; border-bottom-left-radius: 1px; border: 1px solid #102117; }
        .chat-input-row { display: flex; padding: 10px; background: var(--panel-glass); border-top: 1px solid #102117; }
        .chat-input-row input { flex: 1; margin-bottom: 0; padding: 11px; background: #030604; border-radius: 8px 0 0 8px; border: 1px solid #12291a; border-right: none; }
        .chat-input-row button { background: var(--primary-emerald); color: white; border: none; padding: 0 18px; border-radius: 0 8px 8px 0; font-weight: bold; cursor: pointer; border: 1px solid #12291a; border-left: none; }

        .footer-credits { text-align: center; padding: 35px 20px; font-size: 0.75rem; color: var(--text-dim); background: #010302; border-top: 1px solid #09120e; margin-top: 50px; }
    </style>
</head>
<body>

    <!-- HERO -->
    <div class="hero-banner">
        <span class="badge-top">PROTOTIPO FINTECH ESCOLAR OFICIAL</span>
        <h1>LEGACY FINANCE ACADEMY</h1>
        <p>Aprende la ciencia del dinero, domina tus presupuestos y construye tu propio legado económico paso a paso.</p>
    </div>

    <!-- NAVBAR NIVELES -->
    <div class="nav-wrapper">
        <div class="level-navbar">
            <button class="nav-btn active" id="nav-junior" onclick="switchLevel('junior')"><i class="fas fa-seedling"></i> Nivel Semilla</button>
            <button class="nav-btn" id="nav-emprende" onclick="switchLevel('emprende')"><i class="fas fa-store"></i> Emprendedor</button>
            <button class="nav-btn" id="nav-inversion" onclick="switchLevel('inversion')"><i class="fas fa-chart-line"></i> Inversionista</button>
        </div>
    </div>

    <!-- MAIN INTERFACE -->
    <div class="main-layout">
        
        <!-- BLOCK 1: CERTIFICADOS -->
        <div class="content-card">
            <div class="section-title"><i class="fas fa-trophy"></i> Reconocimiento Académico</div>
            <div class="shelf-container">
                <div class="shelf-item" id="badge-read"><i class="fas fa-book-reader"></i>Módulo Leído</div>
                <div class="shelf-item" id="badge-calc"><i class="fas fa-chart-pie"></i>Planificador</div>
                <div class="shelf-item" id="badge-test"><i class="fas fa-award"></i>Sello Dorado</div>
            </div>
        </div>

        <!-- BLOCK 2: MARCO TEÓRICO EN EXTENSIÓN -->
        <div class="content-card">
            <div class="graphic-display" id="vector-box"><i class="fas fa-piggy-bank"></i></div>
            
            <!-- Frase Dinámica -->
            <div class="quote-box" id="level-quote">
                "No me digas lo que valoras, muéstrame tu presupuesto y te diré lo que valoras."
                <span class="quote-author">— Joe Biden</span>
            </div>

            <div class="section-title"><i class="fas fa-university"></i> Academia Teórica Avanzada</div>
            <div class="theory-deck" id="theory-deck-content">
                <!-- Se llena con Javascript dependiente del nivel -->
            </div>
        </div>

        <div style="text-align: center; color: var(--accent-gold); font-weight: 700; font-size: 1.1rem; letter-spacing: 1px;">📊 SISTEMA DE HERRAMIENTAS Y SIMULADORES</div>

        <!-- SIMULADORES -->
        <div class="tools-grid" style="display: flex; flex-direction: column; gap: 25px;">
            
            <!-- PRESUPUESTO 50/30/20 -->
            <div class="content-card">
                <div class="section-title"><i class="fas fa-wallet"></i> Distribución Presupuestal Automatizada</div>
                <div class="input-block">
                    <label>Tus Ingresos Mensuales Proyectados (Soles S/):</label>
                    <input type="number" id="income-value" value="400" min="0">
                </div>
                <div class="action-buttons">
                    <button class="btn-main" onclick="runBudgetMatrix()">Ejecutar Algoritmo 50/30/20</button>
                    <button class="btn-main btn-accent-gold" onclick="triggerCoachAI()">Consultar Auditoría Coach IA</button>
                </div>
                <div class="response-panel" id="panel-budget-res"></div>
                <div class="response-panel" id="panel-coach-ai" style="border-left-color: var(--success-green); font-style: italic; color: #d8f3dc;"></div>
                <div style="margin-top: 15px;"><canvas id="chartDoughnutCanvas" style="max-height: 180px; display:none;"></canvas></div>
            </div>

            <!-- PLANIFICADOR DE METAS -->
            <div class="content-card">
                <div class="section-title"><i class="fas fa-bullseye"></i> Planificador Estratégico de Objetivos</div>
                <div class="input-block">
                    <label>¿Qué meta u objeto deseas adquirir? (Ej. Laptop, Bicicleta):</label>
                    <input type="text" id="goal-title" value="Bicicleta de Montaña">
                </div>
                <div class="input-block">
                    <label>Costo total del objetivo de inversión (Soles S/):</label>
                    <input type="number" id="goal-total-cost" value="800">
                </div>
                <div class="input-block">
                    <label>¿Cuánto dinero puedes ahorrar al mes exclusivamente para esto? (S/):</label>
                    <input type="number" id="goal-monthly-save" value="80">
                </div>
                <button class="btn-main" onclick="runGoalPlanner()">Proyectar Tiempo Solución</button>
                <div class="response-panel" id="panel-goal-res"></div>
            </div>

            <!-- SIMULADOR DE COBERTURA CAMBIARIA -->
            <div class="content-card">
                <div class="section-title"><i class="fas fa-exchange-alt"></i> Simulador Cambiario (PEN a USD)</div>
                <div class="input-block">
                    <label>Monto en Soles que deseas evaluar (S/):</label>
                    <input type="number" id="currency-pen" value="200">
                </div>
                <div class="input-block">
                    <label>Tipo de Cambio Actual del Mercado Peruano:</label>
                    <input type="number" id="currency-rate" value="3.76" step="0.01">
                </div>
                <button class="btn-main" onclick="runCurrencySimulator()">Simular Cambio Patrimonial</button>
                <div class="response-panel" id="panel-currency-res"></div>
            </div>

            <!-- CUESTIONARIO -->
            <div class="content-card">
                <div class="section-title"><i class="fas fa-graduation-cap"></i> Cuestionario de Certificación del Nivel</div>
                <div id="quiz-block-root"></div>
                <button class="btn-main" onclick="processQuizGrade()">Validar Evaluación Oficial</button>
                <div class="badge-alert" id="panel-quiz-alert"></div>
            </div>

        </div>

    </div>

    <!-- MENTOR FLOJANTE -->
    <div class="chat-circle-trigger" onclick="switchChatDisplay()">💬</div>
    <div class="chat-window" id="chatWindowBox">
        <div class="chat-title-bar">
            <span>🤖 Mentor Financiero Inteligente</span>
            <span style="cursor:pointer;" onclick="switchChatDisplay()">✖</span>
        </div>
        <div class="chat-body-stream" id="chatStreamArea">
            <div class="msg ia chat-bubble" id="chat-welcome">Terminal inicializada. Estoy listo para auditar tus ideas de presupuesto o estrategias comerciales. ¿En qué te ayudo hoy?</div>
        </div>
        <div class="chat-input-row">
            <input type="text" id="textChatInput" placeholder="Hazme una pregunta sobre finanzas..." onkeypress="if(event.key==='Enter') executeChatSpeech()">
            <button onclick="executeChatSpeech()">Enviar</button>
        </div>
    </div>

    <!-- FOOTER -->
    <div class="footer-credits">
        <strong>Legacy Finance Academy Pro • Arquitectura Web v4.0 Final Extendida</strong><br>
        Infraestructura Cloud de costo cero operando de manera eficiente en GitHub Pages.<br>
        Desarrollado para Promover la Inclusión Económica Escolar y el Éxito Comercial Emprendedor • 2026
    </div>

    <script>
        let currentActiveLevel = 'junior';
        let chartInstanceDoughnut = null;

        const databaseContent = {
            junior: {
                quote: '"No ahorres lo que queda después de gastar, gasta lo que queda después de ahorrar."',
                author: "Warren Buffett",
                icon: "fas fa-seedling",
                theoryCards: [
                    { h: "🌱 La Filosofía del Nivel Semilla", p: "Cada gran fortuna, empresa exitosa o meta cumplida nace exactamente de la misma manera: cuidando y dándole un propósito a las primeras monedas. El dinero no aparece por arte de magia; representa una porción de tiempo, valor e ingenio que entregamos a nuestra comunidad a través del trabajo o la ayuda." },
                    { h: "👑 La Regla de Oro del Chanchito de Oro", p: "El error financiero más común entre las personas es guardar el dinero que les sobra al final de la semana después de haber comprado dulces, antojos o juegos. Los verdaderos expertos aplican la regla inversa: 'Págate a ti mismo primero'. Apenas recibas una propina o un pago, congela de inmediato un porcentaje fijo (mínimo el 20%) en tu alcancía. Ese dinero está prohibido tocarse; es la base de tu futuro." },
                    { h: "🛑 El Peligro Oculto de los 'Gastos Hormiga'", p: "Se les llama gastos hormiga a esas pequeñas monedas que gastas a diario casi sin darte cuenta: un caramelo a la salida, un empaque decorativo, un refresco extra. Individualmente parecen insignificantes (un par de soles), pero si sumas ese gasto hormiga durante los 30 días del mes, descubrirás que se ha devorado el dinero con el que habías podido comprar el libro, la ropa o el accesorio tecnológico que tanto deseabas." },
                    { h: "🎯 El Filtro de Decisiones 'Anti-Antojos'", p: "Cuando sientas un deseo incontrolable por comprar un objeto variable o de moda en internet o en la tienda, aplícale el truco de las 24 horas. Regresa a tu casa, conversa, duerme bien y mantén la mente fría. Si al día siguiente sigues queriendo ese objeto con la misma urgencia, evalúa su compra. Te darás cuenta de que el 85% de las veces la emoción desaparece, ahorrándote mucho dinero." }
                ],
                quizQuestions: [
                    { q: "Si recibes una propina de S/ 40 por tus buenas notas, ¿cuál es la acción correcta según el Nivel Semilla?", o: ["Gastar todo el capital en antojos y dulces ese mismo fin de semana", "Separar inmediatamente S/ 8 para tu fondo de reserva inamovible antes de planear otros consumos", "Prestarle el dinero a un compañero sin registrarlo en tu cuaderno de control"], a: 1 }
                ]
            },
            emprende: {
                quote: '"El precio es lo que pagas. El valor es lo que recibes."',
                author: "Warren Buffett",
                icon: "fas fa-store",
                theoryCards: [
                    { h: "📊 La Estructura de los Costos Reales", p: "Vender un producto en el colegio a S/ 5 habiéndolo adquirido a S/ 3 en el mercado mayorista no significa que estés ganando S/ 2 netos. Para conocer tu verdadera rentabilidad, debes calcular los costos invisibles: el dinero de los pasajes que usaste para ir a comprarlo, las bolsas plásticas de empaque, las servilletas y el tiempo invertido en venderlo. Si no mides tus costos reales unitarios, estás subsidiando pérdidas sin saberlo." },
                    { h: "🛡️ El Capital de Trabajo es Intocable", p: "El capital de trabajo es la cantidad total de dinero que requiere tu negocio para comprar su mercadería o insumos iniciales antes de abrir las puertas. Este fondo es sagrado y corporativo. Si utilizas las monedas del capital de trabajo para comprarte un antojo personal o un almuerzo, el negocio se quedará sin dinero para reponer stock al día siguiente, provocando una quiebra técnica inmediata." },
                    { h: "📈 El Punto de Equilibrio Operativo", p: "Consiste en el cálculo matemático exacto que te dice cuántas unidades de tu producto necesitas vender como mínimo para recuperar la inversión total sin ganar ni perder un solo sol. Toda unidad que logres comercializar por encima de ese número crítico representa ganancia líquida pura para tu caja neta." }
                ],
                quizQuestions: [
                    { q: "Si para armar tu negocio de bocaditos escolares gastas S/ 50 en insumos y vendes todo a S/ 90, ¿qué representan los S/ 50 originales?", o: ["La utilidad neta lograda", "El capital de trabajo necesario para la recompra de mercadería", "Un gasto hormiga perdido"], a: 1 }
                ]
            },
            inversion: {
                quote: '"La riqueza no consiste en tener grandes posesiones, sino en tener pocas necesidades."',
                author: "Epicteto",
                icon: "fas fa-chart-line",
                theoryCards: [
                    { h: "📈 El Algoritmo Exponencial del Interés Compuesto", p: "Consiste en la capitalización cíclica de las ganancias. Al dejar tus fondos guardados en un vehículo de inversión, el interés que ganas no se gasta, sino que se fusiona automáticamente con tu capital original. Al siguiente ciclo, ganarás nuevos intereses sobre los intereses acumulados anteriores, creando un efecto de bola de nieve exponencial a lo largo de los años." },
                    { h: "🏦 Filtro de Crecimiento Seguro: La Tasa TREA", p: "Los bancos comerciales grandes suelen invertir mucho dinero en publicidad masiva, pero pagan tasas muy bajas. Los inversores inteligentes comparan siempre la TREA (Tasa de Rendimiento Efectiva Anual) de las Cajas Municipales o Rurales supervisadas por la SBS, las cuales suelen pagar hasta el triple por tus ahorros inmovilizados a plazo fijo." },
                    { h: "🛡️ Mitigación del Riesgo Mediante Diversificación", p: "La regla fundamental del inversionista es: 'No pongas todos tus huevos en la misma canasta'. Distribuir tu capital acumulado en diferentes herramientas económicas o negocios complementarios absorbe el impacto negativo en caso de que un sector sufra volatilidad." }
                ],
                quizQuestions: [
                    { q: "¿Qué métrica financiera determina la cantidad exacta de dinero neto que ganarás al dejar un fondo a plazo fijo?", o: ["La TCEA que aplican las tarjetas para compras a crédito", "La TREA que pagan las entidades financieras supervisadas", "La tasa de devaluación del tipo de cambio diario"], a: 1 }
                ]
            }
        };

        function switchLevel(levelKey) {
            currentActiveLevel = levelKey;
            document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
            document.getElementById(`nav-${levelKey}`).classList.add('active');
            
            // Cambiar Frase Dinámica
            document.getElementById('level-quote').innerHTML = `
                "${databaseContent[levelKey].quote}"
                <span class="quote-author">— ${databaseContent[levelKey].author}</span>
            `;

            // Cambiar Ilustración Vectorial
            document.getElementById('vector-box').innerHTML = `<i class="${databaseContent[levelKey].icon}"></i>`;

            // Cargar Tarjetas Teóricas Ampliadas
            const deck = document.getElementById('theory-deck-content');
            deck.innerHTML = "";
            databaseContent[levelKey].theoryCards.forEach((card, idx) => {
                deck.innerHTML += `
                    <div class="theory-flashcard" onclick="unlockReadingBadge()">
                        <h3><span>Lección ${idx+1}</span> ${card.h}</h3>
                        <p>${card.p}</p>
                    </div>`;
            });

            // Cargar Preguntas del Cuestionario
            const quizRoot = document.getElementById('quiz-block-root');
            quizRoot.innerHTML = "";
            databaseContent[levelKey].quizQuestions.forEach((item, qIdx) => {
                let optionsData = "";
                item.o.forEach((opt, oIdx) => {
                    optionsData += `<div class="option-item" data-q="${qIdx}" data-o="${oIdx}" onclick="captureOptionSelect(this)"><i class="far fa-circle"></i> ${opt}</div>`;
                });
                quizRoot.innerHTML += `<div><p style="font-weight:600; margin-bottom:12px; color:white; font-size:0.95rem;">${item.q}</p>${optionsData}</div>`;
            });

            // Resetear vistas
            document.getElementById('panel-budget-res').style.display = 'none';
            document.getElementById('panel-coach-ai').style.display = 'none';
            document.getElementById('panel-goal-res').style.display = 'none';
            document.getElementById('panel-currency-res').style.display = 'none';
            document.getElementById('panel-quiz-alert').style.display = 'none';
            if(chartInstanceDoughnut) document.getElementById('chartDoughnutCanvas').style.display = 'none';

            // Mensajes de bienvenida dinámicos del Mentor
            let chatText = "Terminal activa. ¿Qué variables de capital analizamos hoy?";
            if(levelKey === 'junior') chatText = "¡Hola crack! Soy tu mentor del Nivel Semilla. Estoy listo para enseñarte a liquidar los gastos hormiga y multiplicar el tamaño de tu alcancía.";
            if(levelKey === 'emprende') chatText = "Saludos socio. Vamos a auditar minuciosamente la estructura de costos de tu emprendimiento para blindar tu flujo de caja.";
            document.getElementById('chat-welcome').innerText = chatText;
        }

        function unlockReadingBadge() {
            document.getElementById('badge-read').classList.add('unlocked');
        }

        function captureOptionSelect(targetElement) {
            const rowOptions = targetElement.parentElement.querySelectorAll('.option-item');
            rowOptions.forEach(opt => {
                opt.classList.remove('selected');
                opt.querySelector('i').className = "far fa-circle";
            });
            targetElement.classList.add('selected');
            targetElement.querySelector('i').className = "fas fa-check-circle";
            targetElement.parentElement.setAttribute('data-user-selection', targetElement.getAttribute('data-o'));
        }

        function processQuizGrade() {
            const items = document.getElementById('quiz-block-root').children;
            let finalScore = 0;
            let maxItems = databaseContent[currentActiveLevel].quizQuestions.length;

            for(let i=0; i<maxItems; i++) {
                const block = items[i];
                const selected = block.getAttribute('data-user-selection');
                if(selected == databaseContent[currentActiveLevel].quizQuestions[i].a) finalScore++;
            }

            const alertBox = document.getElementById('panel-quiz-alert');
            alertBox.style.display = 'block';

            if(finalScore === maxItems) {
                alertBox.innerHTML = "<i class='fas fa-check-circle'></i> ¡EXAMEN PERFECTO! Desbloqueas el Sello de Oro de la academia.";
                alertBox.style.background = "#0c2417";
                alertBox.style.color = "#52b788";
                document.getElementById('badge-test').classList.add('unlocked');
            } else {
                alertBox.innerHTML = "<i class='fas fa-times-circle'></i> Calificación insuficiente. Repasa las lecciones de arriba e inténtalo de nuevo.";
                alertBox.style.background = "#2b0d0d";
                alertBox.style.color = "#e63946";
            }
        }

        function runBudgetMatrix() {
            const income = parseFloat(document.getElementById('income-value').value) || 0;
            if(income <= 0) return alert("Ingresa un monto de dinero válido.");

            const opNec = income * 0.50;
            const opDes = income * 0.30;
            const opAho = income * 0.20;

            const panel = document.getElementById('panel-budget-res');
            panel.style.display = 'block';
            panel.innerHTML = `
                <p style="font-weight:700; color:var(--accent-gold); margin-bottom:8px;"><i class="fas fa-chart-pie"></i> Distribución Presupuestal Ejecutada:</p>
                <ul>
                    <li><span>🛠️ Necesidades y Operaciones (50%):</span> <strong>S/ ${opNec.toFixed(2)}</strong></li>
                    <li><span>🍿 DeseosVariables / Ocio (30%):</span> <strong>S/ ${opDes.toFixed(2)}</strong></li>
                    <li><span>🐷 Ahorro Patrimonial Seguro (20%):</span> <strong style="color:var(--success-green)">S/ ${opAho.toFixed(2)}</strong></li>
                </ul>
            `;

            document.getElementById('badge-calc').classList.add('unlocked');

            // Renderizar Gráfico
            document.getElementById('chartDoughnutCanvas').style.display = 'block';
            if(chartInstanceDoughnut) chartInstanceDoughnut.destroy();

            const ctx = document.getElementById('chartDoughnutCanvas').getContext('2d');
            chartInstanceDoughnut = new Chart(ctx, {
                type: 'doughnut',
                data: {
                    labels: ['Necesidades (50%)', 'Deseos (30%)', 'Ahorro (20%)'],
                    datasets: [{
                        data: [opNec, opDes, opAho],
                        backgroundColor: ['#0f3621', '#d4af37', '#1b5335'],
                        borderColor: '#09120e'
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { labels: { color: '#f4f7f5', font: { weight: 'bold' } } } }
                }
            });
        }

        function runGoalPlanner() {
            const name = document.getElementById('goal-title').value;
            const cost = parseFloat(document.getElementById('goal-total-cost').value) || 0;
            const monthly = parseFloat(document.getElementById('goal-monthly-save').value) || 0;

            if(cost <= 0 || monthly <= 0) return alert("Ingresa montos superiores a cero.");

            const totalMonths = Math.ceil(cost / monthly);
            const panel = document.getElementById('panel-goal-res');
            panel.style.display = 'block';
            panel.innerHTML = `<i class="fas fa-flag-checkered" style="color:var(--accent-gold)"></i> Proyección: Financiar tu meta de mediano plazo (<em>${name}</em>) demandará un periodo de <strong>${totalMonths} meses</strong> de disciplina contable ininterrumpida.`;
        }

        function runCurrencySimulator() {
            const penAmount = parseFloat(document.getElementById('currency-pen').value) || 0;
            const exchangeRate = parseFloat(document.getElementById('currency-rate').value) || 0;

            if(penAmount <= 0 || exchangeRate <= 0) return alert("Completa los valores monetarios.");

            const usdResult = penAmount / exchangeRate;
            const panel = document.getElementById('panel-currency-res');
            panel.style.display = 'block';
            panel.innerHTML = `<i class="fas fa-shield-alt" style="color:var(--success-green)"></i> Tus <strong>S/ ${penAmount.toFixed(2)} Soles</strong> representan un valor refugio de <strong>$ ${usdResult.toFixed(2)} Dólares Americanos</strong> a un tipo de cambio de S/ ${exchangeRate.toFixed(2)}.`;
        }

        function triggerCoachAI() {
            const income = parseFloat(document.getElementById('income-value').value) || 0;
            if(income <= 0) return alert("Calcula una matriz matemática primero.");

            runBudgetMatrix();
            const aho = income * 0.20;
            const des = income * 0.30;
            const coachPanel = document.getElementById('panel-coach-ai');
            coachPanel.style.display = 'block';
            coachPanel.innerHTML = "<i class='fas fa-spinner fa-spin'></i> Ejecutando vectores predictivos corporativos...";

            setTimeout(() => {
                let reportText = "";
                if(currentActiveLevel === 'junior') {
                    reportText = `Auditoría del Coach Semilla: Tus S/ ${aho.toFixed(2)} mensuales de ahorro deben blindarse contra los gastos hormiga. Te sugiero usar el 'Filtro anti-antojos' en el recreo escolar. Evita pulverizar tus S/ ${des.toFixed(2)} de deseos variables de manera descontrolada.`;
                } else if(currentActiveLevel === 'emprende') {
                    reportText = `Estrategia de Negocios EPT: Operar con S/ ${income} exige proteger tu capital de trabajo. No combines las ganancias con tus gastos del día. Te recomiendo derivar un 10% del fondo de deseos directo a inventario al por mayor para optimizar tus márgenes netos.`;
                } else {
                    reportText = `Análisis Financiero de Portafolio: Registrar S/ ${aho.toFixed(2)} constantes te permite aprovechar el interés compuesto. En lugar de dejarlo inactivo, busca las tasas TREA que pagan las Cajas Municipales de la región sur supervisadas por la SBS.`;
                }
                coachPanel.innerHTML = `<strong>🤖 Dictamen de Auditoría IA:</strong><br>${reportText}`;
            }, 700);
        }

        function switchChatDisplay() {
            const chat = document.getElementById('chatWindowBox');
            chat.style.display = chat.style.display === 'flex' ? 'none' : 'flex';
        }

        function executeChatSpeech() {
            const input = document.getElementById('textChatInput');
            const userText = input.value.trim();
            if(!userText) return;

            const chatArea = document.getElementById('chatStreamArea');
            chatArea.innerHTML += `<div class="msg user chat-bubble">${userText}</div>`;
            input.value = "";
            chatArea.scrollTop = chatArea.scrollHeight;

            const uid = "ai-" + Date.now();
            chatArea.innerHTML += `<div class="msg ia chat-bubble" id="${uid}">Evaluando consulta contable...</div>`;
            chatArea.scrollTop = chatArea.scrollHeight;

            setTimeout(() => {
                let aiReply = "Es un excelente planteamiento analítico. Recuerda siempre mantener bajo control los costos fijos y proteger tu capital de trabajo para asegurar el flujo de caja.";
                if(currentActiveLevel === 'junior') aiReply = "¡Qué gran duda! Recuerda aplicar la regla del Chanchito de Oro: guarda hoy una porción fija de dinero antes de gastar. ¡Los gastos hormiga son el enemigo silencioso de tus metas!";
                document.getElementById(uid).innerText = aiReply;
                chatArea.scrollTop = chatArea.scrollHeight;
            }, 800);
        }

        // Carga Inicial del Sistema
        switchLevel('junior');
    </script>
</body>
</html><!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Legacy Finance Academy - Edición Maestra</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --bg-deep: #020604;
            --panel-glass: #09120e;
            --primary-emerald: #0f3621;
            --primary-light: #1b5335;
            --accent-gold: #d4af37;
            --accent-gold-glow: rgba(212, 175, 55, 0.15);
            --text-pure: #f4f7f5;
            --text-dim: #8fa598;
            --success-green: #4bb543;
        }
        
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Roboto, Helvetica, sans-serif; }
        body { background-color: var(--bg-deep); color: var(--text-pure); line-height: 1.6; -webkit-tap-highlight-color: transparent; }

        /* HERO HEADER */
        .hero-banner {
            background: linear-gradient(180deg, #07170e 0%, var(--bg-deep) 100%);
            padding: 50px 20px 40px 20px;
            text-align: center;
            border-bottom: 1px solid rgba(212, 175, 55, 0.15);
        }
        .hero-banner .badge-top { display: inline-block; padding: 4px 12px; background: rgba(212, 175, 55, 0.1); border: 1px solid var(--accent-gold); border-radius: 20px; color: var(--accent-gold); font-size: 0.75rem; font-weight: 700; text-transform: uppercase; margin-bottom: 15px; letter-spacing: 1px; }
        .hero-banner h1 { font-size: 2.1rem; font-weight: 900; letter-spacing: 0.5px; background: linear-gradient(135deg, #ffffff 30%, var(--accent-gold) 100%); -webkit-background-clip: text; -webkit-text-fill-color: transparent; margin-bottom: 8px; }
        .hero-banner p { color: var(--text-dim); font-size: 0.95rem; max-width: 550px; margin: auto; }

        /* NAV STICKY */
        .nav-wrapper { max-width: 850px; margin: -22px auto 25px auto; padding: 0 15px; position: sticky; top: 10px; z-index: 100; }
        .level-navbar { display: flex; gap: 8px; overflow-x: auto; padding: 6px; background: rgba(9, 18, 14, 0.95); border-radius: 14px; border: 1px solid rgba(31, 95, 62, 0.3); backdrop-filter: blur(12px); box-shadow: 0 8px 24px rgba(0,0,0,0.5); }
        .level-navbar::-webkit-scrollbar { display: none; }
        .nav-btn { flex: 1; min-width: 125px; background: transparent; border: none; padding: 12px 8px; color: var(--text-dim); font-weight: 700; cursor: pointer; border-radius: 10px; transition: all 0.3s ease; text-align: center; font-size: 0.8rem; display: flex; flex-direction: column; align-items: center; gap: 4px; }
        .nav-btn.active { background: linear-gradient(135deg, var(--primary-emerald) 0%, var(--primary-light) 100%); color: white; border: 1px solid var(--accent-gold); box-shadow: 0 4px 15px var(--accent-gold-glow); }

        /* LAYOUT PRINCIPAL */
        .main-layout { max-width: 850px; margin: auto; padding: 0 15px 50px 15px; display: flex; flex-direction: column; gap: 30px; }
        
        .content-card { background: var(--panel-glass); border-radius: 20px; padding: 25px; border: 1px solid #102117; box-shadow: 0 10px 30px rgba(0,0,0,0.3); }
        .section-title { font-size: 1.25rem; color: white; margin-bottom: 20px; display: flex; align-items: center; gap: 10px; font-weight: 700; }
        .section-title i { color: var(--accent-gold); }

        /* VITRINA DE TROFEOS */
        .shelf-container { display: flex; justify-content: space-around; background: #040906; padding: 18px 10px; border-radius: 14px; border: 1px solid #0a140f; }
        .shelf-item { text-align: center; opacity: 0.2; transition: all 0.6s ease; width: 30%; font-size: 0.75rem; color: var(--text-dim); }
        .shelf-item i { font-size: 2.2rem; display: block; margin-bottom: 6px; color: #4e5f54; }
        .shelf-item.unlocked { opacity: 1; color: white; transform: scale(1.03); }
        .shelf-item.unlocked i { color: var(--accent-gold); text-shadow: 0 0 15px var(--accent-gold-glow); }

        /* ILUSTRACIÓN VECTORIAL */
        .graphic-display { width: 100%; height: 130px; background: linear-gradient(135deg, #030705 0%, #0d2116 100%); border-radius: 14px; margin-bottom: 22px; display: flex; justify-content: center; align-items: center; border: 1px dashed #143321; }
        .graphic-display i { font-size: 3.5rem; color: var(--accent-gold); text-shadow: 0 0 25px rgba(212,175,55,0.4); }

        /* FRASES DESTACADAS */
        .quote-box { background: rgba(212, 175, 55, 0.05); border-left: 3px solid var(--accent-gold); padding: 15px; border-radius: 8px; margin-bottom: 20px; font-style: italic; color: #e1c775; font-size: 0.95rem; }
        .quote-author { display: block; text-align: right; font-size: 0.8rem; color: var(--text-dim); font-style: normal; margin-top: 5px; font-weight: bold; }

        /* FLASHCARDS TEORÍA */
        .theory-deck { display: flex; flex-direction: column; gap: 16px; }
        .theory-flashcard { background: #050a07; border: 1px solid #0f2115; padding: 20px; border-radius: 12px; transition: all 0.3s ease; }
        .theory-flashcard:hover { border-color: var(--primary-light); background: #07120c; }
        .theory-flashcard h3 { color: var(--accent-gold); font-size: 1.1rem; margin-bottom: 8px; display: flex; align-items: center; gap: 8px; }
        .theory-flashcard h3 span { font-size: 0.75rem; background: rgba(255,255,255,0.05); padding: 2px 8px; border-radius: 4px; color: var(--text-dim); border: 1px solid rgba(255,255,255,0.1); }
        .theory-flashcard p { color: var(--text-dim); font-size: 0.92rem; line-height: 1.6; }

        /* FORMULARIOS */
        .input-block { margin-bottom: 16px; }
        .input-block label { display: block; margin-bottom: 6px; font-size: 0.85rem; color: var(--text-dim); font-weight: 500; }
        input, select { width: 100%; background: #030604; border: 1px solid #12291a; padding: 13px 12px; color: white; border-radius: 10px; font-size: 0.95rem; transition: all 0.3s ease; }
        input:focus, select:focus { border-color: var(--accent-gold); outline: none; }
        
        /* BOTONES */
        .action-buttons { display: flex; flex-direction: column; gap: 10px; margin-top: 15px; }
        button.btn-main { width: 100%; background: linear-gradient(135deg, var(--primary-emerald) 0%, var(--primary-light) 100%); color: white; border: none; padding: 14px; border-radius: 10px; font-size: 0.95rem; font-weight: 700; cursor: pointer; transition: all 0.3s ease; display: flex; justify-content: center; align-items: center; gap: 8px; }
        button.btn-main:hover { transform: translateY(-1px); filter: brightness(1.1); }
        button.btn-accent-gold { background: linear-gradient(135deg, #bda031 0%, var(--accent-gold) 100%); color: #020604; }

        /* RESPUESTAS */
        .response-panel { background: #030604; border-left: 4px solid var(--accent-gold); padding: 18px; border-radius: 10px; margin-top: 18px; display: none; font-size: 0.92rem; }
        .response-panel ul { list-style: none; }
        .response-panel li { display: flex; justify-content: space-between; padding: 8px 0; border-bottom: 1px solid #0a140f; }
        .response-panel li:last-child { border: none; }

        /* TEST INTERFAZ */
        .option-item { background: #030604; padding: 14px; margin-bottom: 10px; border-radius: 10px; cursor: pointer; border: 1px solid #0f2115; font-size: 0.9rem; transition: all 0.2s ease; display: flex; align-items: center; gap: 10px; color: var(--text-dim); }
        .option-item:hover { border-color: var(--primary-light); background: #050a07; }
        .option-item.selected { background: #081a10; border-color: var(--accent-gold); font-weight: bold; color: white; }
        .badge-alert { text-align: center; margin-top: 15px; font-size: 0.95rem; font-weight: bold; padding: 14px; border-radius: 10px; display: none; }

        /* CHAT FLOJANTE */
        .chat-circle-trigger { position: fixed; bottom: 20px; right: 20px; background: linear-gradient(135deg, var(--primary-emerald) 0%, var(--primary-light) 100%); color: white; width: 58px; height: 58px; border-radius: 50%; display: flex; justify-content: center; align-items: center; font-size: 1.4rem; cursor: pointer; box-shadow: 0 4px 16px rgba(0,0,0,0.5); border: 1px solid var(--accent-gold); z-index: 999; }
        .chat-window { position: fixed; bottom: 90px; right: 20px; width: calc(100% - 40px); max-width: 360px; height: 400px; background: var(--panel-glass); border-radius: 16px; box-shadow: 0 10px 30px rgba(0,0,0,0.6); border: 1px solid #1f5f3e; display: none; flex-direction: column; overflow: hidden; z-index: 999; }
        .chat-title-bar { background: var(--primary-emerald); color: white; padding: 14px; font-weight: bold; display: flex; justify-content: space-between; align-items: center; font-size: 0.88rem; border-bottom: 1px solid var(--accent-gold); }
        .chat-body-stream { flex: 1; padding: 14px; overflow-y: auto; display: flex; flex-direction: column; gap: 10px; background: #040806; font-size: 0.88rem; }
        .chat-bubble { padding: 10px 14px; border-radius: 12px; max-width: 82%; }
        .chat-bubble.user { background: var(--primary-emerald); color: white; align-self: flex-end; border-bottom-right-radius: 1px; }
        .chat-bubble.ia { background: var(--panel-glass); color: var(--text-pure); align-self: flex-start; border-bottom-left-radius: 1px; border: 1px solid #102117; }
        .chat-input-row { display: flex; padding: 10px; background: var(--panel-glass); border-top: 1px solid #102117; }
        .chat-input-row input { flex: 1; margin-bottom: 0; padding: 11px; background: #030604; border-radius: 8px 0 0 8px; border: 1px solid #12291a; border-right: none; }
        .chat-input-row button { background: var(--primary-emerald); color: white; border: none; padding: 0 18px; border-radius: 0 8px 8px 0; font-weight: bold; cursor: pointer; border: 1px solid #12291a; border-left: none; }

        .footer-credits { text-align: center; padding: 35px 20px; font-size: 0.75rem; color: var(--text-dim); background: #010302; border-top: 1px solid #09120e; margin-top: 50px; }
    </style>
</head>
<body>

    <!-- HERO -->
    <div class="hero-banner">
        <span class="badge-top">PROTOTIPO FINTECH ESCOLAR OFICIAL</span>
        <h1>LEGACY FINANCE ACADEMY</h1>
        <p>Aprende la ciencia del dinero, domina tus presupuestos y construye tu propio legado económico paso a paso.</p>
    </div>

    <!-- NAVBAR NIVELES -->
    <div class="nav-wrapper">
        <div class="level-navbar">
            <button class="nav-btn active" id="nav-junior" onclick="switchLevel('junior')"><i class="fas fa-seedling"></i> Nivel Semilla</button>
            <button class="nav-btn" id="nav-emprende" onclick="switchLevel('emprende')"><i class="fas fa-store"></i> Emprendedor</button>
            <button class="nav-btn" id="nav-inversion" onclick="switchLevel('inversion')"><i class="fas fa-chart-line"></i> Inversionista</button>
        </div>
    </div>

    <!-- MAIN INTERFACE -->
    <div class="main-layout">
        
        <!-- BLOCK 1: CERTIFICADOS -->
        <div class="content-card">
            <div class="section-title"><i class="fas fa-trophy"></i> Reconocimiento Académico</div>
            <div class="shelf-container">
                <div class="shelf-item" id="badge-read"><i class="fas fa-book-reader"></i>Módulo Leído</div>
                <div class="shelf-item" id="badge-calc"><i class="fas fa-chart-pie"></i>Planificador</div>
                <div class="shelf-item" id="badge-test"><i class="fas fa-award"></i>Sello Dorado</div>
            </div>
        </div>

        <!-- BLOCK 2: MARCO TEÓRICO EN EXTENSIÓN -->
        <div class="content-card">
            <div class="graphic-display" id="vector-box"><i class="fas fa-piggy-bank"></i></div>
            
            <!-- Frase Dinámica -->
            <div class="quote-box" id="level-quote">
                "No me digas lo que valoras, muéstrame tu presupuesto y te diré lo que valoras."
                <span class="quote-author">— Joe Biden</span>
            </div>

            <div class="section-title"><i class="fas fa-university"></i> Academia Teórica Avanzada</div>
            <div class="theory-deck" id="theory-deck-content">
                <!-- Se llena con Javascript dependiente del nivel -->
            </div>
        </div>

        <div style="text-align: center; color: var(--accent-gold); font-weight: 700; font-size: 1.1rem; letter-spacing: 1px;">📊 SISTEMA DE HERRAMIENTAS Y SIMULADORES</div>

        <!-- SIMULADORES -->
        <div class="tools-grid" style="display: flex; flex-direction: column; gap: 25px;">
            
            <!-- PRESUPUESTO 50/30/20 -->
            <div class="content-card">
                <div class="section-title"><i class="fas fa-wallet"></i> Distribución Presupuestal Automatizada</div>
                <div class="input-block">
                    <label>Tus Ingresos Mensuales Proyectados (Soles S/):</label>
                    <input type="number" id="income-value" value="400" min="0">
                </div>
                <div class="action-buttons">
                    <button class="btn-main" onclick="runBudgetMatrix()">Ejecutar Algoritmo 50/30/20</button>
                    <button class="btn-main btn-accent-gold" onclick="triggerCoachAI()">Consultar Auditoría Coach IA</button>
                </div>
                <div class="response-panel" id="panel-budget-res"></div>
                <div class="response-panel" id="panel-coach-ai" style="border-left-color: var(--success-green); font-style: italic; color: #d8f3dc;"></div>
                <div style="margin-top: 15px;"><canvas id="chartDoughnutCanvas" style="max-height: 180px; display:none;"></canvas></div>
            </div>

            <!-- PLANIFICADOR DE METAS -->
            <div class="content-card">
                <div class="section-title"><i class="fas fa-bullseye"></i> Planificador Estratégico de Objetivos</div>
                <div class="input-block">
                    <label>¿Qué meta u objeto deseas adquirir? (Ej. Laptop, Bicicleta):</label>
                    <input type="text" id="goal-title" value="Bicicleta de Montaña">
                </div>
                <div class="input-block">
                    <label>Costo total del objetivo de inversión (Soles S/):</label>
                    <input type="number" id="goal-total-cost" value="800">
                </div>
                <div class="input-block">
                    <label>¿Cuánto dinero puedes ahorrar al mes exclusivamente para esto? (S/):</label>
                    <input type="number" id="goal-monthly-save" value="80">
                </div>
                <button class="btn-main" onclick="runGoalPlanner()">Proyectar Tiempo Solución</button>
                <div class="response-panel" id="panel-goal-res"></div>
            </div>

            <!-- SIMULADOR DE COBERTURA CAMBIARIA -->
            <div class="content-card">
                <div class="section-title"><i class="fas fa-exchange-alt"></i> Simulador Cambiario (PEN a USD)</div>
                <div class="input-block">
                    <label>Monto en Soles que deseas evaluar (S/):</label>
                    <input type="number" id="currency-pen" value="200">
                </div>
                <div class="input-block">
                    <label>Tipo de Cambio Actual del Mercado Peruano:</label>
                    <input type="number" id="currency-rate" value="3.76" step="0.01">
                </div>
                <button class="btn-main" onclick="runCurrencySimulator()">Simular Cambio Patrimonial</button>
                <div class="response-panel" id="panel-currency-res"></div>
            </div>

            <!-- CUESTIONARIO -->
            <div class="content-card">
                <div class="section-title"><i class="fas fa-graduation-cap"></i> Cuestionario de Certificación del Nivel</div>
                <div id="quiz-block-root"></div>
                <button class="btn-main" onclick="processQuizGrade()">Validar Evaluación Oficial</button>
                <div class="badge-alert" id="panel-quiz-alert"></div>
            </div>

        </div>

    </div>

    <!-- MENTOR FLOJANTE -->
    <div class="chat-circle-trigger" onclick="switchChatDisplay()">💬</div>
    <div class="chat-window" id="chatWindowBox">
        <div class="chat-title-bar">
            <span>🤖 Mentor Financiero Inteligente</span>
            <span style="cursor:pointer;" onclick="switchChatDisplay()">✖</span>
        </div>
        <div class="chat-body-stream" id="chatStreamArea">
            <div class="msg ia chat-bubble" id="chat-welcome">Terminal inicializada. Estoy listo para auditar tus ideas de presupuesto o estrategias comerciales. ¿En qué te ayudo hoy?</div>
        </div>
        <div class="chat-input-row">
            <input type="text" id="textChatInput" placeholder="Hazme una pregunta sobre finanzas..." onkeypress="if(event.key==='Enter') executeChatSpeech()">
            <button onclick="executeChatSpeech()">Enviar</button>
        </div>
    </div>

    <!-- FOOTER -->
    <div class="footer-credits">
        <strong>Legacy Finance Academy Pro • Arquitectura Web v4.0 Final Extendida</strong><br>
        Infraestructura Cloud de costo cero operando de manera eficiente en GitHub Pages.<br>
        Desarrollado para Promover la Inclusión Económica Escolar y el Éxito Comercial Emprendedor • 2026
    </div>

    <script>
        let currentActiveLevel = 'junior';
        let chartInstanceDoughnut = null;

        const databaseContent = {
            junior: {
                quote: '"No ahorres lo que queda después de gastar, gasta lo que queda después de ahorrar."',
                author: "Warren Buffett",
                icon: "fas fa-seedling",
                theoryCards: [
                    { h: "🌱 La Filosofía del Nivel Semilla", p: "Cada gran fortuna, empresa exitosa o meta cumplida nace exactamente de la misma manera: cuidando y dándole un propósito a las primeras monedas. El dinero no aparece por arte de magia; representa una porción de tiempo, valor e ingenio que entregamos a nuestra comunidad a través del trabajo o la ayuda." },
                    { h: "👑 La Regla de Oro del Chanchito de Oro", p: "El error financiero más común entre las personas es guardar el dinero que les sobra al final de la semana después de haber comprado dulces, antojos o juegos. Los verdaderos expertos aplican la regla inversa: 'Págate a ti mismo primero'. Apenas recibas una propina o un pago, congela de inmediato un porcentaje fijo (mínimo el 20%) en tu alcancía. Ese dinero está prohibido tocarse; es la base de tu futuro." },
                    { h: "🛑 El Peligro Oculto de los 'Gastos Hormiga'", p: "Se les llama gastos hormiga a esas pequeñas monedas que gastas a diario casi sin darte cuenta: un caramelo a la salida, un empaque decorativo, un refresco extra. Individualmente parecen insignificantes (un par de soles), pero si sumas ese gasto hormiga durante los 30 días del mes, descubrirás que se ha devorado el dinero con el que habías podido comprar el libro, la ropa o el accesorio tecnológico que tanto deseabas." },
                    { h: "🎯 El Filtro de Decisiones 'Anti-Antojos'", p: "Cuando sientas un deseo incontrolable por comprar un objeto variable o de moda en internet o en la tienda, aplícale el truco de las 24 horas. Regresa a tu casa, conversa, duerme bien y mantén la mente fría. Si al día siguiente sigues queriendo ese objeto con la misma urgencia, evalúa su compra. Te darás cuenta de que el 85% de las veces la emoción desaparece, ahorrándote mucho dinero." }
                ],
                quizQuestions: [
                    { q: "Si recibes una propina de S/ 40 por tus buenas notas, ¿cuál es la acción correcta según el Nivel Semilla?", o: ["Gastar todo el capital en antojos y dulces ese mismo fin de semana", "Separar inmediatamente S/ 8 para tu fondo de reserva inamovible antes de planear otros consumos", "Prestarle el dinero a un compañero sin registrarlo en tu cuaderno de control"], a: 1 }
                ]
            },
            emprende: {
                quote: '"El precio es lo que pagas. El valor es lo que recibes."',
                author: "Warren Buffett",
                icon: "fas fa-store",
                theoryCards: [
                    { h: "📊 La Estructura de los Costos Reales", p: "Vender un producto en el colegio a S/ 5 habiéndolo adquirido a S/ 3 en el mercado mayorista no significa que estés ganando S/ 2 netos. Para conocer tu verdadera rentabilidad, debes calcular los costos invisibles: el dinero de los pasajes que usaste para ir a comprarlo, las bolsas plásticas de empaque, las servilletas y el tiempo invertido en venderlo. Si no mides tus costos reales unitarios, estás subsidiando pérdidas sin saberlo." },
                    { h: "🛡️ El Capital de Trabajo es Intocable", p: "El capital de trabajo es la cantidad total de dinero que requiere tu negocio para comprar su mercadería o insumos iniciales antes de abrir las puertas. Este fondo es sagrado y corporativo. Si utilizas las monedas del capital de trabajo para comprarte un antojo personal o un almuerzo, el negocio se quedará sin dinero para reponer stock al día siguiente, provocando una quiebra técnica inmediata." },
                    { h: "📈 El Punto de Equilibrio Operativo", p: "Consiste en el cálculo matemático exacto que te dice cuántas unidades de tu producto necesitas vender como mínimo para recuperar la inversión total sin ganar ni perder un solo sol. Toda unidad que logres comercializar por encima de ese número crítico representa ganancia líquida pura para tu caja neta." }
                ],
                quizQuestions: [
                    { q: "Si para armar tu negocio de bocaditos escolares gastas S/ 50 en insumos y vendes todo a S/ 90, ¿qué representan los S/ 50 originales?", o: ["La utilidad neta lograda", "El capital de trabajo necesario para la recompra de mercadería", "Un gasto hormiga perdido"], a: 1 }
                ]
            },
            inversion: {
                quote: '"La riqueza no consiste en tener grandes posesiones, sino en tener pocas necesidades."',
                author: "Epicteto",
                icon: "fas fa-chart-line",
                theoryCards: [
                    { h: "📈 El Algoritmo Exponencial del Interés Compuesto", p: "Consiste en la capitalización cíclica de las ganancias. Al dejar tus fondos guardados en un vehículo de inversión, el interés que ganas no se gasta, sino que se fusiona automáticamente con tu capital original. Al siguiente ciclo, ganarás nuevos intereses sobre los intereses acumulados anteriores, creando un efecto de bola de nieve exponencial a lo largo de los años." },
                    { h: "🏦 Filtro de Crecimiento Seguro: La Tasa TREA", p: "Los bancos comerciales grandes suelen invertir mucho dinero en publicidad masiva, pero pagan tasas muy bajas. Los inversores inteligentes comparan siempre la TREA (Tasa de Rendimiento Efectiva Anual) de las Cajas Municipales o Rurales supervisadas por la SBS, las cuales suelen pagar hasta el triple por tus ahorros inmovilizados a plazo fijo." },
                    { h: "🛡️ Mitigación del Riesgo Mediante Diversificación", p: "La regla fundamental del inversionista es: 'No pongas todos tus huevos en la misma canasta'. Distribuir tu capital acumulado en diferentes herramientas económicas o negocios complementarios absorbe el impacto negativo en caso de que un sector sufra volatilidad." }
                ],
                quizQuestions: [
                    { q: "¿Qué métrica financiera determina la cantidad exacta de dinero neto que ganarás al dejar un fondo a plazo fijo?", o: ["La TCEA que aplican las tarjetas para compras a crédito", "La TREA que pagan las entidades financieras supervisadas", "La tasa de devaluación del tipo de cambio diario"], a: 1 }
                ]
            }
        };

        function switchLevel(levelKey) {
            currentActiveLevel = levelKey;
            document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
            document.getElementById(`nav-${levelKey}`).classList.add('active');
            
            // Cambiar Frase Dinámica
            document.getElementById('level-quote').innerHTML = `
                "${databaseContent[levelKey].quote}"
                <span class="quote-author">— ${databaseContent[levelKey].author}</span>
            `;

            // Cambiar Ilustración Vectorial
            document.getElementById('vector-box').innerHTML = `<i class="${databaseContent[levelKey].icon}"></i>`;

            // Cargar Tarjetas Teóricas Ampliadas
            const deck = document.getElementById('theory-deck-content');
            deck.innerHTML = "";
            databaseContent[levelKey].theoryCards.forEach((card, idx) => {
                deck.innerHTML += `
                    <div class="theory-flashcard" onclick="unlockReadingBadge()">
                        <h3><span>Lección ${idx+1}</span> ${card.h}</h3>
                        <p>${card.p}</p>
                    </div>`;
            });

            // Cargar Preguntas del Cuestionario
            const quizRoot = document.getElementById('quiz-block-root');
            quizRoot.innerHTML = "";
            databaseContent[levelKey].quizQuestions.forEach((item, qIdx) => {
                let optionsData = "";
                item.o.forEach((opt, oIdx) => {
                    optionsData += `<div class="option-item" data-q="${qIdx}" data-o="${oIdx}" onclick="captureOptionSelect(this)"><i class="far fa-circle"></i> ${opt}</div>`;
                });
                quizRoot.innerHTML += `<div><p style="font-weight:600; margin-bottom:12px; color:white; font-size:0.95rem;">${item.q}</p>${optionsData}</div>`;
            });

            // Resetear vistas
            document.getElementById('panel-budget-res').style.display = 'none';
            document.getElementById('panel-coach-ai').style.display = 'none';
            document.getElementById('panel-goal-res').style.display = 'none';
            document.getElementById('panel-currency-res').style.display = 'none';
            document.getElementById('panel-quiz-alert').style.display = 'none';
            if(chartInstanceDoughnut) document.getElementById('chartDoughnutCanvas').style.display = 'none';

            // Mensajes de bienvenida dinámicos del Mentor
            let chatText = "Terminal activa. ¿Qué variables de capital analizamos hoy?";
            if(levelKey === 'junior') chatText = "¡Hola crack! Soy tu mentor del Nivel Semilla. Estoy listo para enseñarte a liquidar los gastos hormiga y multiplicar el tamaño de tu alcancía.";
            if(levelKey === 'emprende') chatText = "Saludos socio. Vamos a auditar minuciosamente la estructura de costos de tu emprendimiento para blindar tu flujo de caja.";
            document.getElementById('chat-welcome').innerText = chatText;
        }

        function unlockReadingBadge() {
            document.getElementById('badge-read').classList.add('unlocked');
        }

        function captureOptionSelect(targetElement) {
            const rowOptions = targetElement.parentElement.querySelectorAll('.option-item');
            rowOptions.forEach(opt => {
                opt.classList.remove('selected');
                opt.querySelector('i').className = "far fa-circle";
            });
            targetElement.classList.add('selected');
            targetElement.querySelector('i').className = "fas fa-check-circle";
            targetElement.parentElement.setAttribute('data-user-selection', targetElement.getAttribute('data-o'));
        }

        function processQuizGrade() {
            const items = document.getElementById('quiz-block-root').children;
            let finalScore = 0;
            let maxItems = databaseContent[currentActiveLevel].quizQuestions.length;

            for(let i=0; i<maxItems; i++) {
                const block = items[i];
                const selected = block.getAttribute('data-user-selection');
                if(selected == databaseContent[currentActiveLevel].quizQuestions[i].a) finalScore++;
            }

            const alertBox = document.getElementById('panel-quiz-alert');
            alertBox.style.display = 'block';

            if(finalScore === maxItems) {
                alertBox.innerHTML = "<i class='fas fa-check-circle'></i> ¡EXAMEN PERFECTO! Desbloqueas el Sello de Oro de la academia.";
                alertBox.style.background = "#0c2417";
                alertBox.style.color = "#52b788";
                document.getElementById('badge-test').classList.add('unlocked');
            } else {
                alertBox.innerHTML = "<i class='fas fa-times-circle'></i> Calificación insuficiente. Repasa las lecciones de arriba e inténtalo de nuevo.";
                alertBox.style.background = "#2b0d0d";
                alertBox.style.color = "#e63946";
            }
        }

        function runBudgetMatrix() {
            const income = parseFloat(document.getElementById('income-value').value) || 0;
            if(income <= 0) return alert("Ingresa un monto de dinero válido.");

            const opNec = income * 0.50;
            const opDes = income * 0.30;
            const opAho = income * 0.20;

            const panel = document.getElementById('panel-budget-res');
            panel.style.display = 'block';
            panel.innerHTML = `
                <p style="font-weight:700; color:var(--accent-gold); margin-bottom:8px;"><i class="fas fa-chart-pie"></i> Distribución Presupuestal Ejecutada:</p>
                <ul>
                    <li><span>🛠️ Necesidades y Operaciones (50%):</span> <strong>S/ ${opNec.toFixed(2)}</strong></li>
                    <li><span>🍿 DeseosVariables / Ocio (30%):</span> <strong>S/ ${opDes.toFixed(2)}</strong></li>
                    <li><span>🐷 Ahorro Patrimonial Seguro (20%):</span> <strong style="color:var(--success-green)">S/ ${opAho.toFixed(2)}</strong></li>
                </ul>
            `;

            document.getElementById('badge-calc').classList.add('unlocked');

            // Renderizar Gráfico
            document.getElementById('chartDoughnutCanvas').style.display = 'block';
            if(chartInstanceDoughnut) chartInstanceDoughnut.destroy();

            const ctx = document.getElementById('chartDoughnutCanvas').getContext('2d');
            chartInstanceDoughnut = new Chart(ctx, {
                type: 'doughnut',
                data: {
                    labels: ['Necesidades (50%)', 'Deseos (30%)', 'Ahorro (20%)'],
                    datasets: [{
                        data: [opNec, opDes, opAho],
                        backgroundColor: ['#0f3621', '#d4af37', '#1b5335'],
                        borderColor: '#09120e'
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { labels: { color: '#f4f7f5', font: { weight: 'bold' } } } }
                }
            });
        }

        function runGoalPlanner() {
            const name = document.getElementById('goal-title').value;
            const cost = parseFloat(document.getElementById('goal-total-cost').value) || 0;
            const monthly = parseFloat(document.getElementById('goal-monthly-save').value) || 0;

            if(cost <= 0 || monthly <= 0) return alert("Ingresa montos superiores a cero.");

            const totalMonths = Math.ceil(cost / monthly);
            const panel = document.getElementById('panel-goal-res');
            panel.style.display = 'block';
            panel.innerHTML = `<i class="fas fa-flag-checkered" style="color:var(--accent-gold)"></i> Proyección: Financiar tu meta de mediano plazo (<em>${name}</em>) demandará un periodo de <strong>${totalMonths} meses</strong> de disciplina contable ininterrumpida.`;
        }

        function runCurrencySimulator() {
            const penAmount = parseFloat(document.getElementById('currency-pen').value) || 0;
            const exchangeRate = parseFloat(document.getElementById('currency-rate').value) || 0;

            if(penAmount <= 0 || exchangeRate <= 0) return alert("Completa los valores monetarios.");

            const usdResult = penAmount / exchangeRate;
            const panel = document.getElementById('panel-currency-res');
            panel.style.display = 'block';
            panel.innerHTML = `<i class="fas fa-shield-alt" style="color:var(--success-green)"></i> Tus <strong>S/ ${penAmount.toFixed(2)} Soles</strong> representan un valor refugio de <strong>$ ${usdResult.toFixed(2)} Dólares Americanos</strong> a un tipo de cambio de S/ ${exchangeRate.toFixed(2)}.`;
        }

        function triggerCoachAI() {
            const income = parseFloat(document.getElementById('income-value').value) || 0;
            if(income <= 0) return alert("Calcula una matriz matemática primero.");

            runBudgetMatrix();
            const aho = income * 0.20;
            const des = income * 0.30;
            const coachPanel = document.getElementById('panel-coach-ai');
            coachPanel.style.display = 'block';
            coachPanel.innerHTML = "<i class='fas fa-spinner fa-spin'></i> Ejecutando vectores predictivos corporativos...";

            setTimeout(() => {
                let reportText = "";
                if(currentActiveLevel === 'junior') {
                    reportText = `Auditoría del Coach Semilla: Tus S/ ${aho.toFixed(2)} mensuales de ahorro deben blindarse contra los gastos hormiga. Te sugiero usar el 'Filtro anti-antojos' en el recreo escolar. Evita pulverizar tus S/ ${des.toFixed(2)} de deseos variables de manera descontrolada.`;
                } else if(currentActiveLevel === 'emprende') {
                    reportText = `Estrategia de Negocios EPT: Operar con S/ ${income} exige proteger tu capital de trabajo. No combines las ganancias con tus gastos del día. Te recomiendo derivar un 10% del fondo de deseos directo a inventario al por mayor para optimizar tus márgenes netos.`;
                } else {
                    reportText = `Análisis Financiero de Portafolio: Registrar S/ ${aho.toFixed(2)} constantes te permite aprovechar el interés compuesto. En lugar de dejarlo inactivo, busca las tasas TREA que pagan las Cajas Municipales de la región sur supervisadas por la SBS.`;
                }
                coachPanel.innerHTML = `<strong>🤖 Dictamen de Auditoría IA:</strong><br>${reportText}`;
            }, 700);
        }

        function switchChatDisplay() {
            const chat = document.getElementById('chatWindowBox');
            chat.style.display = chat.style.display === 'flex' ? 'none' : 'flex';
        }

        function executeChatSpeech() {
            const input = document.getElementById('textChatInput');
            const userText = input.value.trim();
            if(!userText) return;

            const chatArea = document.getElementById('chatStreamArea');
            chatArea.innerHTML += `<div class="msg user chat-bubble">${userText}</div>`;
            input.value = "";
            chatArea.scrollTop = chatArea.scrollHeight;

            const uid = "ai-" + Date.now();
            chatArea.innerHTML += `<div class="msg ia chat-bubble" id="${uid}">Evaluando consulta contable...</div>`;
            chatArea.scrollTop = chatArea.scrollHeight;

            setTimeout(() => {
                let aiReply = "Es un excelente planteamiento analítico. Recuerda siempre mantener bajo control los costos fijos y proteger tu capital de trabajo para asegurar el flujo de caja.";
                if(currentActiveLevel === 'junior') aiReply = "¡Qué gran duda! Recuerda aplicar la regla del Chanchito de Oro: guarda hoy una porción fija de dinero antes de gastar. ¡Los gastos hormiga son el enemigo silencioso de tus metas!";
                document.getElementById(uid).innerText = aiReply;
                chatArea.scrollTop = chatArea.scrollHeight;
            }, 800);
        }

        // Carga Inicial del Sistema
        switchLevel('junior');
    </script>
</body>
</html>
