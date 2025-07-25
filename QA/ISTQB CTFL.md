# 🧪 ISTQB CTFL – Capítulo 1: Fundamentos del Testing

---

## 📌 1.1 ¿Qué es el testing?

### ✅ Definición:
**Testing** es el proceso que consiste en analizar un sistema o componente para:
- Encontrar **defectos (bugs)**
- Evaluar la **calidad del software**
- Asegurar que cumple con los **requisitos funcionales y no funcionales**

### 📍 Propósitos del testing:
- **Detectar defectos** antes de que llegue al usuario
- **Dar confianza** en la calidad del software
- **Reducir riesgos** de fallo en producción
- **Cumplir con requisitos contractuales, legales o regulatorios**

---

## 📌 1.2 Por qué es necesario el testing

### 🎯 Razones clave:
- El software puede tener **defectos ocultos**
- Los defectos pueden causar **fallos severos** (ej: pérdidas económicas, accidentes)
- El desarrollo humano es **propenso a errores**
- **Testing reduce riesgos**, pero **no puede garantizar software libre de defectos**

### 📌 Ejemplo frecuente en exámenes:
> **P: ¿Cuál de los siguientes enunciados es correcto sobre el testing?**  
> **R correcta:** El testing ayuda a reducir la probabilidad de defectos, pero no los elimina completamente.

---

## 📌 1.3 Principios generales del testing

Los **7 principios del testing** son claves. Aparecen mucho en el examen.

### 1. El testing muestra la presencia de defectos
- El objetivo es encontrar defectos, **no demostrar que el software funciona perfectamente.**

### 2. El testing exhaustivo es imposible
- No se puede probar **todo**, se deben usar **técnicas de muestreo inteligente**.

### 3. Las pruebas tempranas ahorran tiempo y dinero
- Iniciar pruebas **desde las etapas iniciales** (ej: revisión de requisitos) reduce costos de corrección.

### 4. Agrupación de defectos
- Los defectos tienden a **concentrarse en ciertas áreas del software.**

### 5. La paradoja del pesticida
- Repetir siempre las mismas pruebas **no encuentra nuevos defectos.** Se deben **actualizar** regularmente.

### 6. El testing depende del contexto
- Pruebas diferentes para distintos tipos de software (ej: banco vs. videojuego)

### 7. La ausencia de errores no implica software útil
- Que el software esté libre de errores **no significa que sea lo que el cliente necesita.**

### 📌 Ejemplo frecuente en exámenes:
> **P: ¿Qué principio del testing implica que no se pueden probar todas las combinaciones posibles?**  
> **R correcta:** El testing exhaustivo es imposible.

---

## 📌 1.4 El proceso de testing

### Fases del proceso:
1. **Planificación y control**
   - Establecer objetivos, estrategia y seguimiento
2. **Análisis y diseño**
   - Revisar requisitos y diseñar casos de prueba
3. **Implementación y ejecución**
   - Construir casos de prueba, preparar datos, ejecutarlos
4. **Evaluación de criterios de salida y reporte**
   - Evaluar si se cumplió el objetivo, emitir informes
5. **Cierre de las pruebas**
   - Finalizar, archivar, evaluar lecciones aprendidas

### 📌 Notas importantes:
- Se debe usar el proceso de testing de forma **adaptativa**, según el contexto y metodología (ágil, tradicional…).

---

## 📌 1.5 La mentalidad del tester

### Características de un buen tester:
- **Pensamiento crítico y analítico**
- Capacidad para **ver lo que puede fallar**
- **Colaboración constructiva** con el equipo
- En entornos ágiles, se espera que todos participen en testing (no solo el “tester oficial”)

### 📌 Tip de examen:
Aparece la diferencia entre la **mentalidad de desarrollo (confirmación)** y la **mentalidad de testing (cuestionamiento/crítica constructiva).**

---

## 📋 RESUMEN RÁPIDO – Capítulo 1

| Concepto | Clave para recordar |
|----------|----------------------|
| Testing | Detecta defectos y evalúa calidad |
| Exhaustividad | Imposible testear todo |
| Pruebas tempranas | Más baratas y efectivas |
| Pesticida | Cambiar las pruebas regularmente |
| Ausencia de errores ≠ Éxito | Debe cumplir requisitos |
| Mentalidad del tester | Crítica, colaborativa, analítica |

---

## 📌 Temas de este capítulo que más aparecen en preguntas de examen:

| Tema | Frecuencia |
|------|------------|
| Principios del testing | Muy alta |
| Objetivos del testing | Alta |
| Mentalidad del tester | Media |
| Proceso de testing | Media |

---

# 🧪 ISTQB CTFL – Capítulo 2: Pruebas durante el ciclo de vida del software

---

## 📌 2.1 Modelos de desarrollo de software

### 📚 Modelos tradicionales (secuenciales):

#### ✅ Modelo en cascada (Waterfall)
- Etapas secuenciales: requisitos → diseño → implementación → pruebas → mantenimiento.
- Las pruebas se ejecutan **después del desarrollo**.
- Ideal cuando los requisitos son **claros y estables**.

#### ✅ Modelo V
- Relación directa entre fases de desarrollo y tipos de prueba.
- Incluye **pruebas desde el principio** (pruebas se diseñan con los requisitos).
- Ventaja: permite **verificación y validación más estructuradas**.

### 📚 Modelos iterativos e incrementales (Ágiles):

#### ✅ Modelos incrementales
- Se construye el producto en **módulos funcionales (incrementos)**.
- Las pruebas se aplican a cada incremento.

#### ✅ Modelos ágiles (Scrum, Kanban, XP)
- Ciclos cortos (sprints).
- **Testing continuo**: pruebas automatizadas, unitarias, revisión colaborativa.
- **Todos participan del testing**, incluyendo desarrolladores, testers y clientes.

---

## 📌 2.2 Niveles de prueba

Los niveles de prueba se **organizan jerárquicamente**. Cada uno tiene **objetivos específicos**:

### 1. Pruebas de componente (unitarias)
- Prueban componentes individuales (funciones, métodos, clases).
- Son rápidas y automatizables.
- **Responsabilidad del desarrollador.**

### 2. Pruebas de integración
- Prueban interacciones entre componentes (interfaces).
- Pueden ser:
  - **Top-down**: módulos superiores primero.
  - **Bottom-up**: módulos inferiores primero.
  - **Big bang**: todos a la vez (riesgoso).
- Herramientas: stubs y drivers.

### 3. Pruebas de sistema
- Prueban el sistema completo, como si fuera en producción.
- Validan funcionalidad, rendimiento, usabilidad, etc.
- **Responsabilidad del equipo de testing.**

### 4. Pruebas de aceptación
- Verifican si el sistema cumple los **requisitos del negocio.**
- Normalmente realizadas por el **cliente o usuario final.**

#### Tipos:
- **UAT (User Acceptance Testing)**: pruebas reales por usuarios.
- **Pruebas alfa/beta**: alfa = entorno del proveedor, beta = entorno real del cliente.

### 📌 Ejemplo frecuente en el examen:
> **P: ¿Cuál es el objetivo de las pruebas de integración?**  
> **R correcta:** Verificar la interacción entre componentes o sistemas.

---

## 📌 2.3 Tipos de prueba

### ✅ 1. Pruebas funcionales
- Verifican **qué hace el sistema**.
- Basadas en requisitos funcionales (ej: reglas de negocio).
- Incluyen pruebas de:
  - Interfaces de usuario
  - APIs
  - Bases de datos

### ✅ 2. Pruebas no funcionales
- Verifican **cómo se comporta el sistema**.
- Ejemplos: rendimiento, usabilidad, seguridad, compatibilidad, escalabilidad.

### ✅ 3. Pruebas estructurales (white-box)
- Prueban la **estructura interna del código**.
- Analizan decisiones lógicas, cobertura de sentencias, condiciones, etc.

### ✅ 4. Pruebas de cambio
- Verifican efectos de cambios o correcciones:
  - **Re-testing (re-prueba):** volver a probar lo mismo luego de arreglar algo.
  - **Testing de regresión:** verificar que el cambio no haya afectado otras áreas.

---

## 📌 2.4 Pruebas de mantenimiento

### Ocurren luego de la liberación del software. Incluyen:
- **Correcciones (defectos)**
- **Mejoras y actualizaciones**
- **Migraciones o adaptaciones**

### Desafíos:
- Poca documentación
- Personal diferente al original
- Mayor necesidad de regresión

---

## 📋 RESUMEN RÁPIDO – Capítulo 2

| Concepto | Clave para recordar |
|----------|----------------------|
| V-Model | Relación directa entre etapas de desarrollo y tipos de prueba |
| Niveles de prueba | Componente → Integración → Sistema → Aceptación |
| Tipos de prueba | Funcional, No funcional, Estructural, Cambio |
| Re-testing | Probar lo que fue corregido |
| Regresión | Probar que nada más se rompió |
| Ágil | Pruebas continuas, automatización, colaboración |

