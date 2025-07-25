# 🧪 ISQTB CTFL-AcT – Capítulo 1: Introducción al Testing de Aceptación

---

## 📌 1.1 Propósito del testing de aceptación

### ✅ ¿Qué es el testing de aceptación?
Es un tipo de prueba **formal y planificada** que verifica si un sistema cumple con los **criterios de aceptación acordados** y si está **listo para ser liberado** al usuario final o cliente.

### ✅ Objetivos principales:
- Confirmar que el sistema **cumple los requisitos del negocio**.
- Validar que el software está listo para el **uso en producción**.
- Obtener **confianza y aprobación** de las partes interesadas.

### ❗Importante:
- Se basa en **criterios definidos con anterioridad**.
- **No se limita a probar funcionalidad**, también cubre aspectos no funcionales (usabilidad, rendimiento, etc.).

📌 Ejemplo típico de examen:
> **P: ¿Cuál es el propósito del testing de aceptación?**  
> **R correcta:** Validar que el sistema cumple los criterios de aceptación previamente acordados.

---

## 📌 1.2 Tipos de testing de aceptación

### Existen distintos tipos, dependiendo del contexto y del stakeholder principal:

| Tipo de prueba de aceptación | Quién la realiza | En qué contexto |
|------------------------------|------------------|------------------|
| ✅ **Prueba de aceptación del usuario (UAT)** | Usuarios del negocio | Sistemas internos, software personalizado |
| ✅ **Prueba de aceptación operativa** | Equipo de operaciones (admins, DevOps) | Infraestructura, despliegue, mantenimiento |
| ✅ **Prueba contractual y regulatoria** | Cliente o entidades regulatorias | Cumplimiento de contrato o normativas |
| ✅ **Prueba alfa y beta** | Usuarios reales o potenciales | Productos comerciales listos para lanzar |

📌 Detalle de tipos frecuentes:

- **UAT**: usuarios reales validan procesos de negocio.
- **Operativa**: se comprueba si el sistema puede operar en producción (backups, logs, monitoreo).
- **Regulatoria**: cumplimiento con leyes, normas o estándares.
- **Beta**: versión preliminar del producto, feedback real antes del lanzamiento.

---

## 📌 1.3 Colaboración en el testing de aceptación

### Enfoque moderno: colaboración temprana
El testing de aceptación debe involucrar desde el inicio a:

- **Desarrolladores**
- **Testers**
- **Product Owners**
- **Usuarios del negocio**
- **Operaciones**

Esto se alinea con los principios ágiles: **"el testing es responsabilidad de todo el equipo"**.

### Herramientas para colaborar:
- Talleres de definición de criterios de aceptación
- Historias de usuario claras
- Lenguaje común (ubiquitous language)

📌 Ejemplo frecuente de pregunta:
> **P: ¿Cuál es una ventaja clave de involucrar a los usuarios del negocio desde temprano?**  
> **R correcta:** Asegurar que los criterios de aceptación reflejen las necesidades reales del negocio.

---

## 📋 RESUMEN RÁPIDO – Capítulo 1

| Concepto | Clave para recordar |
|---------|----------------------|
| Testing de aceptación | Validar que el sistema cumple requisitos del negocio |
| UAT | Usuarios finales prueban funcionalidad |
| Operativa | Admins validan entorno de producción |
| Regulatoria/contractual | Cumplimiento legal o contractual |
| Alfa/Beta | Pruebas tempranas con usuarios reales |
| Colaboración | Fundamental desde etapas tempranas |

---

## 📌 Temas más frecuentes del examen:

| Tema | Frecuencia |
|------|------------|
| Propósito del acceptance testing | Muy alta |
| Tipos de pruebas de aceptación | Muy alta |
| Involucramiento de stakeholders | Alta |
| Alfa vs Beta | Media |

---

# 🧪 ISQTB CTFL-AcT – Capítulo 2: Contribución al Testing de Aceptación

---

## 📌 2.1 Roles y colaboración en testing de aceptación

