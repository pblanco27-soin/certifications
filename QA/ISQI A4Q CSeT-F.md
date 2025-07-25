# 🧪 ISQI A4Q CSeT-F – Capítulo 1: Introducción al testing automatizado y Selenium

---

## 📌 1.1 Introducción a la automatización del testing

### 🎯 ¿Por qué automatizar pruebas?
Automatizar pruebas ayuda a reducir errores humanos, mejorar la repetibilidad y acelerar los ciclos de validación del software.

---

### ✅ Ventajas principales del testing automatizado:

| Ventaja | Descripción |
|--------|-------------|
| Eficiencia | Ahorro de tiempo en pruebas repetitivas |
| Fiabilidad | Resultados consistentes, sin fatiga humana |
| Escalabilidad | Permite probar más funcionalidades en menos tiempo |
| Reusabilidad | Scripts pueden ejecutarse múltiples veces sin esfuerzo extra |

---

### ❌ Desventajas / Desafíos:

| Desventaja | Ejemplo |
|------------|---------|
| Alto costo inicial | Requiere tiempo para escribir y mantener scripts |
| Fragilidad | Pruebas se rompen si cambia la UI |
| Complejidad técnica | Requiere habilidades de programación |

📌 Pregunta típica:
> **¿Cuál de las siguientes es una desventaja de la automatización del testing?**  
> ✅ El mantenimiento constante de los scripts de prueba.

---

## 📌 1.2 Tipos de testing que se pueden automatizar

Selenium se utiliza **principalmente** para pruebas funcionales (también llamadas de caja negra o end-to-end).

| Tipo de prueba | ¿Es común automatizarla con Selenium? | Detalle |
|----------------|------------------------|---------|
| Pruebas funcionales | ✅ Sí | Interacción con la interfaz del usuario |
| Pruebas de regresión | ✅ Sí | Validar que funciones anteriores no se rompieron |
| Pruebas unitarias | ❌ No | Se hacen a nivel de código, no UI |
| Pruebas de carga o rendimiento | ❌ No directamente | Se usan herramientas como JMeter o Gatling |

---

## 📌 1.3 ¿Qué es Selenium?

Selenium es un **framework open source** para automatizar navegadores web. Permite simular acciones humanas (clicks, escritura, navegación).

---

### Componentes principales de Selenium:

| Componente | Descripción |
|------------|-------------|
| Selenium WebDriver | API principal para controlar navegadores reales |
| Selenium IDE | Herramienta de grabación y reproducción para usuarios no técnicos |
| Selenium Grid | Permite ejecutar pruebas en múltiples máquinas/navegadores en paralelo |

---

### ¿Qué lenguajes de programación soporta Selenium?
- Java ✅
- Python ✅
- C# ✅
- JavaScript ✅
- Ruby ✅

---

📌 Pregunta frecuente:
> **¿Qué componente de Selenium se utiliza para ejecutar pruebas en navegadores reales usando código?**  
> ✅ Selenium WebDriver.

---

## 📌 1.4 Testing manual vs testing automatizado

| Característica | Testing Manual | Testing Automatizado |
|----------------|----------------|-----------------------|
| Ejecución | Manual por un tester humano | Automática mediante scripts |
| Tiempo | Lento y repetitivo | Rápido y constante |
| Costo inicial | Bajo | Alto (pero se amortiza a largo plazo) |
| Escenarios complejos | Difícil de repetir con precisión | Fáciles de repetir una y otra vez |

📌 Tené en cuenta:
- El testing manual **no desaparece**. Se usa cuando se requiere juicio humano (UX, pruebas exploratorias).
- La automatización **complementa** el testing manual, no lo reemplaza.

---

## 📋 RESUMEN RÁPIDO – Capítulo 1

| Tema | Clave para recordar |
|------|---------------------|
| Por qué automatizar | Reduce errores, acelera validación |
| Ventajas | Velocidad, repetibilidad, escalabilidad |
| Desventajas | Costo, fragilidad, mantenimiento |
| Qué automatiza Selenium | Pruebas funcionales y regresión |
| Componentes de Selenium | WebDriver, IDE, Grid |
| Comparación con testing manual | Automatización es más rápida pero más costosa al inicio |

---

## 📌 Temas más preguntados del examen (según mock exam):

