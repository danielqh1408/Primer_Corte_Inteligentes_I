# Actividad Final del Primer Corte: Búsqueda No Informada, Informada y Adversarial

**Universidad de Caldas**  
**Facultad de Ingenierías — Departamento de Sistemas e Informática**  
**Asignatura:** Sistemas Inteligentes I  
**Docente:** Jairo I. Vélez B.  
**Fecha de Entrega:** 25 de septiembre de 2026  

---

## 👥 Integrantes del Equipo

| Nombre Completo | Correo Electrónico | Rol / Usuario GitHub |
| :--- | :--- | :--- |
| **Daniel Quintero Hurtado** | [danielqh321@gmail.com](mailto:danielqh321@gmail.com) | [@danielqh1408](https://github.com/danielqh1408) |
| **Juan David Ocampo González** | [juan.ocampo38402@ucaldas.edu.co](mailto:juan.ocampo38402@ucaldas.edu.co) | [@JuanGonzalezx](https://github.com/JuanGonzalezx) |

---

## 📌 1. Descripción Breve de la Actividad

Esta actividad corresponde a la evaluación práctica y conceptual del **Primer Corte** de la asignatura **Sistemas Inteligentes I**. Su propósito central es diseñar, implementar, experimentar y comparar de manera rigurosa los cuatro paradigmas clásicos de búsqueda en Inteligencia Artificial:

1. **Búsqueda No Informada (BFS y DFS):** Modelado formal de espacios de estados acíclicos y no ponderados, resolución de laberintos en matrices $5 \times 5$ y $10 \times 10$, análisis de sensibilidad al orden de operadores en DFS, formulación algebraica del problema de los recipientes de agua (Teorema/Identidad de Bézout) y BFS en el 8-puzzle con estudio de la explosión combinatoria.
2. **Búsqueda Informada (UCS, A* y Beam Search):** Estudio de admisibilidad ($h \le h^*$) y consistencia heurística en grafos ponderados, navegación óptima en mapas $12 \times 12$ con obstáculos, análisis de dominancia ($h_{\text{Manhattan}} \ge h_{\text{Euclidiana}}$) y resolución eficiente del 8-puzzle mediante A* contrastando heurísticas de piezas fuera de lugar ($h_1$) y distancia Manhattan ($h_2$).
3. **Búsqueda Adversarial (Minimax):** Toma de decisiones secuencial y óptima en juegos deterministas de suma cero con dos jugadores racionales, resolución por inducción hacia atrás (backward induction), análisis matemático del juego de sustracción de piedras con movimientos clásicos y modificados $\{1, 2, 4\}$ bajo aritmética modular ($\pmod 3$), e implementación completa del motor de Tres en Raya (Tic-Tac-Toe).
4. **Búsqueda Adversarial con Poda Alfa–Beta:** Optimización exhaustiva del árbol Minimax mediante la conservación de límites $[\alpha, \beta]$, análisis del impacto crítico del ordenamiento de jugadas (*Move Ordering*), benchmark cuantitativo del porcentaje de nodos y hojas podados frente a Minimax puro, y simulación de partidas autónomas de juego perfecto (*Perfect Play*).

---

## 📂 2. Estructura del Repositorio

El repositorio presenta una organización limpia y modular, sin archivos temporales ni binarios residuales:

```text
Primer_Corte_Inteligentes_I/
├── .gitignore                                           # Exclusiones de venv, cache y checkpoints
├── README.md                                            # Documento maestro y memoria técnica
├── requirements.txt                                     # Especificación de dependencias reproducibles
├── Resolucion_Problemas_Busqueda_NoInformada.ipynb      # Notebook 1: BFS y DFS
├── Resolucion_Problemas_Busqueda_Informada.ipynb        # Notebook 2: UCS, A* y Beam Search
├── Minimax.ipynb                                        # Notebook 3: Búsqueda Adversarial Minimax
└── Poda_Alfa_Beta.ipynb                                 # Notebook 4: Poda Alfa-Beta y Benchmarks
```

---

## 📓 3. Relación Detallada de los Notebooks Incluidos

Todos los notebooks han sido desarrollados, documentados y **completamente ejecutados sin errores**, conteniendo sus salidas tabulares, numéricas y gráficos generados con `matplotlib`:

| # | Archivo de Notebook | Temática y Algoritmos | Problemas Abordados y Experimentos |
| :-: | :--- | :--- | :--- |
| **1** | [`Resolucion_Problemas_Busqueda_NoInformada.ipynb`](./Resolucion_Problemas_Busqueda_NoInformada.ipynb) | BFS, DFS, Modelado de Grafos | Laberintos $5 \times 5$ y $10 \times 10$, visualizaciones con mapas de calor y trayectorias, análisis del orden LIFO de operadores, recipientes con Identidad de Bézout, BFS 8-puzzle y análisis de paridad de inversiones. |
| **2** | [`Resolucion_Problemas_Busqueda_Informada.ipynb`](./Resolucion_Problemas_Busqueda_Informada.ipynb) | UCS, A*, Beam Search ($k=1,2,4,8$) | Grafo ponderado con heurística admisible vs. sobreestimada, navegación en cuadrícula $12 \times 12$, dominancia Manhattan vs. Euclidiana, A* 8-puzzle ($h_1$ vs. $h_2$) y comparación de costo vs. tiempo de cómputo. |
| **3** | [`Minimax.ipynb`](./Minimax.ipynb) | Minimax, Inducción hacia atrás | Árboles multinivel paso a paso, juego de las piedras $\{1, 2, 3\}$ ($\pmod 4$), variante modificada $\{1, 2, 4\}$ ($\pmod 3$), motor completo para Tres en Raya y evaluación de tableros. |
| **4** | [`Poda_Alfa_Beta.ipynb`](./Poda_Alfa_Beta.ipynb) | Poda Alfa–Beta ($\alpha \ge \beta$), Move Ordering | Cuantificación de podas en árboles sintéticos, impacto del orden favorable vs. desfavorable, benchmark en Tres en Raya (reducción $> 70\%$ de visitas) y simulación de juego perfecto autónomo. |

---

## 🧠 4. Síntesis de Respuestas Conceptuales y Justificaciones Teóricas

A continuación se resumen las respuestas a las preguntas de análisis planteadas en los talleres de clase:

### 4.1 Búsqueda No Informada (BFS y DFS)
* **Garantía de Camino Mínimo en BFS:** Dado que las aristas tienen costo unitario ($c = 1$), la exploración por niveles concéntricos de profundidad garantiza que el primer encuentro con el objetivo corresponde a la ruta con el menor número de transiciones posibles.
* **Comportamiento de DFS vs. Orden de Operadores:** Al apoyarse en una pila LIFO, DFS prioriza ciegamente el último sucesor insertado; si se permuta el orden de movimientos (ej. arriba, abajo, izquierda, derecha), el árbol de expansión cambia drásticamente, modificando tanto el número de estados visitados como la subóptima del camino hallado.
* **Solubilidad de Recipientes de Agua (Identidad de Bézout):** Un volumen objetivo $D \le \max(M, N)$ es alcanzable a través de operaciones elementales si y solo si $D$ es múltiplo entero del máximo común divisor: $D = k \cdot \gcd(M, N)$. Si $D \pmod{\gcd(M,N)} \ne 0$, el problema carece de solución.
* **Explosión Combinatoria en el 8-Puzzle:** Con un factor de ramificación efectivo $b \approx 2.67$, a profundidad $d = 20$ la frontera de BFS exigiría almacenar $2.67^{20} \approx 2.8 \times 10^8$ estados en memoria RAM ($O(b^d)$), provocando el colapso del proceso y evidenciando la necesidad de heurísticas.

### 4.2 Búsqueda Informada (UCS, A* y Beam Search)
* **Admisibilidad vs. Dominancia Heurística:** Una heurística mayor no siempre es mejor si sobreestima el costo real ($h(n) > h^*(n)$), ya que pierde admisibilidad y sacrifica la optimalidad. Sin embargo, entre dos heurísticas admisibles, si $h_2(n) \ge h_1(n) \;\forall n$, se dice que $h_2$ domina a $h_1$ y está garantizado que expandirá menor o igual cantidad de nodos.
* **$g(n)$ frente a $h(n)$:** $g(n)$ mide el costo real incurrido desde la raíz hasta el nodo actual (conocimiento exacto del pasado), mientras que $h(n)$ es una estimación optimista del costo restante hacia la meta (proyección hacia el futuro). UCS opera con $h(n) = 0$.
* **Trade-off en Beam Search:** Al restringir la frontera a los $k$ mejores estados según $f(n)$, Beam Search ahorra drásticamente memoria y tiempo ($O(k \cdot b)$), pero renuncia a la completitud y a la optimalidad al podar ramas que potencialmente contenían la solución óptima.

### 4.3 Minimax y Búsqueda Adversarial
* **Racionalidad y Suposición del Adversario:** Minimax asume que el contrincante juega de manera óptima según sus propios intereses (minimizar la ganancia de MAX en juegos de suma cero). Si el oponente comete un error y juega de forma no óptima, MAX obtiene un resultado estrictamente mejor o igual al garantizado teóricamente.
* **Juego de las Piedras y Aritmética Modular:** En la variante con sustracción $\{1, 2, 4\}$, las posiciones perdedoras corresponden a los múltiplos de 3 ($n \equiv 0 \pmod 3$), puesto que cualquier jugada legal deja un residuo no divisible entre 3, permitiendo al rival forzar un nuevo múltiplo de 3 hasta ganar.
* **Miopía en Decisiones Inmediatas:** Una jugada tentadora a corto plazo (como capturar una ficha) puede dejar desprotegido un flanco crítico que el adversario explotará en su turno, demostrando por qué la búsqueda adversarial requiere evaluación recursiva de horizontes.

### 4.4 Poda Alfa–Beta
* **Naturaleza de la Poda ($\alpha \ge \beta$):** Una poda no indica que una rama sea «mala»; indica que es matemáticamente irrelevante para la decisión en la raíz, pues un jugador en un nivel superior ya cuenta con una alternativa que le garantiza un mejor desenlace.
* **Impacto del Move Ordering:** En el mejor caso (jugadas evaluadas de mejor a peor), Alfa–Beta reduce la complejidad temporal de $O(b^m)$ a $O(b^{m/2})$, duplicando la profundidad de búsqueda efectiva.
* **Juego Perfecto en Tres en Raya:** La simulación Minimax y Alfa-Beta contra sí mismos demuestra que, bajo juego racional perfecto, el resultado matemático inevitable es siempre un empate ($0$).

---

## 💻 5. Instrucciones de Instalación y Ejecución

El proyecto está preparado para reproducirse de forma idéntica en entornos locales macOS / Linux / Windows, así como en Google Colab.

### 5.1 Requisitos del Sistema
- Python 3.10, 3.11 o 3.12.
- Administrador de paquetes `pip`.

### 5.2 Configuración del Entorno Virtual (Local)

1. **Clonar el repositorio:**
   ```bash
   git clone git@github.com:danielqh1408/Primer_Corte_Inteligentes_I.git
   cd Primer_Corte_Inteligentes_I
   ```

2. **Crear y activar un entorno virtual:**
   - En macOS / Linux:
     ```bash
     python3 -m venv .venv
     source .venv/bin/activate
     ```
   - En Windows (PowerShell):
     ```powershell
     python -m venv .venv
     .venv\Scripts\Activate.ps1
     ```

3. **Instalar dependencias requeridas:**
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```

4. **Registrar el Kernel de Jupyter (opcional, para VS Code / JupyterLab):**
   ```bash
   python -m ipykernel install --user --name inteligentes1 --display-name "Python 3.12 (Inteligentes I)"
   ```

5. **Lanzar el servidor de Jupyter:**
   ```bash
   jupyter notebook
   # o bien:
   jupyter lab
   ```

6. **Ejecutar los Notebooks:**  
   Abra cualquiera de los archivos `.ipynb` y seleccione `Kernel -> Restart & Run All`. Todas las celdas se ejecutarán de principio a fin de manera secuencial y autocontenida.

### 5.3 Enlaces de Acceso y Respaldo en Google Drive / Colab
Para facilitar la revisión docente en la nube, se encuentran disponibles réplicas ejecutadas en Google Colab:
- **Carpeta de Google Drive:** [Actividad Final Primer Corte - Sistemas Inteligentes I](https://drive.google.com/drive/folders/1fOY8K28k76Sypq8T5AGfLFSq4bDDC2k4?utm_source=gemini)
- **Notebook 1 (Colab):** [Resolucion_Problemas_Busqueda_NoInformada.ipynb](https://colab.research.google.com/drive/1nRpNauDGNitdX72hcpQp3-5c_fLh4fjx)
- **Notebook 2 (Colab):** [Resolucion_Problemas_Busqueda_Informada.ipynb](https://colab.research.google.com/drive/1-Nz3OYnbpy8ufJs1cnQGD87-1oM9aNQC)
- **Notebook 3 (Colab):** [Minimax.ipynb](https://colab.research.google.com/drive/18IFSa-dNlEE7VQso2JsHdb7DxVVUuFMG)
- **Notebook 4 (Colab):** [Poda_Alfa_Beta.ipynb](https://colab.research.google.com/drive/1wzrK64a4mt2hKdnAfhfBV6FUZm3EGUW8)

---

## 🌿 6. Uso de Git y Flujo de Trabajo Colaborativo

El repositorio evidencia un desarrollo progresivo y estructurado mediante control de versiones con Git, cumpliendo los criterios de la rúbrica:
- **Estructura clara y limpia:** Sin binarios innecesarios, carpetas de caché `__pycache__` o `.DS_Store`.
- **Commits significativos y progresivos:** El repositorio cuenta con más de 10 commits descriptivos realizados a lo largo de las distintas etapas de desarrollo.
- **Estandarización de mensajes:** Adopción de la convención *Conventional Commits* (`feat:`, `docs:`, `chore:`, `fix:`).
- **Colaboración en equipo:** Participación y aportes conjuntos de Daniel Quintero Hurtado y Juan David Ocampo González.

---

## 🤖 7. Declaración de Uso de IA Generativa

En cumplimiento explícito de los lineamientos éticos de la asignatura y la rúbrica de evaluación:

* **Herramientas utilizadas:** Google Gemini Spark y Antigravity IDE (Gemini 3.8 Flash).
* **Propósito de uso:**
  1. Asistencia en el diseño de scripts modulares para renderizado y visualización gráfica con `matplotlib`.
  2. Apoyo en la formulación y validación cruzada de benchmarks empíricos (conteo de nodos visitados y podados en árboles de juego).
  3. Estructuración técnica y redacción académica de las explicaciones matemáticas y teóricas en formato Markdown.
* **Partes de la actividad en las que fue empleada:**
  - Automatización de comparativas numéricas y tabulación de resultados experimentales en los cuatro notebooks.
  - Formato formal del archivo `README.md` y organización del historial de commits.
* **Compromiso ético y autoría:** Todo el código fuente implementado, las funciones algorítmicas (`bfs`, `dfs`, `ucs`, `a*`, `beam_search`, `minimax`, `alfa_beta`) y las justificaciones teóricas fueron inspeccionadas, depuradas, ejecutadas y asimiladas íntegramente por los integrantes del equipo para su sustanciación académica.