### 🎯 Rol del tester en el testing de aceptación:
El tester colabora activamente con stakeholders para:
- Entender el **contexto del negocio**
- Asegurar que los criterios de aceptación estén **claros y verificables**
- Diseñar y ejecutar pruebas alineadas con los **objetivos del negocio**

### ✅ Actividades del tester:
- Ayudar a definir criterios de aceptación.
- Revisar y clarificar historias de usuario.
- Identificar inconsistencias o ambigüedades.
- Diseñar escenarios de prueba enfocados en la **valoración del negocio**, no solo la funcionalidad.

📌 Pregunta típica:
> **P: ¿Cuál es un aporte clave de un tester al testing de aceptación?**  
> **R correcta:** Asegurar que los criterios de aceptación sean claros, completos y verificables.

---

## 📌 2.2 El enfoque de equipo en pruebas de aceptación

### 🧠 Principio Agile: **“Testing es responsabilidad de todos”**

El equipo completo colabora en las siguientes tareas:
- Identificar criterios de aceptación desde el inicio.
- Discutir ejemplos de negocio con stakeholders.
- Refinar historias de usuario para que sean **comprensibles y testeables**.

### Técnicas para colaborar:
- **Three Amigos**: Product Owner + Dev + Tester discuten cada historia de usuario.
- **Talleres colaborativos**: análisis de historias, definición de reglas de negocio.
- **BDD**: fomenta una colaboración basada en el lenguaje común (más adelante se amplía en el capítulo 3).

📌 Pregunta de examen:
> **P: ¿Qué representa el enfoque “Three Amigos”?**  
> **R correcta:** Una colaboración entre PO, desarrollador y tester para refinar historias y criterios de aceptación.

---

## 📌 2.3 Artefactos para el testing de aceptación

### 📄 Artefactos clave utilizados:
- **Historias de usuario**: describen funcionalidades desde la perspectiva del usuario.
- **Criterios de aceptación**: definen cuándo una historia está “terminada” y aceptada.
- **Reglas de negocio**: definen restricciones y comportamientos esperados.
- **Modelos de negocio**: como procesos, diagramas de flujo, BPMN, etc.

### Relación entre artefactos:

| Artefacto | Propósito |
|-----------|-----------|
| Historia de usuario | Qué se necesita y por qué |
| Criterios de aceptación | Cómo sabremos que está bien hecho |
| Reglas de negocio | Qué condiciones o cálculos aplicar |
| Modelos de negocio | Visualización del flujo y lógica |

📌 Ejemplo de pregunta:
> **P: ¿Cuál artefacto describe condiciones bajo las cuales una historia de usuario se acepta?**  
> **R correcta:** Los criterios de aceptación.

---

## 📋 RESUMEN RÁPIDO – Capítulo 2

| Concepto | Clave para recordar |
|---------|----------------------|
| Rol del tester | Ayuda a definir y validar criterios de aceptación |
| Trabajo en equipo | Dev + PO + Tester colaboran desde el inicio |
| Three Amigos | Técnica para clarificar historias y criterios |
| Artefactos clave | Historias de usuario, criterios, reglas de negocio |

---

## 📌 Temas más frecuentes del examen:

| Tema | Frecuencia |
|------|------------|
| Rol del tester y colaboración | Alta |
| Enfoque “Three Amigos” | Alta |
| Uso de artefactos | Media a alta |
| Definición de criterios de aceptación | Muy alta |

---

# 🧪 ISQTB CTFL-AcT – Capítulo 3: Trabajo con Comportamiento Deseado (BDD)

---

## 📌 3.1 Propósito de BDD (Behavior-Driven Development)

### 🎯 ¿Qué es BDD?
Es una técnica de desarrollo **centrada en el comportamiento deseado del sistema**, expresado en un lenguaje **natural y entendible para todos los stakeholders**.

### Propósitos clave de BDD:
- Facilitar la **colaboración entre negocio y desarrollo**
- Alinear el desarrollo con los **objetivos del negocio**
- Usar un **lenguaje común (ubiquitous language)** en todas las etapas
- Generar **especificaciones que son también pruebas ejecutables**