| Tema | Frecuencia |
|------|------------|
| Ventajas/desventajas de automatización | Muy alta |
| Componentes de Selenium | Alta |
| Casos adecuados para automatizar | Alta |

---

# 🧪 ISQI A4Q CSeT-F – Capítulo 2: Fundamentos de programación

---

## 📌 2.1 Introducción a los conceptos básicos de programación

La automatización con Selenium implica escribir scripts en lenguajes como Java, Python o C#. Es vital conocer conceptos básicos de programación orientada a objetos.

---

### 🧱 Conceptos fundamentales que debés manejar:

| Concepto | Explicación clara | Ejemplo (Java) |
|---------|-------------------|----------------|
| Variable | Espacio en memoria que almacena datos | `int edad = 30;` |
| Tipo de dato | Tipo de valor que puede tener una variable | `String`, `int`, `boolean` |
| Condicionales | Ejecutar código dependiendo de una condición | `if (edad > 18) { ... }` |
| Bucles | Repetir acciones múltiples veces | `for`, `while` |
| Funciones / Métodos | Bloques reutilizables de código | `public void login() { ... }` |
| Clases y objetos | Estructura que encapsula datos y comportamiento | `class Usuario { ... }` |

📌 Pregunta típica:
> **¿Qué estructura se usa para repetir una acción varias veces?**  
> ✅ Un bucle (por ejemplo, `for` o `while`).

---

## 📌 2.2 Estructura básica de un script de Selenium

Un script de prueba automatizada con Selenium suele tener esta estructura básica:

```java
// Importar librerías necesarias
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class MiPrimeraPrueba {
    public static void main(String[] args) {
        // Configurar el driver
        WebDriver driver = new ChromeDriver();

        // Navegar a una URL
        driver.get("https://example.com");

        // Interacciones, validaciones, etc.
        // ...

        // Cerrar el navegador
        driver.quit();
    }
}
```

---

## 📌 2.3 Conceptos clave de la programación orientada a objetos (POO)

Selenium WebDriver se usa dentro de un paradigma orientado a objetos. Los 4 pilares básicos de POO son:

| Pilar | Descripción | Ejemplo básico |
|-------|-------------|----------------|
| Encapsulamiento | Ocultar detalles internos de una clase | Métodos públicos, variables privadas |
| Herencia | Clases que heredan comportamiento de otras | `class LoginPage extends BasePage` |
| Polimorfismo | Mismo método con diferentes implementaciones | `click()` funciona distinto según el elemento |
| Abstracción | Usar interfaces para ocultar la implementación | `WebDriver` es una interfaz, `ChromeDriver` es una implementación |

📌 Pregunta frecuente:
> **¿Qué pilar de la programación orientada a objetos permite ocultar los detalles internos de una clase?**  
> ✅ Encapsulamiento.

---

## 📌 2.4 Librerías comunes usadas con Selenium

Para escribir pruebas efectivas con Selenium, se suele complementar con otras bibliotecas:

| Librería | Uso típico |
|----------|------------|
| JUnit / TestNG | Frameworks para estructurar y ejecutar pruebas |
| Assert / Hamcrest | Validaciones (asserts) |
| Maven / Gradle | Gestión de dependencias |
| Log4j / SLF4J | Registro de logs de prueba |
| Selenium Grid | Ejecución distribuida de pruebas |

---

## 📋 RESUMEN RÁPIDO – Capítulo 2

| Tema | Clave para recordar |
|------|---------------------|
| Variables, condicionales, bucles | Fundamentos de cualquier script |
| Clases, objetos, métodos | Base de Selenium orientado a objetos |
| Encapsulamiento, herencia, polimorfismo | Pilares clave de POO |
| Librerías como JUnit/TestNG | Estructuran y ejecutan pruebas |
| Maven/Gradle | Gestionan dependencias del proyecto |

---

## 📌 Temas más preguntados del examen (según mock exam):

| Tema | Frecuencia |
|------|------------|
| Fundamentos de programación | Muy alta |
| Encapsulamiento y herencia | Alta |
| Librerías auxiliares | Moderada |

---

# 🧪 ISQI A4Q CSeT-F – Capítulo 3: Selenium WebDriver

---

## 📌 3.1 ¿Qué es Selenium WebDriver?

Es el **componente principal de Selenium** que permite controlar navegadores web directamente desde scripts automatizados.

### 🧠 ¿Qué lo hace especial?