---

## 📌 Temas de este capítulo que más aparecen en preguntas de examen:

| Tema | Frecuencia |
|------|------------|
| Niveles de prueba | Muy alta |
| Tipos de prueba | Alta |
| Re-testing vs. regresión | Alta |
| Modelos de desarrollo | Media |

---

# 🧪 ISTQB CTFL – Capítulo 3: Pruebas Estáticas

---

## 📌 3.1 Técnicas estáticas y su propósito

### ✅ ¿Qué son las pruebas estáticas?
- Son actividades de testing que **no requieren ejecutar el código**.
- Se aplican sobre **documentos**: requisitos, código fuente, casos de prueba, diagramas, etc.

### ✅ Propósitos clave:
- **Detectar defectos tempranamente**, antes de ejecutar el sistema.
- Reducir costos (más barato corregir en fases tempranas).
- Identificar **inconsistencias, omisiones o ambigüedades** en requisitos y diseño.
- Mejorar la calidad del software **desde etapas tempranas**.

### Dos tipos principales:
1. **Revisiones (manuales)** → análisis humano de artefactos.
2. **Análisis estático (automático)** → herramientas que analizan código sin ejecutarlo.

---

## 📌 3.2 Proceso de revisión

Las **revisiones** son un tipo de prueba estática basada en inspección de documentos o código. Son actividades **manuales y sistemáticas**.

### Tipos de revisiones (de menor a mayor formalidad):

| Tipo de revisión | Características |
|------------------|------------------|
| **Informal**     | No estructurada. Lectura rápida entre colegas. |
| **Walkthrough**  | Revisión dirigida por el autor, con participación de pares. |
| **Revisión técnica** | Más formal, liderada por un moderador técnico. Detecta defectos técnicos. |
| **Inspección**   | La más formal. Roles definidos, checklist, métricas, reportes. Altamente efectiva. |

### ✅ Roles típicos en revisiones formales:
- **Autor**: crea el documento.
- **Moderador**: lidera y organiza la revisión.
- **Revisor**: analiza el artefacto.
- **Lector**: lee en voz alta el documento durante la reunión.
- **Scribe (anotador)**: registra defectos encontrados.

### 📌 Ejemplo frecuente en examen:
> **P: ¿Cuál es el rol del moderador en una inspección formal?**  
> **R correcta:** Liderar la revisión, coordinar participantes y controlar el proceso.

---

## 📌 3.3 Análisis estático mediante herramientas

### ✅ ¿Qué hacen estas herramientas?
- Analizan **el código fuente o los modelos** sin ejecutarlos.
- Detectan defectos como:
  - Violaciones de estándares de codificación
  - Variables no utilizadas
  - Problemas de complejidad
  - Posibles errores de flujo de control
  - Vulnerabilidades de seguridad

### ✅ Beneficios:
- Ahorra tiempo y esfuerzo (detección automática).
- Fomenta buenas prácticas de codificación.
- Ayuda a encontrar errores que podrían pasar desapercibidos con pruebas dinámicas.

### Ejemplos de herramientas:
- **Linters**: verifican estilo de código (ej. ESLint).
- **Análisis de flujo de datos**: verifica uso de variables.
- **Detección de dependencias cíclicas**.
- **Análisis de complejidad ciclomática.**

---

## 📋 RESUMEN RÁPIDO – Capítulo 3

| Concepto | Clave para recordar |
|----------|----------------------|
| Pruebas estáticas | No se ejecuta el software |
| Revisiones | Análisis manual de documentos |
| Análisis estático | Automatizado, sobre código |
| Inspección | Revisión formal con roles |
| Herramientas estáticas | Buscan defectos sin ejecutar el código |

---

## 📌 Temas más frecuentes en preguntas de examen:

| Tema | Frecuencia |
|------|------------|
| Tipos de revisión y sus roles | Muy alta |
| Diferencia entre revisión y análisis estático | Alta |
| Ventajas del testing estático | Alta |
| Herramientas de análisis estático | Media |

---

# 🧪 ISTQB CTFL – Capítulo 4: Técnicas de diseño de pruebas

---

## 📌 4.1 Categorías de técnicas de diseño

Las técnicas de diseño de pruebas permiten **crear casos de prueba efectivos y eficientes**. Se dividen en tres grandes categorías:

| Categoría | Características |
|----------|------------------|
| ✅ **Basadas en especificación (caja negra)** | Se basan en los requisitos. No se ve el código. |
| ✅ **Basadas en estructura (caja blanca)** | Se basan en la lógica del código o estructura interna. |
| ✅ **Basadas en experiencia** | Se basan en el conocimiento del tester, sin seguir reglas formales. |

---

## 📌 4.2 Técnicas basadas en la especificación (caja negra)

Estas técnicas analizan **qué debe hacer el sistema**, sin conocer su implementación interna.

### ✅ 1. **Partición de equivalencia**
- Divide los valores posibles de entrada en **clases válidas e inválidas**.
- Se **elige un valor representativo** de cada clase.
- Reduce el número de pruebas manteniendo buena cobertura.

📌 **Ejemplo:**
Campo de edad válido: 18–65  
- Clases válidas: 18–65  
- Clases inválidas: <18, >65  
→ Se prueba 1 valor de cada clase: 25 (válido), 10 (inválido), 70 (inválido)

---

### ✅ 2. **Análisis de valores límite (Boundary Value Analysis)**
- Los errores suelen ocurrir en los **límites** de las clases válidas.
- Se prueban los valores en y cerca del límite.

📌 **Ejemplo:**
Edad válida: 18–65  
→ Probar: 17, 18, 65, 66

---

### ✅ 3. **Tabla de decisión**
- Útil para modelar reglas de negocio complejas.
- Cada fila es una condición o acción; cada columna, una combinación específica.

📌 **Ejemplo:**
Condición 1: es cliente frecuente  
Condición 2: tiene descuento  
→ Acción: aplica descuento del 20%

---

### ✅ 4. **Transición de estado**
- Modela el sistema como una **máquina de estados**.
- Se prueban transiciones válidas e inválidas.

📌 **Ejemplo:**
Sistema de login:  
- Estado: No autenticado → autenticado  
- Evento: ingresar credenciales válidas  
→ Verificar que el cambio de estado ocurra correctamente

---

### ✅ 5. **Caso de uso**
- Pruebas basadas en **escenarios reales de uso por parte del usuario**.
- Útil para pruebas de aceptación.

---

## 📌 4.3 Técnicas basadas en estructura (caja blanca)

Analizan la **estructura interna del software**: flujo lógico, condiciones, bucles, etc.

### ✅ 1. **Cobertura de sentencias**
- Asegura que **cada línea de código** se ejecute al menos una vez.

### ✅ 2. **Cobertura de decisiones**
- Verifica que cada **decisión booleana** sea evaluada como verdadera y falsa al menos una vez.

📌 **Ejemplo:**
```js
if (x > 5) {
   // sentencia
}
```
→ Se debe probar con `x = 6` (true) y `x = 3` (false)

---

## 📌 4.4 Técnicas basadas en experiencia

Son técnicas **informales**, utilizadas cuando:
- No hay documentación
- El tiempo es limitado
- Se depende del conocimiento del tester

### ✅ 1. **Pruebas exploratorias**
- El tester **diseña y ejecuta pruebas al mismo tiempo**.
- Utiliza habilidades, intuición y experiencia.
- Puede usar “charters” o sesiones exploratorias.

### ✅ 2. **Adivinación de errores (Error guessing)**
- El tester **intencionalmente intenta provocar errores comunes**.
- Se basa en conocimiento de errores típicos del sistema, tecnología o tipo de entrada.

---

## 📋 RESUMEN RÁPIDO – Capítulo 4

| Técnica | Tipo | Punto clave |
|--------|------|-------------|
| Partición de equivalencia | Caja negra | Dividir entradas en clases válidas/ inválidas |
| Valores límite | Caja negra | Probar justo en el borde de lo permitido |
| Tabla de decisión | Caja negra | Lógica compleja con condiciones múltiples |
| Transición de estado | Caja negra | Pruebas basadas en eventos y estados |
| Caso de uso | Caja negra | Escenarios completos de uso |
| Cobertura de sentencias | Caja blanca | Ejecutar todas las líneas |
| Cobertura de decisiones | Caja blanca | Verificar condiciones en ambas direcciones |
| Exploratorias | Experiencia | Diseñar/ejecutar al vuelo |
| Adivinación de errores | Experiencia | Buscar errores típicos conocidos |

---

## 📌 Temas más frecuentes en el examen:

| Tema | Frecuencia |
|------|------------|
| Partición de equivalencia | Muy alta |
| Valores límite | Muy alta |
| Cobertura de decisiones/sentencias | Alta |
| Diferencias entre técnicas | Alta |
| Pruebas exploratorias | Media |