### Principio base:
> Si todos usamos el mismo lenguaje para describir lo que debe hacer el sistema, es más fácil construirlo bien y probarlo mejor.

📌 Pregunta típica:
> **P: ¿Cuál es el propósito principal del enfoque BDD?**  
> **R correcta:** Alinear el desarrollo con los objetivos del negocio usando un lenguaje común.

---

## 📌 3.2 Características del lenguaje común (ubiquitous language)

### ✅ ¿Qué es?
Es un vocabulario compartido que:
- Usa **términos del negocio**
- Evita ambigüedad técnica
- Permite que todos (desarrolladores, testers, usuarios) **entiendan y colaboren**

📌 Ejemplo:
En lugar de decir “validar input”, el lenguaje común diría:  
👉 “El cliente no debe poder comprar si no ha ingresado su número de tarjeta válido”.

### Beneficios del lenguaje común:
- Reducción de malentendidos
- Mejora en la calidad de los criterios de aceptación
- Mejora la comunicación entre negocio, testers y desarrollo

---

## 📌 3.3 Relación entre ejemplos concretos y criterios de aceptación

### 🔁 De criterio → ejemplo → prueba

BDD transforma **criterios de aceptación** en **ejemplos concretos** que luego se convierten en **pruebas automáticas**.

### 🧩 Ejemplo típico:
**Historia**: “Como usuario, quiero recibir una confirmación por email después de registrarme.”  
**Criterio**: “El sistema debe enviar un email si el registro fue exitoso.”  
**Ejemplo (escenario)**: “Dado que el usuario completa el formulario correctamente, cuando presiona 'Registrarse', entonces debe recibir un correo de confirmación.”

Este tipo de redacción estructurada se desarrolla en Gherkin (ver más abajo).

📌 Pregunta típica:
> **P: ¿Qué beneficio tiene transformar un criterio de aceptación en un ejemplo concreto?**  
> **R correcta:** Clarifica la intención y permite automatizar la verificación.

---

## 📌 3.4 Sintaxis Gherkin

### 🧾 ¿Qué es Gherkin?
Es un **lenguaje estructurado de BDD** para describir escenarios de prueba de forma natural y comprensible.

### 📌 Estructura:
```gherkin
Funcionalidad: Registro de usuario
  Escenario: Usuario se registra exitosamente
    Dado que el usuario completa todos los campos requeridos
    Cuando presiona el botón "Registrarse"
    Entonces debe recibir un correo de confirmación
```

| Palabra clave | Función |
|---------------|---------|
| **Funcionalidad** | Contexto general |
| **Escenario** | Comportamiento a probar |
| **Dado** | Estado inicial |
| **Cuando** | Acción del usuario |
| **Entonces** | Resultado esperado |

### Beneficios:
- Es comprensible para todos.
- Se puede automatizar con herramientas como Cucumber o SpecFlow.
- Reduce la ambigüedad de los requisitos.

📌 Pregunta frecuente:
> **P: ¿Cuál palabra clave en Gherkin representa la acción realizada por el usuario?**  
> **R correcta:** “Cuando”

---

## 📋 RESUMEN RÁPIDO – Capítulo 3

| Concepto | Clave para recordar |
|---------|----------------------|
| BDD | Enfocado en comportamiento, colaboración y lenguaje común |
| Lenguaje común | Vocabulario del negocio compartido por todos |
| De criterio a ejemplo | Paso clave para automatizar pruebas |
| Gherkin | Sintaxis estructurada: Dado, Cuando, Entonces |

---

## 📌 Temas más frecuentes del examen:

| Tema | Frecuencia |
|------|------------|
| Propósito del BDD | Muy alta |
| Lenguaje común (ubiquitous language) | Alta |
| Sintaxis de Gherkin | Muy alta |
| Relación entre criterios y ejemplos | Alta |

---

# 🧪 ISQTB CTFL-AcT – Capítulo 4: Evaluación de Sistemas para la Aceptación

