<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>UemaKids PRO — Aprende y Gana Medallas 🏅</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
  <!-- html2canvas para captura -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Comic Sans MS', 'Chalkboard SE', 'Arial Rounded MT Bold', sans-serif;
      background: linear-gradient(135deg, #a1c4fd 0%, #c2e9fb 100%);
      color: #333;
      line-height: 1.6;
      padding-bottom: 3rem;
    }

    @keyframes fadeInUp {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }
    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.05); }
      100% { transform: scale(1); }
    }
    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }

    .animated { animation: fadeInUp 1s ease-out forwards; }
    .pulse { animation: pulse 1.5s infinite; }
    .floating { animation: float 3s ease-in-out infinite; }

    header {
      text-align: center;
      padding: 1.5rem 1rem;
      background: rgba(255, 255, 255, 0.9);
      box-shadow: 0 4px 15px rgba(0,0,0,0.12);
      margin-bottom: 2rem;
    }

    .logo {
      font-size: 2.8rem;
      font-weight: bold;
      color: #ff6b6b;
      text-shadow: 2px 2px 0 #ffd166;
    }

    .welcome {
      font-size: 2rem;
      color: #4a6fa5;
      margin: 1rem 0;
      opacity: 0;
    }

    .subtitle {
      font-size: 1.2rem;
      color: #6c757d;
    }

    .welcome-box {
      max-width: 850px;
      margin: 1.5rem auto;
      padding: 1.5rem;
      background: white;
      border-radius: 20px;
      box-shadow: 0 6px 20px rgba(0,0,0,0.1);
      text-align: center;
      opacity: 0;
    }

    section {
      max-width: 950px;
      margin: 1.5rem auto;
      padding: 0 1.5rem;
    }

    h2 {
      font-size: 2rem;
      color: #ff9e44;
      text-align: center;
      margin: 2rem 0 1.5rem;
      text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
    }

    /* ÁREAS */
    .subjects {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 20px;
      margin-top: 1.5rem;
    }

    .subject-card {
      background: white;
      border-radius: 18px;
      padding: 1.4rem 1rem;
      text-align: center;
      box-shadow: 0 6px 15px rgba(0,0,0,0.08);
      transition: all 0.3s;
      opacity: 0;
      cursor: pointer;
      position: relative;
    }

    .subject-card:hover {
      transform: translateY(-8px);
      box-shadow: 0 10px 25px rgba(0,0,0,0.15);
    }

    .subject-icon {
      font-size: 3rem;
      margin-bottom: 0.8rem;
    }
    .subject-card h3 { font-size: 1.3rem; }
    .natural { color: #4CAF50; }
    .social { color: #FF9800; }
    .math { color: #2196F3; }
    .language { color: #9C27B0; }

    /* JUEGO */
    .game-section {
      background: white;
      border-radius: 20px;
      padding: 2rem;
      box-shadow: 0 8px 25px rgba(0,0,0,0.1);
      margin-top: 2rem;
      display: none;
    }

    .game-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 1.5rem;
      flex-wrap: wrap;
    }

    .game-title {
      font-size: 1.8rem;
      color: #2c3e50;
    }

    .progress-bar {
      width: 100%;
      height: 12px;
      background: #e0e0e0;
      border-radius: 6px;
      margin: 10px 0;
      overflow: hidden;
    }
    .progress-fill {
      height: 100%;
      background: linear-gradient(90deg, #4CAF50, #81C784);
      border-radius: 6px;
      width: 0%;
      transition: width 0.4s;
    }

    .question-counter {
      font-weight: bold;
      color: #666;
    }

    /* Estilos comunes a preguntas */
    .question-box {
      background: #f9f9ff;
      border-radius: 16px;
      padding: 1.8rem;
      text-align: center;
      margin: 1.5rem 0;
      font-size: 1.4rem;
      min-height: 140px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .options-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 14px;
      max-width: 700px;
      margin: 1.5rem auto;
    }

    .option-btn {
      padding: 14px;
      font-size: 1.15rem;
      border: none;
      border-radius: 12px;
      background: #e3f2fd;
      cursor: pointer;
      transition: all 0.3s;
    }
    .option-btn:hover:not(:disabled) {
      background: #bbdefb;
      transform: scale(1.03);
    }
    .option-btn:disabled {
      cursor: not-allowed;
      opacity: 0.8;
    }
    .correct { background: #81c784 !important; color: white; }
    .incorrect { background: #e57373 !important; color: white; }

    /* MATEMÁTICAS */
    .math-input {
      padding: 14px;
      font-size: 1.4rem;
      text-align: center;
      width: 140px;
      margin: 1.5rem auto;
      display: block;
      border: 3px solid #2196F3;
      border-radius: 12px;
    }

    /* LENGUAJE */
    .sentence {
      font-size: 1.5rem;
      background: #fff8e1;
      padding: 20px;
      border-radius: 12px;
      border-left: 6px solid #ffd54f;
      margin: 1.5rem auto;
      max-width: 700px;
    }

    /* BOTONES */
    .btn {
      padding: 12px 24px;
      font-size: 1.2rem;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      font-weight: bold;
      transition: all 0.3s;
      display: inline-flex;
      align-items: center;
      gap: 8px;
    }
    .btn-primary { background: #4CAF50; color: white; }
    .btn-secondary { background: #FF9800; color: white; }
    .btn-danger { background: #f44336; color: white; }
    .btn-success { background: #2196F3; color: white; }
    .btn:disabled {
      opacity: 0.6;
      cursor: not-allowed;
    }

    /* RESULTADOS */
    .results-section {
      background: white;
      border-radius: 20px;
      padding: 2.5rem;
      box-shadow: 0 10px 30px rgba(0,0,0,0.15);
      text-align: center;
      max-width: 800px;
      margin: 2rem auto;
      display: none;
    }

    .medal {
      font-size: 5rem;
      margin: 1rem 0;
      animation: pulse 2s infinite;
    }
    .medal.bronze { color: #cd7f32; }
    .medal.silver { color: #c0c0c0; }
    .medal.gold { color: #ffd700; }
    .medal.platinum { color: #b5b5b5; background: linear-gradient(45deg, #e0e0e0, #ffffff); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }

    .score-big {
      font-size: 3.5rem;
      font-weight: bold;
      margin: 1rem 0;
      color: #2c3e50;
    }

    .summary {
      background: #f5f5f5;
      padding: 1.2rem;
      border-radius: 12px;
      margin: 1.5rem 0;
      text-align: left;
    }

    /* CAPTURA */
    #capture-area {
      background: white;
      padding: 2rem;
      border-radius: 16px;
      margin: 1.5rem auto;
      max-width: 600px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      display: none;
    }

    /* FOOTER */
    footer {
      text-align: center;
      padding: 2rem;
      background: #333;
      color: white;
      margin-top: 3rem;
      font-size: 0.95rem;
    }

    @media (max-width: 600px) {
      .logo { font-size: 2.2rem; }
      .welcome { font-size: 1.5rem; }
      .options-grid { grid-template-columns: 1fr; }
      .game-header { flex-direction: column; gap: 10px; }
    }
  </style>
</head>
<body>

  <header>
    <div class="logo">Uema<span style="color:#4a6fa5;">Kids</span> PRO</div>
    <p class="subtitle">🏆 15 ejercicios por materia • Sistema de medallas • Captura para tu profesor</p>
    <div class="welcome" id="welcomeText">¡Hola, campeón/a del conocimiento! 🌟</div>
  </header>

  <div class="welcome-box animated" id="welcomeBox">
    <p>Selecciona una materia y resuelve los 15 ejercicios. ¡Gana puntos, medallas y envía tu constancia al profesor! 📜✨</p>
  </div>

  <section>
    <h2>📚 Elige tu Materia</h2>
    <div class="subjects">
      <div class="subject-card bounce" onclick="startGame('ciencias')">
        <div class="subject-icon natural"><i class="fas fa-flask"></i></div>
        <h3>Ciencias Naturales</h3>
        <p>15 preguntas<br><small>Animales, plantas, cuerpo humano</small></p>
      </div>
      <div class="subject-card bounce" onclick="startGame('sociales')">
        <div class="subject-icon social"><i class="fas fa-landmark"></i></div>
        <h3>Estudios Sociales</h3>
        <p>15 preguntas<br><small>Historia, geografía, ciudadanía</small></p>
      </div>
      <div class="subject-card bounce" onclick="startGame('matematica')">
        <div class="subject-icon math"><i class="fas fa-calculator"></i></div>
        <h3>Matemática</h3>
        <p>15 ejercicios<br><small>Operaciones, problemas, lógica</small></p>
      </div>
      <div class="subject-card bounce" onclick="startGame('lenguaje')">
        <div class="subject-icon language"><i class="fas fa-book-open"></i></div>
        <h3>Lenguaje</h3>
        <p>15 oraciones<br><small>Ortografía, gramática, puntuación</small></p>
      </div>
    </div>
  </section>

  <!-- ZONA DE JUEGO -->
  <section id="game-container" class="game-section">
    <div class="game-header">
      <h2 class="game-title" id="current-game-title">Cargando...</h2>
      <div>
        <span class="question-counter"><span id="current-q">0</span>/15</span>
      </div>
    </div>
    <div class="progress-bar">
      <div class="progress-fill" id="progress-fill"></div>
    </div>

    <div class="question-box" id="question-box">
      ¡Prepárate para tu primera pregunta!
    </div>

    <div id="options-container"></div>

    <button class="btn btn-success" id="next-btn" onclick="nextQuestion()" style="display:none; margin:1.5rem auto;">
      <i class="fas fa-arrow-right"></i> Siguiente
    </button>
  </section>

  <!-- RESULTADOS -->
  <section id="results-section" class="results-section">
    <h2>🎉 ¡Felicidades! Has terminado</h2>
    <div class="medal" id="medal-display">🏅</div>
    <div class="score-big" id="final-score">0/15</div>
    <p id="medal-text">¡Sigue practicando para subir de nivel!</p>

    <div class="summary">
      <h3>📊 Resumen</h3>
      <p><strong>Materia:</strong> <span id="result-subject">—</span></p>
      <p><strong>Correctas:</strong> <span id="correct-count">0</span></p>
      <p><strong>Incorrectas:</strong> <span id="incorrect-count">0</span></p>
      <p><strong>Puntaje:</strong> <span id="points-count">0</span> pts</p>
    </div>

    <p>¿Quieres enviar tu constancia al profesor?</p>
    <button class="btn btn-primary" onclick="showCapture()">
      <i class="fas fa-file-export"></i> Generar constancia
    </button>
    <button class="btn btn-secondary" onclick="restartGame()" style="margin-left:10px;">
      <i class="fas fa-redo"></i> Jugar de nuevo
    </button>
  </section>

  <!-- ÁREA DE CAPTURA -->
  <div id="capture-area">
    <div id="certificado">
      <h2 style="color:#2c3e50; margin-bottom:10px;">📜 CONSTANCIA DE APRENDIZAJE</h2>
      <p><strong>Estudiante:</strong> <span id="cert-name">Nombre del estudiante</span></p>
      <p><strong>Materia:</strong> <span id="cert-subject">—</span></p>
      <p><strong>Puntaje:</strong> <span id="cert-score">0/15</span> ✅</p>
      <p><strong>Medalla:</strong> <span id="cert-medal">—</span></p>
      <p><small>Fecha: <span id="cert-date">—</span></small></p>
      <hr style="margin:15px 0; border:0; border-top:1px dashed #aaa;">
      <p style="font-style:italic; color:#555;">"Aprender es como remar contra la corriente: hay que seguir adelante"</p>
      <p><strong>UemaKids PRO</strong> — Ministerio de Educación del Ecuador</p>
    </div>
    <br>
    <button class="btn btn-success" onclick="takeScreenshot()">
      <i class="fas fa-camera"></i> Capturar y descargar
    </button>
    <button class="btn btn-secondary" onclick="hideCapture()" style="margin-left:10px;">
      Cancelar
    </button>
    <p id="download-link" style="margin-top:15px; display:none;"></p>
  </div>

  <footer>
    <p>© 2025 <strong>UemaKids PRO</strong> — Plataforma gamificada para 5.º, 6.º y 7.º de básica</p>
    <p>Diseñado con ❤️ para el sistema educativo ecuatoriano</p>
  </footer>

  <script>
    // ===== DATOS: 15 ejercicios por materia =====
    const database = {
      ciencias: [
        { q: "¿Cuál es el órgano más grande del cuerpo humano?", a: ["Corazón", "Hígado", "Piel", "Cerebro"], correct: 2 },
        { q: "¿Qué proceso usan las plantas para fabricar su alimento?", a: ["Fotosíntesis", "Digestión", "Respiración", "Polinización"], correct: 0 },
        { q: "¿Cuántos huesos tiene el cuerpo humano adulto?", a: ["206", "300", "150", "250"], correct: 0 },
        { q: "¿Cuál de estos es un mamífero?", a: ["Tiburón", "Pingüino", "Delfín", "Serpiente"], correct: 2 },
        { q: "¿Dónde se encuentran los pulmones?", a: ["Abdomen", "Tórax", "Cuello", "Pelvis"], correct: 1 },
        { q: "¿Qué gas absorben las plantas del aire?", a: ["Oxígeno", "Nitrógeno", "Dióxido de carbono", "Hidrógeno"], correct: 2 },
        { q: "¿Cuál NO es un sentido humano?", a: ["Vista", "Oído", "Telepatía", "Gusto"], correct: 2 },
        { q: "¿Qué animal es un insecto?", a: ["Araña", "Ciempiés", "Mariposa", "Cangrejo"], correct: 2 },
        { q: "¿Cuál es la capa más externa de la Tierra?", a: ["Núcleo", "Manto", "Corteza", "Atmósfera"], correct: 2 },
        { q: "¿Qué órgano produce la bilis?", a: ["Estómago", "Páncreas", "Hígado", "Riñón"], correct: 2 },
        { q: "¿Cuál es el hábitat de los pingüinos?", a: ["Ártico", "Antártida", "Desierto", "Selva"], correct: 1 },
        { q: "¿Qué tipo de energía proviene del Sol?", a: ["Eólica", "Hidráulica", "Solar", "Geotérmica"], correct: 2 },
        { q: "¿Cuántos litros de agua tiene aproximadamente el cuerpo humano?", a: ["20 L", "40 L", "60 L", "80 L"], correct: 1 },
        { q: "¿Cuál es el único mamífero volador?", a: ["Ave colibrí", "Ardilla voladora", "Murciélago", "Pájaro carpintero"], correct: 2 },
        { q: "¿Qué parte de la planta absorbe agua y nutrientes?", a: ["Tallo", "Hojas", "Flores", "Raíces"], correct: 3 }
      ],
      sociales: [
        { q: "¿Cuál es la capital del Ecuador?", a: ["Guayaquil", "Cuenca", "Quito", "Ambato"], correct: 2 },
        { q: "¿En qué año se proclamó la Independencia de Guayaquil?", a: ["1809", "1820", "1822", "1830"], correct: 1 },
        { q: "¿Cuántas regiones naturales tiene Ecuador?", a: ["2", "3", "4", "5"], correct: 2 },
        { q: "¿Qué provincia NO pertenece a la Costa?", a: ["Manabí", "Esmeraldas", "Los Ríos", "Tungurahua"], correct: 3 },
        { q: "¿Quién fue el primer presidente del Ecuador?", a: ["Juan José Flores", "Eloy Alfaro", "Vicente Rocafuerte", "Gabriel García Moreno"], correct: 0 },
        { q: "¿En qué región se encuentra el volcán Cotopaxi?", a: ["Costa", "Sierra", "Oriente", "Insular"], correct: 1 },
        { q: "¿Cuál es el río más largo del Ecuador?", a: ["Guayas", "Esmeraldas", "Pastaza", "Napo"], correct: 0 },
        { q: "¿Qué significa 'Kawsay' en kichwa?", a: ["Agua", "Vida", "Montaña", "Sol"], correct: 1 },
        { q: "¿Cuál fue la primera ciudad en declarar su independencia en Ecuador?", a: ["Quito", "Cuenca", "Guayaquil", "Loja"], correct: 0 },
        { q: "¿Cuántos idiomas oficiales tiene Ecuador?", a: ["1", "2", "13", "37"], correct: 2 },
        { q: "¿En qué isla está la Estación Científica Charles Darwin?", a: ["Isabela", "Santa Cruz", "San Cristóbal", "Floreana"], correct: 1 },
        { q: "¿Qué cultura prehispánica construyó Ingapirca?", a: ["Valdivia", "Machalilla", "Inca", "Quitu-Cara"], correct: 2 },
        { q: "¿Cuál es la provincia más grande del Ecuador?", a: ["Pichincha", "Guayas", "Pastaza", "Orellana"], correct: 2 },
        { q: "¿Qué derecho tienen los niños según la Constitución?", a: ["Trabajar desde los 10 años", "No ir a la escuela", "Alimentación, salud y educación", "Votar a los 12 años"], correct: 2 },
        { q: "¿Qué ciudad es conocida como 'La Atenas del Ecuador'?", a: ["Quito", "Guayaquil", "Cuenca", "Ambato"], correct: 2 }
      ],
      matematica: [
        { q: "18 + 25 = ?", type: 'calc', correct: 43 },
        { q: "72 - 39 = ?", type: 'calc', correct: 33 },
        { q: "6 × 7 = ?", type: 'calc', correct: 42 },
        { q: "¿Cuál es el doble de 36?", type: 'calc', correct: 72 },
        { q: "¿Cuánto es la mitad de 98?", type: 'calc', correct: 49 },
        { q: "54 ÷ 6 = ?", type: 'calc', correct: 9 },
        { q: "¿Cuál número es mayor: 3.4 o 3.04?", type: 'calc', correct: 3.4 },
        { q: "¿Cuántos minutos hay en 2 horas y media?", type: 'calc', correct: 150 },
        { q: "¿Cuál es el perímetro de un cuadrado de lado 8 cm?", type: 'calc', correct: 32 },
        { q: "¿Cuánto es 25% de 80?", type: 'calc', correct: 20 },
        { q: "¿Cuál es el área de un rectángulo de 9 m × 5 m?", type: 'calc', correct: 45 },
        { q: "¿Cuántos lados tiene un hexágono?", type: 'calc', correct: 6 },
        { q: "¿Qué número sigue? 5, 10, 15, 20, ___", type: 'calc', correct: 25 },
        { q: "¿Cuántos grados tiene un ángulo recto?", type: 'calc', correct: 90 },
        { q: "¿Cuál es la raíz cuadrada de 64?", type: 'calc', correct: 8 }
      ],
      lenguaje: [
        { q: "ayer fuimos al parque a jugar", fix: "Ayer fuimos al parque a jugar.", correct: false },
        { q: "¿Donde esta mi mochila?", fix: "¿Dónde está mi mochila?", correct: false },
        { q: "ellos estudian todos los dias", fix: "Ellos estudian todos los días.", correct: false },
        { q: "Mi hermano mayor se llama Carlos.", correct: true, fix: "✅ Correcto" },
        { q: "la tierra gira alrededor del sol", fix: "La Tierra gira alrededor del Sol.", correct: false },
        { q: "Hoy es lunes, martes y miércoles.", correct: false, fix: "Hoy es lunes." },
        { q: "¿Quién quiere jugar conmigo?", correct: true, fix: "✅ Correcto" },
        { q: "mi mama me compro un libro", fix: "Mi mamá me compró un libro.", correct: false },
        { q: "El perro de Juan es muy jugueton", fix: "El perro de Juan es muy juguetón.", correct: false },
        { q: "¡Que bonito día!", fix: "¡Qué bonito día!", correct: false },
        { q: "Voy a comprar pan, leche y huevos.", correct: true, fix: "✅ Correcto" },
        { q: "los niños juegan en el patio", fix: "Los niños juegan en el patio.", correct: false },
        { q: "¿Cuantos años tienes?", fix: "¿Cuántos años tienes?", correct: false },
        { q: "El Amazonas es el río mas largo del mundo.", fix: "El Amazonas es el río más largo del mundo.", correct: false },
        { q: "Ella canta, baila y actua muy bien.", fix: "Ella canta, baila y actúa muy bien.", correct: false }
      ]
    };

    // ===== ESTADO GLOBAL =====
    let gameState = {
      currentSubject: '',
      questionIndex: 0,
      score: 0,
      answers: [] // { correct: true/false }
    };

    // ===== FUNCIONES =====
    function startGame(subject) {
      gameState = {
        currentSubject: subject,
        questionIndex: 0,
        score: 0,
        answers: []
      };
      document.getElementById('game-container').style.display = 'block';
      document.getElementById('results-section').style.display = 'none';
      loadQuestion();
    }

    function loadQuestion() {
      const { currentSubject, questionIndex } = gameState;
      const questions = database[currentSubject];
      const q = questions[questionIndex];

      // Actualizar UI
      document.getElementById('current-q').textContent = questionIndex + 1;
      document.getElementById('progress-fill').style.width = `${((questionIndex)/15)*100}%`;

      // Título por materia
      const titles = {
        ciencias: '🔬 Ciencias Naturales',
        sociales: '🌎 Estudios Sociales',
        matematica: '➕ Matemática',
        lenguaje: '✍️ Lenguaje'
      };
      document.getElementById('current-game-title').textContent = titles[currentSubject];

      // Limpiar
      document.getElementById('question-box').innerHTML = '';
      document.getElementById('options-container').innerHTML = '';
      document.getElementById('next-btn').style.display = 'none';

      if (currentSubject === 'matematica') {
        document.getElementById('question-box').textContent = q.q;
        const input = document.createElement('input');
        input.type = 'number';
        input.id = 'math-input';
        input.className = 'math-input';
        input.placeholder = '?';
        document.getElementById('options-container').appendChild(input);
        document.getElementById('options-container').innerHTML += 
          `<br><button class="btn btn-success" onclick="submitMath()">✅ Responder</button>`;
      } else if (currentSubject === 'lenguaje') {
        document.getElementById('question-box').innerHTML = `<div class="sentence">${q.q}</div>`;
        const btns = `
          <button class="btn btn-primary" onclick="submitLanguage(true)">✅ Correcto</button>
          <button class="btn btn-danger" style="margin-left:10px;" onclick="submitLanguage(false)">❌ Incorrecto</button>
        `;
        document.getElementById('options-container').innerHTML = btns;
      } else {
        // Trivia normal
        document.getElementById('question-box').textContent = q.q;
        const grid = document.createElement('div');
        grid.className = 'options-grid';
        q.a.forEach((opt, i) => {
          const btn = document.createElement('button');
          btn.className = 'option-btn';
          btn.textContent = opt;
          btn.onclick = () => selectOption(i === q.correct, btn);
          grid.appendChild(btn);
        });
        document.getElementById('options-container').appendChild(grid);
      }
    }

    function selectOption(isCorrect, btn) {
      const btns = document.querySelectorAll('.option-btn');
      btns.forEach(b => {
        b.disabled = true;
        if (b === btn) {
          b.classList.add(isCorrect ? 'correct' : 'incorrect');
        } else if (b.textContent === database[gameState.currentSubject][gameState.questionIndex].a[
          database[gameState.currentSubject][gameState.questionIndex].correct
        ]) {
          b.classList.add('correct');
        }
      });

      recordAnswer(isCorrect);
    }

    function submitMath() {
      const input = document.getElementById('math-input');
      const value = parseFloat(input.value);
      const correct = database[gameState.currentSubject][gameState.questionIndex].correct;
      const isCorrect = Math.abs(value - correct) < 0.01;
      recordAnswer(isCorrect);
    }

    function submitLanguage(userSaidCorrect) {
      const realCorrect = database[gameState.currentSubject][gameState.questionIndex].correct;
      const isCorrect = (userSaidCorrect === realCorrect);
      recordAnswer(isCorrect);
    }

    function recordAnswer(isCorrect) {
      gameState.answers.push({ correct: isCorrect });
      if (isCorrect) gameState.score++;

      // Mostrar retroalimentación
      setTimeout(() => {
        document.getElementById('next-btn').style.display = 'inline-block';
      }, 800);
    }

    function nextQuestion() {
      gameState.questionIndex++;
      if (gameState.questionIndex < 15) {
        loadQuestion();
      } else {
        showResults();
      }
    }

    function showResults() {
      const { score, currentSubject, answers } = gameState;
      const correct = answers.filter(a => a.correct).length;
      const incorrect = 15 - correct;

      // Medalla
      let medal, medalText, medalClass;
      if (score >= 14) {
        medal = '🥇'; medalText = 'Medalla de PLATINO - ¡Eres un genio!'; medalClass = 'platinum';
      } else if (score >= 11) {
        medal = '🥇'; medalText = 'Medalla de ORO - ¡Excelente trabajo!'; medalClass = 'gold';
      } else if (score >= 8) {
        medal = '🥈'; medalText = 'Medalla de PLATA - ¡Muy bien!'; medalClass = 'silver';
      } else {
        medal = '🥉'; medalText = 'Medalla de BRONCE - ¡Sigue practicando!'; medalClass = 'bronze';
      }

      // Actualizar resultados
      document.getElementById('medal-display').textContent = medal;
      document.getElementById('medal-display').className = 'medal ' + medalClass;
      document.getElementById('medal-text').textContent = medalText;
      document.getElementById('final-score').textContent = `${score}/15`;
      document.getElementById('correct-count').textContent = correct;
      document.getElementById('incorrect-count').textContent = incorrect;
      document.getElementById('points-count').textContent = score * 10;
      document.getElementById('result-subject').textContent = 
        ({ciencias:'Ciencias', sociales:'Estudios Sociales', matematica:'Matemática', lenguaje:'Lenguaje'})[currentSubject];

      document.getElementById('game-container').style.display = 'none';
      document.getElementById('results-section').style.display = 'block';
      document.getElementById('results-section').scrollIntoView({ behavior: 'smooth' });
    }

    function showCapture() {
      document.getElementById('capture-area').style.display = 'block';
      // Llenar certificado
      const { score, currentSubject } = gameState;
      document.getElementById('cert-subject').textContent = 
        ({ciencias:'Ciencias Naturales', sociales:'Estudios Sociales', matematica:'Matemática', lenguaje:'Lenguaje'})[currentSubject];
      document.getElementById('cert-score').textContent = `${score}/15`;
      
      let medalName;
      if (score >= 14) medalName = 'Platino';
      else if (score >= 11) medalName = 'Oro';
      else if (score >= 8) medalName = 'Plata';
      else medalName = 'Bronce';
      document.getElementById('cert-medal').textContent = medalName;

      const now = new Date();
      document.getElementById('cert-date').textContent = now.toLocaleDateString('es-EC');

      document.getElementById('capture-area').scrollIntoView({ behavior: 'smooth' });
    }

    function hideCapture() {
      document.getElementById('capture-area').style.display = 'none';
    }

    function takeScreenshot() {
      const element = document.getElementById('certificado');
      html2canvas(element).then(canvas => {
        const link = document.createElement('a');
        link.download = `UemaKids_${gameState.currentSubject}_${new Date().getTime()}.png`;
        link.href = canvas.toDataURL('image/png');
        link.click();
        document.getElementById('download-link').innerHTML = 
          `<a href="${link.href}" download="${link.download}" class="btn btn-primary" style="font-size:1rem;">
            <i class="fas fa-download"></i> Descargar constancia
          </a>`;
        document.getElementById('download-link').style.display = 'block';
      });
    }

    function restartGame() {
      document.getElementById('results-section').style.display = 'none';
      document.getElementById('capture-area').style.display = 'none';
      // Volver al inicio
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    // Animaciones iniciales
    document.addEventListener('DOMContentLoaded', () => {
      setTimeout(() => {
        document.getElementById('welcomeText').style.opacity = '1';
        document.getElementById('welcomeText').style.animation = 'fadeInUp 1.2s ease-out';
      }, 500);

      const cards = document.querySelectorAll('.subject-card');
      cards.forEach((card, i) => {
        setTimeout(() => {
          card.style.opacity = '1';
          card.style.animation = `fadeInUp 0.8s ease-out ${i * 0.15}s forwards`;
        }, 300 + i * 150);
      });
    });
  </script>

</body>
</html>