---

# 🧪 ISTQB CTFL – Capítulo 5: Gestión de pruebas

---

## 📌 5.1 Organización del testing

### ✅ Función del testing dentro del proyecto:
- Puede ser realizado por:
  - **Desarrolladores** (pruebas unitarias, revisiones)
  - **Testers independientes** (QA, usuarios, equipos externos)

### ✅ Ventajas de testers independientes:
- Aportan **objetividad**
- Pueden encontrar defectos que el desarrollador **no ve por familiaridad**

### ✅ Riesgos:
- Puede haber **falta de comunicación** entre desarrollo y testing
- Testing visto como “enemigo del progreso”

---

## 📌 5.2 Planificación y control de las pruebas

### ✅ ¿Qué es la planificación de pruebas?
- Define **qué se va a probar**, **cómo**, **cuándo**, **por quién** y **con qué recursos**.

### Contenido de un plan de pruebas (según el estándar IEEE 829 / ISO/IEC/IEEE 29119):
- Alcance y objetivos
- Elementos a probar (y no probar)
- Criterios de entrada y salida
- Enfoque y técnicas
- Estimación de esfuerzo
- Recursos (personas, ambientes)
- Cronograma
- Riesgos y mitigación

### ✅ ¿Qué es el control de pruebas?
- **Monitorear** el progreso
- **Comparar lo planeado vs. real**
- **Tomar acciones correctivas**

---

## 📌 5.3 Estimación de esfuerzo de pruebas

### ✅ Métodos comunes:
- **Basado en métricas históricas**: usar datos previos de proyectos similares.
- **Basado en expertos**: juicio de quienes ya han probado sistemas similares.
- **Basado en requisitos/puntos de prueba**: cantidad de casos, complejidad.

### 📌 Ejemplo en preguntas:
> **P: ¿Cuál es una técnica común de estimación basada en experiencia previa?**  
> **R correcta:** Estimación basada en expertos

---

## 📌 5.4 Seguimiento y control del testing

### ✅ Qué se debe monitorear:
- Progreso vs. plan
- Número de casos de prueba ejecutados / fallidos / exitosos
- Número de defectos encontrados, severidad, tiempo de resolución

### ✅ Métricas típicas:
| Métrica | Qué indica |
|--------|------------|
| % de cobertura | Qué tanto del código o requisitos ha sido probado |
| Tasa de fallos | Defectos por unidad de tiempo o funcionalidad |
| Tiempo medio para reparar | Eficiencia del proceso de corrección |

---

## 📌 5.5 Gestión de la configuración

### ✅ ¿Qué es?
- Controla **versiones** de los artefactos de prueba y desarrollo:
  - Casos de prueba
  - Código fuente
  - Datos de prueba
  - Documentos

### ✅ Objetivo:
- Asegurar que todos trabajen con las **versiones correctas y consistentes**.
- Registrar los cambios y quién los hizo.

📌 Herramientas comunes: Git, SVN, sistemas de gestión documental.

---

## 📌 5.6 Gestión de riesgos y testing

### ✅ ¿Qué es el riesgo?
- **Evento posible no deseado** que puede tener impacto negativo.

### Tipos:
- **Riesgo de producto**: errores en el software (ej: pérdida de datos).
- **Riesgo de proyecto**: errores en la planificación (ej: falta de recursos).

### ✅ ¿Qué es el testing basado en riesgos (RBT)? 
- **Prioriza las pruebas** en base al nivel de riesgo.
- Riesgo = **probabilidad × impacto**

📌 Ejemplo:
> Si un fallo en la pasarela de pagos es crítico y probable → **se prueba primero y más intensamente**.

---

## 📌 5.7 Manejo de incidentes

### ✅ ¿Qué es un incidente?
- Cualquier **evento inesperado** durante el testing que podría indicar un defecto:
  - Resultado inesperado
  - Error en la documentación
  - Comportamiento extraño del sistema

### ✅ Proceso de gestión:
1. Identificación y registro del incidente
2. Clasificación y priorización
3. Investigación y diagnóstico
4. Resolución
5. Verificación de corrección
6. Cierre del incidente

---

## 📋 RESUMEN RÁPIDO – Capítulo 5

| Concepto | Clave para recordar |
|----------|----------------------|
| Tester independiente | Mayor objetividad |
| Plan de pruebas | Qué, cómo, cuándo, quién y con qué se prueba |
| Control de pruebas | Comparar plan con ejecución real |
| Estimación basada en expertos | Técnica más usada |
| Configuración | Control de versiones |
| Riesgos | Producto y proyecto |
| Testing basado en riesgos | Pruebo más lo que tiene mayor probabilidad e impacto |
| Incidente | Evento inesperado → posible defecto |