---

## 📌 4.1 Evaluación de los resultados de las pruebas de aceptación

### 🎯 ¿Qué es la evaluación en el contexto de testing de aceptación?
Es el **proceso de comparar los resultados obtenidos contra los criterios de aceptación**, para determinar si el sistema puede ser aceptado o no.

### 📊 Actividades clave en la evaluación:
- Analizar los **resultados de ejecución** de pruebas
- Identificar **desviaciones** respecto a lo esperado
- Determinar si las pruebas pasaron o fallaron
- Evaluar la **completitud** de los criterios de aceptación

### 📌 Resultado final:
> Decisión informada: ¿Se acepta o no el sistema/software?

📌 Pregunta típica:
> **P: ¿Qué determina si un sistema cumple los criterios de aceptación?**  
> **R correcta:** La comparación entre los resultados reales y los criterios esperados.

---

## 📌 4.2 Técnicas para evaluar criterios de aceptación y cobertura de requisitos

### 🔍 ¿Cómo se mide si se ha probado “lo suficiente”?

#### 1. **Cobertura de criterios de aceptación**
- ¿Todos los criterios fueron cubiertos por pruebas?
- ¿Se probaron condiciones normales y excepcionales?

#### 2. **Trazabilidad**
- ¿Cada requisito/caso de uso tiene pruebas que lo validen?
- Se utilizan **matrices de trazabilidad** para asegurar que:
  - Cada requisito tiene pruebas asociadas
  - Cada prueba tiene un objetivo claro y válido

#### 3. **Indicadores comunes**:
| Indicador | Significado |
|----------|-------------|
| % criterios cubiertos | Nivel de cobertura funcional |
| % pruebas exitosas | Nivel de calidad alcanzado |
| Riesgo residual | Nivel de riesgo que queda tras las pruebas |

📌 Pregunta frecuente:
> **P: ¿Qué técnica se usa para asegurar que todos los requisitos tienen pruebas asociadas?**  
> **R correcta:** Trazabilidad bidireccional

---

## 📌 4.3 Evaluación de la calidad del sistema y la preparación para la liberación

### 🎯 ¿Qué se considera antes de liberar un sistema?

#### Factores clave:
- ¿Se cumplieron todos los **criterios de aceptación**?
- ¿Se alcanzó la **cobertura esperada**?
- ¿Se gestionaron adecuadamente los **riesgos conocidos**?
- ¿Hay defectos abiertos? ¿Son críticos?
- ¿Está completo el **soporte documental**?

#### Participantes en la decisión:
- **Testers de aceptación**
- **Stakeholders del negocio**
- **Responsables de calidad**
- **Desarrollo (para soporte técnico)**

📌 Frase clave:
> *"No se trata solo de que las pruebas pasen, sino de que los objetivos del negocio se hayan cumplido con la calidad esperada."*

📌 Pregunta típica:
> **P: ¿Cuál de los siguientes factores influye en la decisión de liberar un sistema?**  
> **R correcta:** Evaluación de criterios de aceptación, cobertura de pruebas y riesgos residuales

---

## 📋 RESUMEN RÁPIDO – Capítulo 4

| Tema | Clave para recordar |
|------|---------------------|
| Evaluación de resultados | Comparar lo obtenido con lo esperado |
| Trazabilidad | Requisito ↔ prueba ↔ resultado |
| Técnicas de cobertura | Miden calidad y completitud |
| Decisión de liberación | Basada en criterios, cobertura y riesgos |

---

## 📌 Temas más frecuentes del examen:

| Tema | Frecuencia |
|------|------------|
| Evaluación contra criterios | Alta |
| Trazabilidad | Muy alta |
| Cobertura de requisitos | Alta |
| Decisión de liberación | Alta |

---

# 🧪 ISQTB CTFL-AcT – Capítulo 5: Automatización del Testing de Aceptación

---

## 📌 5.1 Propósito, beneficios y limitaciones de la automatización