- **Soporte para múltiples navegadores**: Chrome, Firefox, Edge, Safari.
- **Independencia del lenguaje**: Java, Python, C#, JavaScript, etc.
- **Simula acciones reales** del usuario: clics, escritura, scroll, validaciones.

---

## 📌 3.2 Arquitectura de Selenium WebDriver

| Componente | Función |
|------------|---------|
| WebDriver API | Permite escribir comandos en el lenguaje de programación |
| Browser Drivers (p. ej., `chromedriver`) | Traducen los comandos a acciones específicas del navegador |
| Navegador real | Donde se ejecuta la prueba como si fuera un usuario real |

**Ejemplo de flujo:**

```
Script (Java) → WebDriver API → ChromeDriver → Chrome (real)
```

---

## 📌 3.3 Configuración básica para ejecutar WebDriver

### 🔧 Pasos esenciales (Java + Chrome):

1. Descargar el `chromedriver` compatible con tu versión de Chrome.
2. Configurar el driver:

```java
System.setProperty("webdriver.chrome.driver", "/ruta/chromedriver");
WebDriver driver = new ChromeDriver();
driver.get("https://example.com");
```

3. Ejecutar acciones → Cerrar navegador:

```java
driver.quit(); // Cierra completamente
```

📌 **Importante para el examen**: `driver.quit()` ≠ `driver.close()`.  
- `quit()` cierra todo el navegador.  
- `close()` cierra solo la pestaña actual.

---

## 📌 3.4 Encontrar elementos en la página (Localizadores)

### Métodos más usados:

| Método | Ejemplo en Java | Descripción |
|--------|------------------|-------------|
| `id` | `driver.findElement(By.id("user"))` | Más rápido y confiable |
| `name` | `By.name("email")` | Útil si no hay `id` |
| `className` | `By.className("btn")` | Cuidado con clases compartidas |
| `tagName` | `By.tagName("input")` | Menos específico |
| `cssSelector` | `By.cssSelector("div > input.btn")` | Muy flexible |
| `xpath` | `By.xpath("//input[@type='submit']")` | Potente, pero más complejo |

✅ **Pregunta típica del examen**:
> ¿Cuál es el método más eficiente para encontrar un elemento si tiene un `id` único?  
> ✅ `By.id("...")`

---

## 📌 3.5 Interacciones básicas con elementos web

| Acción | Código ejemplo | Descripción |
|--------|----------------|-------------|
| Escribir texto | `element.sendKeys("texto")` | Para formularios |
| Click | `element.click()` | Botones, enlaces |
| Obtener texto | `element.getText()` | Leer contenido |
| Limpiar campo | `element.clear()` | Útil antes de `sendKeys()` |

---

## 📌 3.6 Sincronización: Esperas (Waits)

Las páginas web pueden tardar en cargar. Selenium ofrece dos formas de esperar:

### ⏱ Tipos de esperas:

| Tipo | Uso | Ejemplo |
|------|-----|---------|
| Implicita | Espera X segundos por defecto | `driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS)` |
| Explicita | Espera hasta que se cumpla una condición | `WebDriverWait wait = new WebDriverWait(driver, 10);`<br>`wait.until(ExpectedConditions.visibilityOf(element));` |

📌 ¡Importante para el examen! Usar esperas explícitas es más **eficiente y controlado** que depender solo de tiempos fijos como `Thread.sleep()`.

---

## 📌 3.7 Buenas prácticas al usar WebDriver

- Usar `quit()` al final.
- Esperar con `WebDriverWait`, no con `sleep()`.
- Identificar los elementos con `id` si es posible.
- Manejar excepciones (`try/catch`) para evitar que errores detengan la ejecución completa.
- Modularizar tu código (métodos reutilizables).

---

## 📋 RESUMEN RÁPIDO – Capítulo 3

| Tema | Clave para recordar |
|------|---------------------|
| WebDriver | API para controlar navegadores |
| Drivers | Ejecutan comandos del lenguaje al navegador |
| Localizadores | `id`, `cssSelector`, `xpath` son los más usados |
| Acciones | `.click()`, `.sendKeys()`, `.getText()` |
| Esperas | Implicitas y explicitas (preferida) |

---

## 📌 Temas más preguntados del examen (según mock exam):