---

## 📌 Temas más frecuentes en el examen:

| Tema | Frecuencia |
|------|------------|
| Planificación vs. control | Alta |
| Estimación de pruebas | Media |
| Riesgos y RBT | Alta |
| Gestión de incidentes | Alta |

---

# 🧪 ISTQB CTFL – Capítulo 6: Herramientas de soporte para las pruebas

---

## 📌 6.1 Tipos de herramientas de testing

Las herramientas de testing **automatizan o apoyan actividades** en el proceso de pruebas. Pueden reducir esfuerzo manual, mejorar calidad y aumentar cobertura.

### ✅ Categorías de herramientas:

| Categoría | Funcionalidad |
|----------|---------------|
| **Gestión de pruebas** | Planificación, ejecución, trazabilidad, reportes |
| **Gestión de defectos/incidentes** | Registro, seguimiento y análisis de errores |
| **Diseño de casos de prueba** | Generación automática de casos |
| **Comparación de resultados** | Detectan diferencias entre resultados esperados y obtenidos |
| **Simulación y stub/mocks** | Simulan interfaces de componentes no disponibles aún |
| **Testing unitario** | Automatiza pruebas de componentes individuales |
| **Testing de regresión** | Re-ejecuta pruebas automáticamente tras cambios |
| **Análisis estático** | Revisa código sin ejecutarlo (ver Capítulo 3) |
| **Cobertura del código** | Mide cuánto del código fue ejecutado en las pruebas |
| **Performance** | Mide tiempo de respuesta, carga, uso de recursos |
| **Captura/reproducción** | Graba y ejecuta flujos de usuario |

📌 Ejemplos reales:
- JIRA, TestRail, Selenium, JUnit, Postman, SonarQube, JMeter

---

## 📌 6.2 Beneficios y riesgos del uso de herramientas

### ✅ Beneficios:
- **Reducción del esfuerzo manual repetitivo**
- **Mayor precisión** (menos errores humanos)
- **Mejor trazabilidad** de defectos y pruebas
- Facilitan la **automatización**
- **Aumentan la cobertura**

### ⚠️ Riesgos:
- Expectativas poco realistas (ej: automatizarlo todo desde el principio)
- Costos de mantenimiento (scripts, herramientas)
- Inversión en capacitación
- Falsos positivos o negativos
- Dependencia excesiva de la herramienta

📌 Tip de examen:
> Muchos distractores en el examen hacen parecer que una herramienta "resolverá todos los problemas". La respuesta correcta suele ser más equilibrada o conservadora.

---

## 📌 6.3 Consideraciones para seleccionar herramientas

### Factores clave al elegir una herramienta:
- **Necesidades del proyecto**
- Compatibilidad con herramientas existentes
- Facilidad de uso e integración
- Soporte y actualizaciones del proveedor
- Costos de licencia y mantenimiento
- Experiencia del equipo

### ✅ **Piloto o prueba de concepto**:
Antes de adoptar una herramienta, se recomienda realizar una **prueba piloto** para validar su efectividad y detectar problemas tempranamente.

---

## 📌 6.4 Implementación de herramientas

### Etapas típicas de adopción:
1. **Análisis de necesidades**
2. **Evaluación y selección**
3. **Prueba piloto**
4. **Implementación**
5. **Entrenamiento**
6. **Revisión y mejora continua**

📌 Tip en examen:
> El proceso de implementación de herramientas es progresivo. Respuestas correctas suelen incluir etapas como “formación del equipo”, “piloto” y “evaluación”.

---

## 📋 RESUMEN RÁPIDO – Capítulo 6

| Tema | Clave para recordar |
|------|----------------------|
| Herramientas de gestión | Pruebas, defectos, requisitos |
| Herramientas de ejecución | Automatización, captura/reproducción |
| Herramientas de análisis | Estático, cobertura, performance |
| Beneficios | Automatiza, ahorra tiempo, mejora precisión |
| Riesgos | Costos, mantenimiento, expectativas irreales |
| Piloto | Validar antes de adopción general |

---

## 📌 Temas más frecuentes en el examen:

| Tema | Frecuencia |
|------|------------|
| Categorías de herramientas | Alta |
| Beneficios y riesgos | Muy alta |
| Selección de herramientas | Media |
| Proceso de implementación | Media |