### 🎯 Propósito de automatizar pruebas de aceptación:
- Validar **criterios de aceptación** de forma rápida y repetible.
- Mejorar la **retroalimentación continua** durante el desarrollo.
- Permitir **regresiones frecuentes** con bajo esfuerzo.

---

### ✅ Beneficios de automatizar:
| Beneficio | Explicación |
|----------|-------------|
| Velocidad | Ejecución mucho más rápida que manual |
| Repetibilidad | Mismo resultado bajo mismas condiciones |
| Confiabilidad | Menor error humano |
| Escalabilidad | Más pruebas con menos recursos |
| Documentación viva | Scripts reflejan criterios de aceptación |

---

### ❌ Limitaciones comunes:
| Limitación | Riesgo |
|------------|--------|
| Costo inicial | Alto esfuerzo de configuración |
| Mantenimiento | Cambios frecuentes en requisitos rompen pruebas |
| Falsos positivos/negativos | Requiere datos estables y entornos controlados |

📌 Pregunta frecuente:
> **P: ¿Cuál de los siguientes es un beneficio clave de la automatización del testing de aceptación?**  
> **R correcta:** Permitir retroalimentación rápida y continua.

---

## 📌 5.2 Implementación de automatización del testing de aceptación

### 🛠️ Componentes típicos:
1. **Herramientas de BDD**: Cucumber, SpecFlow, Behave, etc.
2. **Lenguaje común (Gherkin)**: Facilita la escritura de pruebas legibles por negocio y automatizables.
3. **Frameworks de ejecución**: Integración con pipelines (CI/CD) para ejecutar en cada build.

---

### 📋 Requisitos para una implementación efectiva:
- Historias de usuario con criterios **claros y concretos**
- Participación activa de negocio + testers + devs
- Datos de prueba consistentes y automatizables
- Integración con gestión de pruebas y código fuente

---

### 🔁 Proceso típico:
1. El Product Owner escribe criterios de aceptación.
2. El equipo define ejemplos en lenguaje común (Gherkin).
3. Los testers/devs implementan los pasos técnicos (bindings).
4. Las pruebas se ejecutan automáticamente con cada entrega.

📌 Pregunta típica:
> **P: ¿Cuál es un requisito previo esencial para una buena automatización del testing de aceptación?**  
> **R correcta:** Tener criterios de aceptación claros y verificables.

---

## 📌 5.3 Uso de ejemplos ejecutables

### 🧪 ¿Qué son ejemplos ejecutables?
Son **escenarios escritos en lenguaje natural (como Gherkin)** que se pueden convertir en pruebas automatizadas.

🔹 Ejemplo típico en Gherkin:
```gherkin
Scenario: Usuario inicia sesión exitosamente
Given el usuario está en la página de login
When introduce credenciales válidas
Then accede al panel principal
```

---

### 💡 Beneficios clave:
- **Unificación** del lenguaje entre testers, devs y negocio.
- Mejora de la **colaboración y entendimiento**.
- Permite que los escenarios vivan como **documentación** y **pruebas reales** al mismo tiempo.

📌 Pregunta frecuente:
> **P: ¿Qué ventaja proporciona el uso de ejemplos ejecutables escritos en Gherkin?**  
> **R correcta:** Facilita la comprensión entre stakeholders técnicos y no técnicos.

---

## 📋 RESUMEN RÁPIDO – Capítulo 5

| Tema | Clave para recordar |
|------|---------------------|
| Propósito de automatizar | Aumentar velocidad y confiabilidad |
| Beneficios | Retroalimentación rápida, repetibilidad |
| Limitaciones | Mantenimiento, inversión inicial |
| Herramientas | BDD, Gherkin, frameworks CI/CD |
| Requisitos | Criterios claros + colaboración |
| Ejemplos ejecutables | Escenarios legibles y automatizables |

---

## 📌 Temas más frecuentes del examen:

| Tema | Frecuencia |
|------|------------|
| Beneficios de automatizar | Alta |
| Gherkin / lenguaje común | Muy alta |
| Implementación técnica | Alta |
| Uso de ejemplos ejecutables | Alta |