| Tema | Frecuencia |
|------|------------|
| Uso de localizadores (`By.id`, `By.xpath`) | Muy alta |
| Diferencia entre `quit()` y `close()` | Alta |
| Esperas explícitas (`WebDriverWait`) | Alta |

---

# 🧪 ISQI A4Q CSeT-F – Capítulo 4: Diseño y mantenimiento de scripts de prueba con Selenium WebDriver

---

## 📌 4.1 Diseño de scripts de prueba

Un buen diseño de scripts de prueba:

- Mejora la **legibilidad**.
- Permite el **mantenimiento**.
- Reduce la **duplicación de código**.
- Aumenta la **reutilización**.

### 🧱 Principios clave:

| Principio | Significado |
|----------|-------------|
| DRY (Don’t Repeat Yourself) | Evitar duplicación de código |
| SRP (Single Responsibility Principle) | Cada clase o método debe tener una única responsabilidad |
| Reusabilidad | Crear métodos reutilizables para acciones comunes |
| Legibilidad | Código limpio, comentado y estructurado |

---

## 📌 4.2 Modularización del código

Dividir el código en módulos mejora el mantenimiento.

### ✳️ Ejemplo típico de modularización:

```java
// Clase BasePage
public class BasePage {
    WebDriver driver;

    public BasePage(WebDriver driver) {
        this.driver = driver;
    }

    public void open(String url) {
        driver.get(url);
    }
}
```

```java
// Clase LoginPage que extiende BasePage
public class LoginPage extends BasePage {
    public LoginPage(WebDriver driver) {
        super(driver);
    }

    public void login(String user, String pass) {
        driver.findElement(By.id("user")).sendKeys(user);
        driver.findElement(By.id("pass")).sendKeys(pass);
        driver.findElement(By.id("loginBtn")).click();
    }
}
```

🔁 Este patrón permite reutilizar código y encapsular lógica en clases.

---

## 📌 4.3 Patrones de diseño aplicados a pruebas automatizadas

### 🎯 Page Object Model (POM)

Es el patrón más recomendado y **más preguntado en el examen**.

| Característica | Detalle |
|----------------|---------|
| Objetivo | Separar la lógica de la prueba del acceso a elementos |
| Ventajas | Facilita mantenimiento, reutilización, menor duplicación |
| Estructura | Una clase por página de la aplicación |

📘 **Ejemplo:**

```java
public class LoginPage {
    WebDriver driver;

    By username = By.id("user");
    By password = By.id("pass");
    By loginBtn = By.id("loginBtn");

    public void login(String user, String pass) {
        driver.findElement(username).sendKeys(user);
        driver.findElement(password).sendKeys(pass);
        driver.findElement(loginBtn).click();
    }
}
```

🔁 Luego, el script de prueba se ve limpio y claro:

```java
LoginPage login = new LoginPage(driver);
login.login("admin", "1234");
```

---

## 📌 4.4 Estructura del proyecto de pruebas

### 📂 Organización recomendada:

```
src/
  ├── base/            → Código común (clase BasePage, configuración)
  ├── pages/           → Objetos de página (LoginPage, HomePage, etc.)
  ├── tests/           → Scripts de prueba (TestLogin, TestSearch)
  └── utils/           → Utilidades (lectura de datos, helpers)
```

✅ Ventaja: facilita localizar, modificar y escalar pruebas.

---

## 📌 4.5 Mantenimiento de scripts de prueba

### 🔧 ¿Cómo reducir el costo de mantenimiento?

- **Usar POM**.
- **Evitar localizadores frágiles** como `xpath` absolutos (`/html/body/...`).
- **Centralizar datos de prueba** en archivos externos (p. ej., `.csv`, `.json`).
- **Validar cambios visuales** y de comportamiento cuando fallan las pruebas.
- **Revisar periódicamente los scripts** ante cambios en la aplicación.

📌 ¡Importante para el examen!  
Evitar hard-coded values (valores escritos directamente en el código).

---

## 📋 RESUMEN RÁPIDO – Capítulo 4

| Tema | Clave para recordar |
|------|---------------------|
| Diseño limpio | DRY, SRP, legibilidad, reutilización |
| Modularización | Métodos y clases reutilizables |
| POM | Separar lógica de pruebas y UI |
| Estructura | Dividir en base/pages/tests/utils |
| Mantenimiento | Usar patrones, evitar hardcoding, centralizar datos |

---

## ❓ Preguntas típicas del examen (según el mock oficial)

