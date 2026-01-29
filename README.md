<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Glosario de Términos de Debate</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
            padding: 20px;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            overflow: hidden;
        }
        
        header {
            background: linear-gradient(135deg, #1a2980, #26d0ce);
            color: white;
            padding: 40px 30px;
            text-align: center;
        }
        
        h1 {
            font-size: 2.8rem;
            margin-bottom: 10px;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.2);
        }
        
        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
            max-width: 800px;
            margin: 0 auto;
        }
        
        .controls {
            display: flex;
            justify-content: center;
            padding: 20px;
            background-color: #f0f4f8;
            border-bottom: 1px solid #e1e8f0;
        }
        
        .search-box {
            display: flex;
            width: 100%;
            max-width: 500px;
        }
        
        #searchInput {
            flex: 1;
            padding: 12px 20px;
            border: 2px solid #ddd;
            border-radius: 50px 0 0 50px;
            font-size: 1rem;
            transition: border-color 0.3s;
        }
        
        #searchInput:focus {
            outline: none;
            border-color: #26d0ce;
        }
        
        #searchBtn {
            background-color: #1a2980;
            color: white;
            border: none;
            padding: 0 25px;
            border-radius: 0 50px 50px 0;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        #searchBtn:hover {
            background-color: #0f1c66;
        }
        
        .sort-buttons {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-top: 15px;
        }
        
        .sort-btn {
            background-color: white;
            border: 2px solid #1a2980;
            color: #1a2980;
            padding: 8px 16px;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: 600;
        }
        
        .sort-btn:hover, .sort-btn.active {
            background-color: #1a2980;
            color: white;
        }
        
        .glossary-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 25px;
            padding: 30px;
        }
        
        .term-card {
            background-color: white;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s, box-shadow 0.3s;
            border-left: 5px solid #26d0ce;
        }
        
        .term-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 20px rgba(0, 0, 0, 0.1);
        }
        
        .term-header {
            background-color: #f8fafc;
            padding: 20px;
            border-bottom: 1px solid #e1e8f0;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        
        .term-title {
            font-size: 1.5rem;
            color: #1a2980;
            font-weight: 700;
        }
        
        .term-number {
            background-color: #1a2980;
            color: white;
            width: 36px;
            height: 36px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
        }
        
        .term-body {
            padding: 20px;
        }
        
        .term-meaning {
            color: #444;
            font-size: 1.1rem;
            line-height: 1.7;
        }
        
        .term-category {
            display: inline-block;
            margin-top: 15px;
            padding: 5px 12px;
            background-color: #e8f7f7;
            color: #1a6d6c;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: 600;
        }
        
        footer {
            text-align: center;
            padding: 25px;
            background-color: #f0f4f8;
            color: #666;
            border-top: 1px solid #e1e8f0;
            margin-top: 20px;
        }
        
        .highlight {
            background-color: #ffeb3b;
            padding: 2px;
            border-radius: 3px;
        }
        
        .no-results {
            grid-column: 1 / -1;
            text-align: center;
            padding: 40px;
            color: #666;
            font-size: 1.2rem;
        }
        
        @media (max-width: 768px) {
            .glossary-container {
                grid-template-columns: 1fr;
                padding: 20px;
            }
            
            h1 {
                font-size: 2.2rem;
            }
            
            .sort-buttons {
                flex-wrap: wrap;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1><i class="fas fa-comments"></i> Glosario de Debate</h1>
            <p class="subtitle">Términos fundamentales en español para entender y participar en debates formales. Incluye palabras clave y sus significados en contexto.</p>
        </header>
        
        <div class="controls">
            <div class="search-box">
                <input type="text" id="searchInput" placeholder="Buscar término o significado...">
                <button id="searchBtn"><i class="fas fa-search"></i></button>
            </div>
            
            <div class="sort-buttons">
                <button class="sort-btn active" data-sort="original">Orden Original</button>
                <button class="sort-btn" data-sort="alphabetical">A-Z</button>
                <button class="sort-btn" data-sort="random">Aleatorio</button>
            </div>
        </div>
        
        <div class="glossary-container" id="glossaryContainer">
            <!-- Los términos se insertarán aquí mediante JavaScript -->
        </div>
        
        <footer>
            <p>Glosario creado para estudiantes de debate y oratoria | Total de términos: <span id="termCount">15</span></p>
            <p style="margin-top: 10px; font-size: 0.9rem;">Los términos están presentados en español con su significado en contexto de debate formal.</p>
        </footer>
    </div>

    <script>
        // Datos de los términos del glosario
        const glossaryTerms = [
            {
                english: "Debate",
                spanish: "Debate",
                meaning: "Discusión formal y organizada en la que dos o más partes presentan argumentos opuestos sobre un tema específico, siguiendo reglas preestablecidas.",
                category: "Concepto Central"
            },
            {
                english: "Affirm",
                spanish: "Afirmar / Postura Afirmativa",
                meaning: "En un debate, es la parte que está a favor de la moción o proposición. Defiende la validez de la resolución planteada.",
                category: "Roles"
            },
            {
                english: "Negate",
                spanish: "Negar / Postura Negativa",
                meaning: "En un debate, es la parte que está en contra de la moción o proposición. Argumenta en contra de su validez o conveniencia.",
                category: "Roles"
            },
            {
                english: "Argument",
                spanish: "Argumento",
                meaning: "Razonamiento o conjunto de razones que se presentan para apoyar o refutar una idea, una propuesta o una postura. Es la unidad básica de persuasión en un debate.",
                category: "Elementos del Debate"
            },
            {
                english: "Reaction",
                spanish: "Réplica / Intervención",
                meaning: "En el formato de algunos debates, es el turno de cada equipo para responder directamente a los argumentos del oponente inmediatamente después de su discurso, normalmente con tiempo limitado.",
                category: "Estructura"
            },
            {
                english: "Counterargument",
                spanish: "Contraargumento",
                meaning: "Argumento específico que se presenta para rechazar o debilitar un argumento previo del oponente. No es solo una negación, sino una refutación razonada.",
                category: "Elementos del Debate"
            },
            {
                english: "Moderator",
                spanish: "Moderador/a",
                meaning: "La persona neutral que dirige el debate, hace cumplir las reglas, gestiona los turnos de palabra, presenta el tema y a los participantes, y puede formular preguntas para guiar la discusión.",
                category: "Roles"
            },
            {
                english: "Cross Examination",
                spanish: "Interrogatorio Cruzado / Contrapreguntas",
                meaning: "Fase del debate en la que un participante hace preguntas directamente a un miembro del equipo contrario. El objetivo es exponer debilidades en sus argumentos, aclarar puntos o forzar concesiones.",
                category: "Estructura"
            },
            {
                english: "Evidence",
                spanish: "Evidencia / Pruebas",
                meaning: "Hechos, datos, estadísticas, testimonios de expertos o ejemplos concretos que se utilizan para respaldar y probar la validez de un argumento. Es lo que da sustento a las afirmaciones.",
                category: "Elementos del Debate"
            },
            {
                english: "Logic",
                spanish: "Lógica",
                meaning: "La coherencia interna y la validez del razonamiento utilizado para pasar de la evidencia a una conclusión. Se refiere a la correcta estructura de los argumentos, evitando falacias (errores lógicos).",
                category: "Habilidades"
            },
            {
                english: "Relevance",
                spanish: "Pertinencia / Relevancia",
                meaning: "La cualidad de un argumento o evidencia de estar directamente relacionado con el tema de debate y con el punto que se está discutiendo. La información irrelevante, aunque sea cierta, no contribuye a la discusión.",
                category: "Criterios"
            },
            {
                english: "Decorum",
                spanish: "Decoro / Protocolo",
                meaning: "La conducta formal y respetuosa que se espera de los debatientes. Incluye el uso de un lenguaje apropiado, dirigirse al moderador y a los oponentes con cortesía, y escuchar sin interrumpir.",
                category: "Criterios"
            },
            {
                english: "Time keeping",
                spanish: "Control del Tiempo",
                meaning: "La habilidad de gestionar el tiempo asignado para cada intervención de manera eficiente. Es crucial para presentar todos los argumentos clave sin excederse, lo que puede acarrear penalizaciones.",
                category: "Habilidades"
            },
            {
                english: "Reason",
                spanish: "Razón / Razonamiento",
                meaning: "La facultad de pensar, entender y juzgar de forma lógica y fundamentada. En un debate, es el uso del intelecto para formular argumentos sólidos y analizar los del oponente, por encima de las emociones o prejuicios.",
                category: "Habilidades"
            },
            {
                english: "Self-confidence",
                spanish: "Confianza en uno mismo / Seguridad",
                meaning: "La creencia en las propias capacidades y preparación. Se manifiesta en una postura corporal firme, un tono de voz claro y convincente, y la capacidad de responder preguntas o críticas sin titubear excesivamente. Transmite credibilidad.",
                category: "Habilidades"
            }
        ];

        // Función para renderizar los términos
        function renderGlossary(terms) {
            const container = document.getElementById('glossaryContainer');
            container.innerHTML = '';
            
            if (terms.length === 0) {
                container.innerHTML = '<div class="no-results"><i class="fas fa-search" style="font-size: 3rem; margin-bottom: 15px;"></i><p>No se encontraron términos que coincidan con la búsqueda.</p></div>';
                return;
            }
            
            terms.forEach((term, index) => {
                const termCard = document.createElement('div');
                termCard.className = 'term-card';
                termCard.innerHTML = `
                    <div class="term-header">
                        <div class="term-title">${term.spanish}</div>
                        <div class="term-number">${index + 1}</div>
                    </div>
                    <div class="term-body">
                        <p class="term-meaning">${term.meaning}</p>
                        <div style="margin-top: 15px; color: #666; font-style: italic;">En inglés: <strong>${term.english}</strong></div>
                        <div class="term-category">${term.category}</div>
                    </div>
                `;
                container.appendChild(termCard);
            });
            
            // Actualizar contador
            document.getElementById('termCount').textContent = terms.length;
        }

        // Función para resaltar texto en los resultados de búsqueda
        function highlightText(text, searchTerm) {
            if (!searchTerm) return text;
            
            const regex = new RegExp(`(${searchTerm})`, 'gi');
            return text.replace(regex, '<span class="highlight">$1</span>');
        }

        // Función para buscar términos
        function searchTerms() {
            const searchTerm = document.getElementById('searchInput').value.toLowerCase().trim();
            const filteredTerms = glossaryTerms.filter(term => {
                return term.english.toLowerCase().includes(searchTerm) ||
                       term.spanish.toLowerCase().includes(searchTerm) ||
                       term.meaning.toLowerCase().includes(searchTerm) ||
                       term.category.toLowerCase().includes(searchTerm);
            });
            
            // Si hay un término de búsqueda, resaltar el texto
            if (searchTerm && filteredTerms.length > 0) {
                const highlightedTerms = filteredTerms.map(term => {
                    return {
                        ...term,
                        spanish: highlightText(term.spanish, searchTerm),
                        meaning: highlightText(term.meaning, searchTerm),
                        english: highlightText(term.english, searchTerm),
                        category: highlightText(term.category, searchTerm)
                    };
                });
                renderGlossary(highlightedTerms);
            } else {
                renderGlossary(filteredTerms);
            }
        }

        // Función para ordenar términos
        function sortTerms(sortType) {
            let sortedTerms = [...glossaryTerms];
            
            switch(sortType) {
                case 'alphabetical':
                    sortedTerms.sort((a, b) => a.spanish.localeCompare(b.spanish));
                    break;
                case 'random':
                    sortedTerms.sort(() => Math.random() - 0.5);
                    break;
                default:
                    // Orden original (como están definidos en el array)
                    break;
            }
            
            renderGlossary(sortedTerms);
            
            // Actualizar botones activos
            document.querySelectorAll('.sort-btn').forEach(btn => {
                btn.classList.remove('active');
                if (btn.dataset.sort === sortType) {
                    btn.classList.add('active');
                }
            });
        }

        // Inicializar la página
        document.addEventListener('DOMContentLoaded', () => {
            // Renderizar términos al cargar
            renderGlossary(glossaryTerms);
            
            // Configurar eventos de búsqueda
            document.getElementById('searchBtn').addEventListener('click', searchTerms);
            document.getElementById('searchInput').addEventListener('keyup', (event) => {
                if (event.key === 'Enter') {
                    searchTerms();
                }
            });
            
            // Configurar eventos de ordenación
            document.querySelectorAll('.sort-btn').forEach(btn => {
                btn.addEventListener('click', () => {
                    sortTerms(btn.dataset.sort);
                });
            });
            
            // Configurar evento para limpiar búsqueda al hacer clic en el logo
            document.querySelector('h1').addEventListener('click', () => {
                document.getElementById('searchInput').value = '';
                renderGlossary(glossaryTerms);
                document.querySelector('.sort-btn[data-sort="original"]').click();
            });
        });
    </script>
</body>
</html>