| Pregunta | Tema relacionado | Respuesta esperada |
|---------|------------------|--------------------|
| ¿Qué patrón permite encapsular elementos de una página? | Page Object Model | ✅ POM |
| ¿Cómo mejorar la legibilidad y mantenimiento de las pruebas? | Modularización y diseño | ✅ Separar lógica y UI |
| ¿Qué NO es una buena práctica? | Hard-coded values | ❌ Usar valores escritos en el código |

---

# 🧪 ISQI A4Q CSeT-F – Capítulo 5: Automatización de pruebas en proyectos

---

## 📌 5.1 Enfoque de equipo

### 🎯 ¿Cuál es el rol del tester automatizador?

- Colabora con desarrolladores, testers manuales, DevOps y Product Owners.
- Traduce criterios de aceptación en pruebas automatizadas.
- Participa desde fases tempranas del ciclo de vida del software.

### 🧑‍🤝‍🧑 Trabajo en equipo:

| Actividad | Participantes |
|----------|----------------|
| Revisión de historias de usuario | Dev, Tester, PO |
| Diseño de pruebas automatizadas | Tester, Dev |
| Integración continua | DevOps, Tester |

🔁 Importante: Automatizar no reemplaza la prueba manual. La complementa.

---

## 📌 5.2 Automatización en metodologías ágiles

### 📍 Enfoque ágil:

- Ciclos iterativos e incrementales.
- Automatización desde el inicio.
- Fuerte colaboración entre roles.

🔍 En ágil se automatiza **lo antes posible** y se mejora continuamente.

---

## 📌 5.3 Criterios para automatizar

Antes de automatizar, considerar:

| Criterio | ¿Automatizar? |
|---------|----------------|
| Prueba repetitiva | ✅ Sí |
| Crítica para negocio | ✅ Sí |
| Difícil de automatizar (captcha, gráficos) | ❌ No |
| Ejecutada una sola vez | ❌ No |

✅ Automatizar pruebas que:

- Son **frecuentes**.
- Afectan funcionalidades **clave**.
- Permiten **feedback rápido**.

---

## 📌 5.4 Limitaciones de Selenium

### ❗ Qué *no* puede hacer Selenium:

- Probar funcionalidades fuera del navegador.
- Validar aspectos visuales complejos (colores, diseño).
- Controlar procesos de backend o servicios externos directamente.
- Interactuar con ventanas del sistema operativo (ventanas modales nativas).

📌 Complementar con herramientas como:

- **Appium** → Para apps móviles.
- **Applitools / Percy** → Para pruebas visuales.
- **Postman / REST Assured** → Para pruebas de APIs.

---

## 📌 5.5 Integración con herramientas de automatización

Selenium se puede integrar con herramientas modernas para facilitar ejecución y monitoreo.

| Herramienta | Propósito |
|------------|-----------|
| Jenkins / GitLab CI | Automatizar pruebas en cada commit (CI/CD) |
| Docker | Ejecutar pruebas en entornos aislados |
| TestNG / JUnit | Estructurar y reportar pruebas |
| Allure / ExtentReports | Reportes visuales |
| BrowserStack / Sauce Labs | Pruebas remotas en múltiples navegadores/SO |

📘 **Ejemplo de pipeline básico en Jenkins:**

```bash
# Ejecutar pruebas automáticamente al hacer push
mvn clean test
```

🔁 Los resultados pueden mostrarse en dashboards o integrarse con Slack / correo.

---

## 📋 RESUMEN RÁPIDO – Capítulo 5

| Tema | Clave para recordar |
|------|---------------------|
| Rol del tester | Colabora en todo el ciclo, no trabaja aislado |
| Ágil | Automatización temprana, iterativa |
| Qué automatizar | Repetitivo, crítico, estable |
| Limitaciones | Solo pruebas web en navegador |
| Integraciones | Jenkins, Docker, reportes, CI/CD |

---

## ❓ Preguntas típicas del examen

| Pregunta | Tema relacionado | Respuesta esperada |
|---------|------------------|--------------------|
| ¿Qué prueba es mejor candidata para automatizar? | Prueba regresiva frecuente | ✅ Sí |
| ¿Cuál no es una fortaleza de Selenium? | Pruebas de servicios backend | ❌ No |
| ¿Qué herramienta complementa Selenium para CI? | Jenkins | ✅ Sí |
