# Microsoft Azure AZ-204 Guía de Estudio Completa (Versión en Español)

Esta guía es una referencia integral y autocontenida diseñada para prepararte para el examen **AZ-204: Developing Solutions for Microsoft Azure** sin depender de materiales adicionales. Amplía el plan oficial de habilidades de Microsoft con detalle de implementación, orientación práctica, cuotas, matrices de decisión y tablas de referencia rápida.

> 🚀 **¡Bienvenido!** Trátalo como tu manual de vuelo. Recorre los mapas (tablas), ejecuta los ejercicios (checklists prácticos) y repite escenarios hasta que las decisiones sean automáticas.

### Esquema Oficial de Habilidades (Vigente 11 de abril 2025) y Mapeo
El esquema oficial agrupa habilidades en cinco dominios. Esta guía alinea cada punto con su sección interna para repaso dirigido.

| Dominio Oficial (Peso) | Punto (Abreviado) | Sección Aquí |
| --- | --- | --- |
| Develop Azure Compute Solutions (25-30%) | Container solutions (images, ACR, ACI, ACA) | 1.3 (Trabajos con Contenedores) |
|  | App Service web apps (create, diagnostics, deploy, config, autoscale, slots) | 1.1 App Service |
|  | Azure Functions (create/config, bindings, triggers) | 1.2 Functions (+ host.json apéndice) |
| Develop for Azure Storage (15-20%) | Cosmos DB ops, consistency, change feed | 2.8 Cosmos DB |
|  | Blob properties/metadata, data ops, lifecycle policies | 2.2 Blob Storage + JSON lifecycle |
| Implement Azure Security (15-20%) | AuthN/AuthZ w/ Identity Platform & Entra ID | 3.1 Identidad & tokens ampliado |
|  | Shared Access Signatures | 2.1 / Ejemplos SAS añadidos |
|  | Microsoft Graph interaction | 3.1 (Graph) & Recetas Apéndice |
|  | Secure config w/ App Config & Key Vault | 3.4 Key Vault + Patrones Seguridad |
|  | Managed identities | 3.1 Managed Identities + Código |
| Monitor, Troubleshoot, Optimize (5-10%) | App Insights metrics/logs/traces | 4.1–4.3 + KQL 4.4 |
|  | Alerts, availability tests | 4.1, 4.6, Checklist Hands-on |
| Connect & Consume Azure / Third-Party (20-25%) | API Management (create, document, secure, policies) | 5.5 API Management |
|  | Event-driven (Event Grid, Event Hubs) | 5.4 Arquitecturas Event-Driven |
|  | Messaging (Service Bus, Queue Storage) | 5.3 Service Bus, 2.5 Queue Storage, 5.4 comparaciones |

## Cómo Usar esta Guía 💡
- Comienza con **Exam Essentials** para entender logística, programación y prerrequisitos.
- Recorre las áreas de habilidad en orden. En cada sección:
  - Lee el **Service Overview** para contexto.
  - Estudia **Design Decisions**, **Pricing & Limits** y **Security** para preguntas de escenario.
  - Practica con los **snippets CLI/PowerShell/código** para memoria muscular.
  - Revisa las llamadas **🧠 Alerta de Examen**: imitan trampas y matices del examen.
- Usa los **Hands-on Checklists** para reforzar mediante mini-labs.
- Vuelve a los **Apéndices** para cheatsheets, comandos CLI, patrones KQL, niveles de precios y repaso final.

---

## Exam Essentials
| Ítem | Detalle |
| --- | --- |
| Certificación | Microsoft Certified: Azure Developer Associate |
| Código Examen | AZ-204 |
| Duración | 120 minutos (+ 30 min encuesta & NDA) |
| Formato | ~40-60 preguntas: múltiple opción, drag-and-drop, hot area, listas, casos, pantalla de revisión |
| Puntaje Aprobatorio | 700/1000 |
| Registro | Pearson VUE o Certiport vía [perfil Microsoft Learn](https://learn.microsoft.com/credentials/) |
| Costo | ~USD 165 (varía región; descuento estudiante hasta 50%) |
| Prerrequisitos | Recomendado 1-2 años dev profesional y 6+ meses Azure práctico |
| Renovación | Anual, evaluación online gratuita (open book) |
| Herramientas Permitidas | Pizarra y calculadora en pantalla; sin material externo |

### Tipos de Preguntas
- **Case studies:** Escenario largo, 4-6 preguntas vinculadas. Lee requisitos cuidadosamente; algunos no se pueden volver a ver dentro del caso.
- **Opción múltiple (una o varias):** Atento a "select two" o "select all that apply".
- **Drag-and-drop:** Ordena pasos (pipelines, políticas lifecycle, etc.).
- **Hot area:** Selecciona configuraciones en capturas simuladas del portal.
- **Yes/No statements:** Evalúa cumplimiento del escenario.

### Consejos Día del Examen
- Usa *Mark for review* para dudas, pero nota el bloqueo en case studies.
- Gestiona el tiempo: 1.5–2 min por pregunta, deja ~20 min para repaso.
- Lee cada escenario dos veces; identifica verbos clave (*implement*, *configure*, *diagnose*, *secure*).

---

## 1. Develop Azure Compute Solutions (25-30%)

### 1.1 Azure App Service (Web Apps, API Apps, WebJobs)
**Resumen:** Hosting PaaS para aplicaciones web, APIs REST y jobs de fondo. Soporta Windows/Linux, múltiples lenguajes e imágenes de contenedor.

**Conceptos Clave**
- App Service Plan define región, nivel de precio, escalado. Las apps heredan recursos.
- Deployment slots permiten despliegue sin downtime (swap con warmup).
- Autenticación integrada con Microsoft Entra ID, proveedores sociales, OpenID Connect personalizado.
- Integración: VNet integration (salida), hybrid connections, private endpoints (entrada), dominios personalizados, certificados administrados, backups, staging slots, deployment center (GitHub, DevOps, Git local).
- Escalado: Manual, reglas autoscale (CPU, memoria, HTTP queue, métricas personalizadas). Límite según tier (Standard hasta 10 instancias, Premium v3 hasta 30, Isolated v2 hasta 200).

**Precios & Límites**
- Free/Shared: Compute compartido, sin SLA, solo HTTP. Dev/test.
- Basic/Standard: VMs dedicadas, dominios/SSL, backup diario (Standard), SLA 99.95%.
- Premium v2/v3: Hardware mejorado, redundancia de zona, VNet integration, SLA 99.95%.
- Isolated (ASE v3): Single-tenant dentro de VNet.
- Instancias hasta worker 64-bit, almacenamiento efímero 250 GB por instancia.

**Opciones de Despliegue**
- `az webapp up`, Git local, ZIP (`Run From Package`), contenedor (Docker Hub/ACR), GitHub Actions, Azure DevOps.
- Infra como código: Bicep/ARM (`Microsoft.Web/serverfarms`, `Microsoft.Web/sites`).

**Configuración**
- App settings vs connection strings. Usa slot settings para valores por slot.
- `WEBSITE_RUN_FROM_PACKAGE=1` para despliegues inmutables.
- Variables de runtime (`WEBSITE_NODE_DEFAULT_VERSION`).

**Diagnóstico**
- Application Logging, HTTP Logging, Detailed Errors, Failed Request Tracing.
- `Kudu` para consola y exploración de procesos.

**Seguridad**
- HTTPS obligatorio, TLS mínimo, certificados (PFX), certificados administrados gratis.
- Managed identity para Key Vault, Storage, SQL (Azure AD Auth).

**CLI Quickstart**
```bash
az appservice plan create --name plan-prod --resource-group rg-az204 --sku P1v3 --is-linux
az webapp create --name contoso-api --plan plan-prod --runtime "DOTNETCORE:8.0"
az webapp config appsettings set --name contoso-api --resource-group rg-az204 --settings APPINSIGHTS_INSTRUMENTATIONKEY=$APPINSIGHTS_KEY
```

**🧠 Alerta de Examen**
- Requisito "VNet sin internet público" -> **Isolated**/ASE.
- Slots + GitHub necesitan **Standard+**.
- >30 instancias -> solo **Isolated**.

**🛠️ Checklist Práctico**
- Desplegar app .NET/Node con slots.
- Integrar Key Vault con identidad administrada.
- Configurar autoscale (CPU>70% 10 min).
- Activar logs diagnósticos a Log Analytics.

**💡 Tip:** Usa warm-up pings para evitar latencia post-swap.
**⚠️ Pitfall:** No marcar connection strings como slot settings expone secretos.

### 1.2 Azure Functions
**Resumen:** Compute serverless orientado a eventos para ejecutar código ligero. Soporta .NET, Node.js, Python, Java, PowerShell, Go y handlers personalizados.

**Planes de Hosting**
- Consumption: Serverless pago por ejecución y tiempo. Escalado automático. Timeout por defecto 5 min (host.json hasta 10 min).
- Premium: Instancias pre-warmed, duración ilimitada, VNet integration, sin cold start, escalado elástico.
- Dedicated (App Service Plan): Usa capacidad existente del plan.
- Azure Container Apps: Funciones empaquetadas en contenedor con escalado KEDA.

**Triggers & Bindings**
- Triggers: HTTP, Timer, Queue Storage, Service Bus Queue/Topic, Event Hub, Event Grid, Cosmos DB (change feed), Blob, Durable, SignalR.
- Bindings entrada/salida simplifican operaciones (ej. salida a Queue, entrada Cosmos).
- Configuración via atributos (C#) o function.json.

**Durable Functions**
- Patrones: chaining, fan-out/fan-in, async HTTP (status polling), human interaction (external events), monitor.
- Entities: Objetos con estado direccionables por ID.
- Estado en Azure Storage (Queues, Tables, Blobs) o proveedor Netherite (Event Hubs).
- Orquestaciones deterministas: evita DateTime directo, usa `context.CurrentUtcDateTime`.

**Escalado**
- Consumption: hasta 200 instancias dinámicas; controlador basado en métricas de trigger.
- Configura concurrencia HTTP y colas en host.json.

**Mitigación Cold Start**
- Premium (pre-warmed), Always On, trimming .NET, reducir dependencias pesadas.

**Seguridad**
- Niveles de autorización HTTP: Anonymous / Function / Admin.
- Managed Identity para secretos / recursos.
- Usa API Management para políticas (rate limit, transformación JWT).

**Monitoreo**
- Application Insights (telemetría de ejecución, cold starts, failures). Live Metrics.

**Ejemplo host.json (claves relevantes)**
```jsonc
{
  "version": "2.0",
  "extensions": {
    "http": { "routePrefix": "api", "maxOutstandingRequests": 200, "maxConcurrentRequests": 100 },
    "queues": { "batchSize": 16, "newBatchThreshold": 8, "visibilityTimeout": "00:00:30" },
    "serviceBus": { "prefetchCount": 20, "messageHandlerOptions": { "autoCompleteMessages": false, "maxConcurrentCalls": 16 } }
  },
  "functionTimeout": "00:10:00"
}
```

**🧠 Alerta de Examen**
- Caso largo con estado/humano -> Durable Functions.
- VNet + serverless -> Premium (Consumption no soporta VNet directa).
- Evitar cold start consistente -> Premium.

**⚠️ Pitfall:** Lógica no determinista dentro de orquestador provoca replays inconsistentes.

### 1.3 Trabajos con Contenedores 🐳

#### Azure Container Apps (ACA)
- Plataforma serverless sobre Kubernetes + Dapr + KEDA.
- Revisions con división de tráfico (blue/green, canary).
- Escalado: min/max réplicas, triggers HTTP, eventos (KEDA), métricas personalizadas.
- Dapr: pub/sub, service invocation, state, bindings.
- Managed identity, Key Vault secrets. Despliegue: `az containerapp up`, Bicep, Terraform.

#### Azure Kubernetes Service (AKS) *(Profundidad extendida, exam suele ser conceptual)*
- Kubernetes administrado (control plane gratis). Pagas nodos.
- Node pools (Linux/Windows), autoscaler, upgrades, Azure CNI/Kubenet.
- Seguridad: Azure AD RBAC, network policies, private cluster, Defender.
- Integraciones: CSI Secrets Store + Key Vault, ingress controllers.

#### Azure Container Instances (ACI)
- Contenedores sin orquestador para jobs puntuales / batch.
- Arranca en segundos, paga por segundo. Soporta VNet, GPU, Linux/Windows.

#### Web App for Containers
- Variante App Service para una imagen Docker (o compose Linux) con slots y diagnósticos.

#### Azure Container Registry (ACR)
- Registro privado Docker.
- Tiers: Basic / Standard / Premium (geo-replication, content trust, private endpoints, scope maps, tokens).
- ACR Tasks (builds automatizados, triggers por base image). Retention policies.

**🧠 Alerta de Examen**
- Canary con división de tráfico rápida -> Container Apps.
- GPU puntual / job simple -> ACI.
- Microservicios complejos, malla, control granular -> AKS.

**⚠️ Pitfall:** Olvidar probes (liveness/readiness) en AKS causa detección lenta de fallos.

### 1.4 Virtual Machines & Scale Sets
- VM: Control total del SO; escala manual.
- VM Scale Sets: Conjunto homogéneo, autoscale por métricas (CPU, memoria, schedule).
- Usar cuando se requieren dependencias de SO específicas o agentes propietarios.

### 1.5 Procesamiento en Segundo Plano & Batch
- **WebJobs:** Scripts/binaries dentro contexto App Service; continuous o triggered.
- **Azure Batch:** Procesamiento a gran escala (pools, jobs, tasks); útil para cargas paralelas; integración con Storage.
- **Azure Logic Apps:** Orquestación basada en conectores; Standard vs Consumption; flujos aprobaciones.
- **Data Factory / Synapse Pipelines:** ETL/ELT (no foco principal en AZ-204 para profundidad, conocer concepto).

### 1.6 Automatización de Despliegues & DevOps
**Infra como Código**
- ARM templates (JSON), Bicep (DSL preferido), Terraform (HCL) para multi-cloud.
- Módulos Bicep para reutilización; `az deployment group create` / `terraform plan/apply`.

**CI/CD**
- GitHub Actions: acciones `azure/login`, `azure/webapps-deploy`, `azure/functions-action`.
- Azure DevOps Pipelines YAML, service connections, variable groups.

**Estrategias Release**
- Blue/Green (slots), Canary (Container Apps revisions / APIM versioning), Feature Flags (App Configuration), Rolling (AKS).

**Patrones Testing**
- Unit, Integration, Load (Azure Load Testing), ephemeral env (Bicep + pipeline).

**🧠 Alerta de Examen**
- Requerimiento rollback instantáneo -> slots App Service.
- Multi-env reproducible -> IaC (Bicep/Terraform) + pipelines.

**⚠️ Pitfall:** Incluir secretos estáticos en YAML en lugar de Key Vault / GitHub Secrets.

---

## 2. Develop for Azure Storage (15-20%)
> 📦 Domina patrones de SAS, lifecycle y particionamiento: aparecen en muchos escenarios.

### 2.1 Fundamentos de Storage Account
**Tipos**
- General-purpose v2 (GPv2) – recomendada; soporta blobs, files, queues, tables, Data Lake.
- Premium block blob (`BlockBlobStorage`) – baja latencia SSD.
- Premium file (`FileStorage`) – SMB 3.0 en SSD.
- Premium page blob (`PageBlobStorage`) – para discos no administrados / IOPS consistentes.

**Endpoints**
- Formato: `https://<account>.blob.core.windows.net`, `.file`, `.queue`, `.table`, `.dfs` (Data Lake), `.web` (static website).
- Dominios personalizados soportados para blob.

**Access Tiers**
- Hot, Cool, Cold (preview), Archive. Retención mínima: Cool 30 días, Archive 180 días. Archive requiere rehidratación (Standard vs High priority).

**Redundancia**
- LRS, ZRS, GRS, RA-GRS, GZRS, RA-GZRS. Entiende trade-offs RPO/RTO.

**Networking**
- Public access on/off, firewall IP, service endpoints, private endpoints, SAS.

**Seguridad**
- Cifrado en reposo (Microsoft-managed keys) o Customer-managed (Key Vault / HSM).
- Azure AD RBAC para plano de datos (Blob Data Contributor, etc.).

**Protección de Datos**
- Soft delete (blobs y contenedores), versioning, change feed (auditoría), point-in-time restore.

**Monitoreo**
- Métricas: transacciones, latencia. Logs diagnósticos a Log Analytics.

**🧠 Alerta de Examen**
- User Delegation SAS recomendado sobre account key SAS para acceso delegado de corta duración vía identidad.
- Políticas de inmutabilidad (legal hold / time-based) para WORM.

### 2.2 Blob Storage Deep Dive 📦
**Tipos de Blob**
- Block Blob (hasta ~190.7 TiB), Append Blob (logs), Page Blob (IO aleatorio 8 TiB).

**Operaciones / Rendimiento**
- Subida segmentada (`StageBlock` + `CommitBlockList`). AzCopy para cargas masivas.
- Optimizar concurrencia (paralelismo controlado para evitar 429).

**Características**
- Static website (`$web`), snapshots, incremental copy, object replication, lifecycle management (JSON), acceso jerárquico (ADLS Gen2 habilitando hierarchical namespace).

**Acceso**
- SAS (Account, Service, User Delegation), RBAC (roles Data), Access tiers (`SetAccessTier`), CORS.

**Seguridad**
- Deshabilitar acceso anónimo, forzar TLS 1.2, private endpoints, logging.

**Ejemplo .NET**
```csharp
BlobClient client = new BlobClient(connectionString, "images", "logo.png");
await client.UploadAsync(stream, overwrite: true);
var props = await client.GetPropertiesAsync();
await client.SetMetadataAsync(new Dictionary<string,string>{{"owner","marketing"}});
```

**SAS Esencial**
- Permisos: r (read), w (write), d (delete), l (list), c (create), a (add), x (delete prev version), t (tag), f (filter tag).
- Stored Access Policy permite revocación sin regenerar keys.

**CLI User Delegation SAS**
```bash
az storage blob generate-sas \
  --account-name $STORAGE \
  --container-name images \
  --name logo.png \
  --permissions r \
  --expiry $(date -v+15M -u +%Y-%m-%dT%H:%MZ) \
  --auth-mode login \
  --as-user
```

**Cuándo preferir User Delegation SAS**
- Menor exposición de claves, alineado a identidad Azure AD, expiraciones cortas.

**⚠️ Pitfall:** SAS con expiración larga incrementa superficie de riesgo.

### 2.3 Azure Data Lake Storage Gen2
- Combina Blob + namespace jerárquico.
- ACL POSIX sobre directorios/archivos, herencia basada en ruta.
- Usar endpoint `dfs` para operaciones ACL.
- Integración con Synapse, Databricks, HDInsight, Azure Data Explorer.
- Patrones: particionado por carpetas (fecha/cliente) para pruning eficiente.
- Seguridad: Azure AD, managed identity, ACLs.

**🧠 Alerta de Examen**
- Requisito ACL a nivel de carpeta + análisis Hadoop/Spark -> ADLS Gen2.
- Jerarquía / analytics vs Blob plano.

### 2.4 Azure Table Storage & Cosmos DB Table API
- NoSQL key-value schemaless. Entity <= 1 MB.
- Clave compuesta PartitionKey + RowKey única.
- Batching hasta 100 operaciones misma partición.
- Table API en Cosmos añade distribución global + RU/s + índices automáticos.

### 2.5 Azure Queue Storage
- Mensajes base64 hasta 64 KB (patrón claim-check para más grandes en Blob).
- Visibility timeout, dequeue count, poison queue (`<queue>-poison`).
- Entrega al menos una vez -> implementar idempotencia.
- Integración con Azure Functions Queue Trigger.

### 2.6 Azure Files & Azure File Sync
- SMB compartido (Windows, Linux, macOS). NFS 4.1 (premium) para Linux.
- Snapshots y soft delete.
- Azure File Sync: caché local + cloud tiering liberando espacio; requiere Storage Sync Service y sync group.

### 2.7 Azure Disk Storage (Managed Disks)
- Tipos: Standard HDD, Standard SSD, Premium SSD, Premium SSD v2, Ultra Disk.
- Snapshots incrementales, shared disks (clustering), Disk Encryption Set.

### 2.8 Azure Cosmos DB
**APIs**: SQL (Core), MongoDB, Cassandra, Gremlin, Table, PostgreSQL (Hyperscale).

**Throughput**
- Provisioned RU/s (contenedor o DB), Autoscale (rango 10x), Serverless (pago por solicitud).
- RU depende tamaño item, índice, query. Usar QueryMetrics.

**Consistencia**
- Strong, Bounded Staleness, Session (default), Consistent Prefix, Eventual.

**Particionamiento**
- Clave con alta cardinalidad y distribución uniforme; límite 20 GB por partición lógica.
- Requiere re-modelar si hot partition.

**Indexación**
- Automática; política para incluir/excluir, índices compuestos, espaciales.
- TTL a nivel contenedor o item.

**Change Feed**
- Flujo ordenado de cambios. Usar trigger Functions o Change Feed Processor (lease container).

**Seguridad**
- Claves primarias/secundarias, resource tokens, Azure AD RBAC, firewalls IP, private endpoints, CMK.

**Backups**
- Periódico (cada 4h) o Continuous (point-in-time).

**🧠 Alerta de Examen**
- TTL para expiración automática.
- Multi-region write -> conflicto (LWW o stored procedure).

### 2.9 Bases de Datos Relacionales
#### Azure SQL Database
- Opciones: Single, Elastic Pool, Managed Instance.
- Modelos: DTU (legacy) y vCore (General Purpose, Business Critical, Hyperscale, Serverless).
- HA: Zone redundant (BC), failover groups.
- Seguridad: TDE, Always Encrypted, Azure AD Auth, firewall, private endpoint, auditing.

#### PostgreSQL/MySQL (Flexible Server)
- Ventana mantenimiento configurable, HA zona redundante.
- Hyperscale (PostgreSQL) para Citus.

#### SQL Managed Instance
- Compatibilidad mayor (Agent, cross DB queries). Solo dentro VNet.

### 2.10 Cache & Search
- **Azure Cache for Redis:** TTL por clave, clustering (Premium), persistence, geo-rep.
- **Azure Cognitive Search:** Índices, escalado por replicas x partitions, AI enrichment.
- **Azure SignalR Service:** Conexiones en tiempo real; plan serverless con Functions.

**Checklist Práctico Storage**
- Lifecycle policy blobs (hot->cool->archive->delete).
- Contenedor Cosmos autoscale + consumidor change feed.
- Azure SQL con private endpoint + managed identity.
- Redis cache frente a Cosmos fallback.

**Blob Lifecycle JSON Ejemplo**
```json
{
  "rules": [
    {
      "name": "tier-and-expire",
      "enabled": true,
      "type": "Lifecycle",
      "definition": {
        "filters": { "blobTypes": ["blockBlob"], "prefixMatch": ["logs/"] },
        "actions": {
          "baseBlob": {
            "tierToCool": { "daysAfterModificationGreaterThan": 30 },
            "tierToArchive": { "daysAfterModificationGreaterThan": 180 },
            "delete": { "daysAfterModificationGreaterThan": 730 }
          }
        }
      }
    }
  ]
}
```

**Ejemplos Clave de Partición Cosmos**
| Escenario | Buena Clave | Motivo |
| --- | --- | --- |
| SaaS multi-tenant | /tenantId | Distribución + filtro natural |
| Telemetría IoT | /deviceId | Aísla series tiempo por dispositivo |
| Pedidos e-commerce | /customerId | Consultas frecuentes por cliente |
| Sesiones juego | /gameSessionId | Aísla estado de sesión |

**¿Qué es un RU (Request Unit)?**
Un RU es la moneda de rendimiento de Cosmos DB: cada operación (lectura, escritura, consulta, upsert) consume una cantidad de Request Units proporcional a CPU, IO y complejidad de indexación. Tú aprovisionas (o usas autoscale) un presupuesto de RU/s por contenedor o base de datos. Si el consumo instantáneo excede el presupuesto, recibes código 429 (Request Rate Too Large) con un encabezado `x-ms-retry-after-ms` recomendando espera.

Ejemplos típicos (aprox, pueden variar por tamaño de documento e índice):
- Lectura punto (Read Item con id + partition key, doc pequeño ~1KB): ~1 RU
- Escritura (Insert/Upsert 1KB): ~5 RU (más si habilitas índices complejos o TTL)
- Consulta filtrada dentro de una partición retornando pocos documentos: 2-5 RU
- Consulta cross-partition con fan-out y agregaciones: 10s–100s RU según volumen
- Operación de cambio de throughput (manual) o mantenimientos internos: 0 RU (administrativo)

Cómo se ve afectado el costo:
- Tamaño de documento: documentos más grandes cuestan más RU en lecturas/escrituras.
- Índices: cada path indexado agrega trabajo en escrituras (más RU). Desindexar campos no consultados ahorra RU.
- Fan-out: consultas que no fijan la clave de partición se disparan a todas las particiones → suma de RU parciales.
- Proyección: devolver solo campos necesarios reduce bytes transferidos y costo.

**Malas Elecciones de Clave de Partición (y por qué)**
- Baja cardinalidad (ej: /region con solo 3 valores) → Crea pocas particiones lógicas y concentra todo el tráfico en ellas generando hotspots; reduce paralelismo y escala horizontal.
- Sesgo alto (un tenant domina el 70% del tráfico) → Esa partición alcanza el límite de RU/s mientras otras quedan infrautilizadas; provoca throttling (429) prematuro.
- Propiedad mutable (ej: /status que cambia a lo largo del ciclo de vida) → No puedes cambiar la partition key de un documento; obliga a reinsertar en nuevo contenedor para "migrar".
- Valores crecientes monotónicos (ej: /timestamp redondeado a minuto) → Los inserts entran secuencialmente en una sola partición generando cola y latencia.
- Demasiada cardinalidad sin agrupación lógica (ej: /uuid aleatorio cuando consultas por usuario) → Pierdes afinidad de consultas; cada query hace fan-out innecesario.

Estrategias para corregir un mal diseño:
- Re-modelar datos y crear nuevo contenedor con clave adecuada; migrar con Change Feed.
- Introducir clave compuesta sintética (ej: `${tenantId}|${yyyyMM}`) para balance temporal + afinidad de tenant.
- Usar materialización denormalizada para queries de acceso frecuente dentro de una partición.

**Optimización de Consumo de RU (Práctico)**
- Proyectar solo campos requeridos (`SELECT c.id, c.status`) en lugar de `SELECT *` para reducir RU y ancho de banda.
- Incluir SIEMPRE la clave de partición en las lecturas punto y queries; si no, fan-out.
- Crear índices personalizados: excluir paths no consultados (`"excludedPaths"`) para abaratar escrituras masivas.
- Pre-agregar (pre-compute) métricas que consultas repetidamente en vez de agregar sobre millones de documentos cada vez.
- Usar TTL para purgar datos fríos y reducir tamaño total (consultas más baratas; menos RU por escaneo de índice).
- Configurar Autoscale si la carga es elástica (ahorra costo sobre aprovisionar RU/s altos 24x7).
- Cache de lectura (ej: Redis) para patrones hot de baja mutación y así reducir read RU.
- Change Feed + proyección incremental: generar vistas materializadas optimizadas para queries de dashboard.

Métricas a vigilar (Azure Monitor / Insights):
- Total Request Units y Normalized RU Consumption: picos cercanos al 100% señalan necesidad de más throughput o mejor partición.
- Throttled Requests (429) count: si persiste, re-evaluar clave o aumentar RU/s.
- Index Transformation Progress: cambios de política de indexación pueden temporalmente elevar RU.

Alerta de Examen: Preguntas suelen darte un patrón de acceso (ej: filtrar por tenant y fecha) — la mejor clave es la que equilibra distribución + coincide con el filtro más frecuente evitando fan-out.

---

## 3. Implement Azure Security (15-20%)
> 🔐 Seguridad impacta de forma transversal; domina identidad, tokens, secretos y aislamiento de red.

### 3.1 Identidad, Autenticación y Autorización (Microsoft Entra ID)
**App Registrations**
- Definir plataformas (Web, SPA, Mobile/Desktop), redirect URIs, logout.
- Definir scopes (Expose an API) y app roles (roles de aplicación) para autorización.

**Permisos**
- Delegated vs Application (app roles). Scopes producen `scp`; roles producen `roles` claim.
- Admin consent para permisos privilegiados (`Directory.Read.All`).

**Credenciales**
- Secrets (vida limitada) o certificados (recomendado para automatización). Rotar antes de expirar.

**Claims Clave**
| Claim | Significado | Nota |
| --- | --- | --- |
| aud | Destino token | Debe coincidir con API | 
| iss | Emisor (tenant) | URL autoridad v2.0 |
| exp | Expiración | Validar lado servidor |
| nbf | Not before | Asegura ventana válida |
| scp | Scopes delegados | Solo en flujos user delegated |
| roles | Roles app | App permissions / app roles |
| oid | Object Id usuario | Estable entre sesiones |
| tid | Tenant Id | Multi-tenant scenarios |
| groups | GUIDs grupos | Puede usar overage claim |

**Validación de Token (API)**
1. Verificar firma (JWKS).
2. `aud` coincide con App Id URI / ClientId.
3. `iss` coincide con tenant esperado.
4. Revisar expiración (`exp`) y `nbf`.
5. Autorizar por `scp` (delegado) o `roles` (aplicación) — no mezclar.

**Modelos de Tenant**
- Single-tenant: Solo directorio propio.
- Multi-tenant: Cualquier Entra ID (authority `common` / `organizations`).
- Multi-tenant + MSA: `common` incluye cuentas personales.

**Managed Identity vs Service Principal**
| Aspecto | Managed Identity | Service Principal |
| --- | --- | --- |
| Gestión credencial | Automática | Manual (secret/cert) |
| Uso fuera Azure | No (limitado) | Sí |
| Rotación | Transparente | Propia/política |
| Escenario ideal | Recurso -> Recurso | Automatizaciones externas |

**Estrategias de Autorización**
- Roles (coarse-grained) + scopes (fine-grained) combinados.
- Minimizar dependencia de groups si son muchos (token overage) -> usar app roles.

**Pitfalls Frecuentes**
- Usar Client Credentials para SPA (incorrecto, usar Auth Code + PKCE).
- Confiar en token sin validar `aud`/`iss`.

### Token Anatomy & Flujos OAuth / OIDC
| Escenario | Flujo | Nota |
| --- | --- | --- |
| Web server-side | Authorization Code | Cliente confidencial |
| SPA | Auth Code + PKCE | Evita implicit (obsoleto) |
| Daemon / servicio | Client Credentials | No usuario presente |
| API llama otra API | On-Behalf-Of | Requiere token delegados inicial |
| CLI / dispositivo | Device Code | Pantalla separado |

**On-Behalf-Of (OBO)**
- API A recibe token usuario, intercambia por token para API B.
- Necesita `offline_access` y consentimiento para scopes del downstream.

**Ejemplo MSAL (C# Client Credentials)**
```csharp
var app = ConfidentialClientApplicationBuilder.Create(clientId)
  .WithClientSecret(clientSecret)
  .WithAuthority(AzureCloudInstance.AzurePublic, tenantId)
  .Build();
var scopes = new[]{"api://api-app/.default"};
var result = await app.AcquireTokenForClient(scopes).ExecuteAsync();
```

### 3.2 App Service & Functions Authentication (Easy Auth)
- Proveedor configurado en portal (Microsoft, Google, OIDC).
- Modo: permitir anónimo + inyectar claims, o requerir autenticación.
- Cabecera `X-MS-CLIENT-PRINCIPAL` expone identidad.

### 3.3 Azure AD B2C (Conciencia)
- Identidad de cliente (MAU). User flows vs custom policies.
- Soporta MFA, proveedores sociales.

### 3.4 Secrets & Azure Key Vault 🔐
**Objetos**: Secrets, Keys, Certificates.

**Modelos de Acceso**
- Access Policy (granular) vs Azure RBAC (escala, rol Data). Migrar a RBAC para múltiples vaults.

**Rotación**
- Keys: políticas automáticas.
- Secrets: eventos near-expiry + automatización (Functions/Automation) o references.

**Versionado**
- Cada `set` crea versión. Referenciar versión fija para despliegue controlado o última para actualizaciones inmediatas.

**Throttling**
- Excesivo `GetSecret` añade latencia -> cache en memoria / App Configuration reference.

**Comparativa Tiers**
| Feature | Standard Vault | Premium Vault | Managed HSM |
| --- | --- | --- | --- |
| Secrets | Sí | Sí | No |
| Software Keys | Sí | Sí | No |
| HSM Keys | No | Sí (multi-tenant) | Sí (single-tenant) |
| Private Endpoint | Sí | Sí | Sí |
| Modelo Control | Access Policy/RBAC | Access Policy/RBAC | Local RBAC |

**Ejemplo (C# SecretClient)**
```csharp
var credential = new DefaultAzureCredential();
var secretClient = new SecretClient(new Uri("https://kv-demo.vault.azure.net/"), credential);
var secret = await secretClient.GetSecretAsync("SqlPassword");
```

### 3.5 Protección de Datos & Cifrado
- Storage Service Encryption, TDE (SQL), Always Encrypted (columnas sensibles), TLS 1.2, HTTPS Only.
- Row-Level Security, Dynamic Data Masking.

### 3.6 Seguridad de Red
- Private Endpoints (IP privada PaaS), Service Endpoints (ruta pública endurecida), NSG, Application Gateway (WAF), Azure Firewall, Azure Front Door, API Management (políticas JWT, mTLS), network policies AKS.

### 3.7 Secure Coding & Compliance
- Usar `DefaultAzureCredential` / `Microsoft.Identity.Web`.
- Parametrizar SQL / evitar inyección.
- Backoff exponencial (Polly), logging sin secretos.
- Azure Policy para cumplimiento (naming, localización, SKU).

**🧠 Alerta de Examen**
- "No secrets in code" + App Service -> Key Vault reference + Managed Identity.
- Acceso delegable blob granular + identidad -> User Delegation SAS.

**⚠️ Pitfall:** Usar grupos enormes en token (overage) en vez de app roles.

### 3.8 Managed Identities
- System-assigned (ciclo de vida del recurso) vs User-assigned (reutilizable múltiples recursos).
- Compatible con: App Service, Functions, Container Apps, AKS (workload identity), VMs, Logic Apps Standard, Data Factory.
- Código (C#): `new DefaultAzureCredential()`.

### 3.9 RBAC Azure
- Scope jerárquico: Management Group > Subscription > Resource Group > Recurso.
- Roles Built-in vs Custom (JSON `Actions`, `DataActions`).
- Ejemplo asignación CLI: `az role assignment create --assignee <principal> --role "Storage Blob Data Contributor" --scope <id>`.

**Tabla Roles (Ejemplos)**
| Necesidad | Rol |
| --- | --- |
| Lectura blobs | Storage Blob Data Reader |
| Lectura/Escritura blobs | Storage Blob Data Contributor |
| Gestión Key Vault + secretos | Key Vault Administrator / Secrets Officer |
| Lectura Cosmos datos | Cosmos DB Built-in Data Reader |

### 3.10 Microsoft Graph (Delegado & Aplicación)
- Delegated: usuario presente (claim `scp`).
- Application: sin usuario (`roles`).
- Respetar `Retry-After` en 429; batching (`/v1.0/$batch`).

**Ejemplo Graph (C# Delegated)**
```csharp
var scopes = new[]{"User.Read"};
var pca = PublicClientApplicationBuilder.Create(clientId)
  .WithRedirectUri("http://localhost")
  .Build();
var auth = await pca.AcquireTokenInteractive(scopes).ExecuteAsync();
var graph = new GraphServiceClient(new DelegateAuthenticationProvider(r => { r.Headers.Authorization = new AuthenticationHeaderValue("Bearer", auth.AccessToken); return Task.CompletedTask; }));
var me = await graph.Me.Request().GetAsync();
```

**Checklist Práctico Seguridad**
- Registrar app Entra ID + Authorization Code PKCE.
- Implementar On-Behalf-Of en API intermedia.
- Key Vault reference en App Service configurado por identidad administrada.
- Crear private endpoint para Storage y probar acceso restringido.

**Resumen Diferenciadores**
| Requisito | Servicio / Enfoque | Clave |
| --- | --- | --- |
| Acceso blob granular temporal | User Delegation SAS | Identidad + expiración corta |
| Evitar secretos despliegue | Managed Identity | Rotación automática |
| Orquestar flujos OAuth multi-API | OBO flow | Token exchange |
| Cifrado claves HSM dedicadas | Managed HSM | Aislamiento FIPS |
| Limitar API por cuota | APIM policy (rate-limit) | Control inbound |

---

## 4. Monitorización, Diagnóstico y Observabilidad 🛰️

Objetivo: instrumentar, recopilar, correlacionar y reaccionar a telemetría (métricas, logs, traces, eventos) para mantener confiabilidad, rendimiento y coste óptimo.

### 4.1 Application Insights (App Insights)
Componentes clave:
- Requests, Dependencies, Exceptions, Traces, Availability, Performance Counters, Custom Events/Measurements.
- Live Metrics Stream: baja latencia para producción.
- Sampling: Adaptive vs Fixed (reduce volumen preservando distribución estadística).

Instrumentación:
- Auto (ASP.NET Core, Functions, Java) vía SDK.
- Manual: `TelemetryClient.TrackEvent("Checkout", props, metrics);`
- OpenTelemetry Exporter -> App Insights (vendor neutral).

**Estrategias de Sampling**
| Tipo | Cuándo usar | Riesgo |
| --- | --- | --- |
| Fijo (porcentaje) | Carga estable | Sesiones truncadas |
| Adaptativo | Carga variable | Complejidad ajuste |
| Ingest (portal) | Ajuste tardío | Datos ya ingeridos |

**🧠 Alerta de Examen**: Sampling reduce coste, pero para fallos críticos (Exceptions) conviene telemetry processor que fuerce retención completa de errores severos.

### 4.2 Azure Monitor (Métricas & Logs)
Métricas: series temporales numéricas (1 min granular típico). Logs: datos estructurados consultables (KQL) en Log Analytics.

Recolección Logs:
- Plataforma: Activity Log, Diagnostic Settings -> Log Analytics / Event Hub / Storage.
- Aplicación: App Insights / agentes / SDK.

Tipos de Alertas:
- Métrica (evaluación rápida, umbrales estáticos/dinámicos).
- Log (consulta KQL programada, latencia >= 1-5 min).
- Activity (cambios control-plane). 

### 4.3 Kusto Query Language (KQL) Essentials
Patrones frecuentes:
```kusto
requests
| where timestamp > ago(1h)
| summarize avg(duration), count() by bin(timestamp, 5m)
| order by timestamp asc
```
Join dependencias lentas:
```kusto
dependencies
| where duration > 500ms and type == "Http"
| project operation_Id, target, duration
| join kind=inner (requests | project operation_Id, name, success) on operation_Id
| where success == false
```
Percentil:
```kusto
requests | summarize p95=percentile(duration, 95) by bin(timestamp, 10m)
```

**Buenas Prácticas**
- Usar `project` para reducir columnas antes de `join`.
- Index mental: tablas base App Insights (requests, dependencies, traces, exceptions, customEvents, customMetrics, availabilityResults, performanceCounters).

### 4.4 Alertas Efectivas
| Tipo | Ejemplo | Consejo |
| --- | --- | --- |
| Métrica | CPU > 80% 10m | Añadir dimension (InstanceName) |
| Log (KQL) | Error rate > 5% | Normalizar por total requests |
| Activity | Eliminación Key Vault | Gateway para seguridad |
| Service Health | Región degradada | Integrar en runbooks |

Suprimir ruido:
- Dynamic threshold (aprende patrones).
- Action Groups reutilizables (Email, Webhook, ITSM, Logic App, Function).
- Correlación: usar `operation_Id` en KQL para agrupar request + dependencias.

### 4.5 Distributed Tracing & Correlación
Cabeceras estándar W3C Trace Context: `traceparent`, `tracestate`.
- Iniciar trace en el primer borde (API pública).
- Propagar en colas/mensajería: agregar `Diagnostic-Id` o `traceparent` como application property.

**Funciones Durable vs Regular**: Durable gestiona correlación automáticamente (instanceId). Regular Function HTTP -> Queue -> Function: añadir manualmente context en message metadata.

**🧠 Alerta de Examen**: Diferenciar Metric Alert (baja latencia, sin KQL) vs Log Alert (flexible, mayor latencia). Pregunta típica compara ambos.

### 4.6 Troubleshooting Playbook
| Servicio | Síntoma | Pasos |
| --- | --- | --- |
| App Service | Alta latencia | Profiler + revisar cold starts (Functions) + scaling events |
| Functions (Consumption) | Timeouts | Incrementar `functionTimeout` o mover a Premium + warm instances |
| Container Apps | Revs no responden | Ver logs `az containerapp logs show` + revisar autoscaling KEDA triggers |
| AKS | Pod CrashLoop | `kubectl describe pod` + eventos OOM + ajustar requests/limits |
| Service Bus | Mensajes acumulados | Ver `ActiveMessageCount` + scale out consumers + DLQ drain |
| Cosmos DB | 429 (throttling) | Incrementar RU / optimizar índice / particionamiento |

### 4.7 Optimización Coste & Rendimiento
- Reducir retención Logs no críticos (politics Data Collection Rule / Table-level TTL).
- Métricas personalizadas: solo esenciales (p.ej. contadores de dominio). 
- Pre-agregación: enviar métricas agregadas (batch) en vez de eventos granulares.
- Excepciones controladas: no lanzar para flujo normal (reduce ruido y coste ingestion).

### 4.8 Dashboards & Workbooks
- Azure Dashboard: mosaicos multi-servicio (métricas + consultas).
- Workbooks: narrativa interactiva + parámetros + ramas condicionales.
- Exportar consulta recurrente a Function/Logic App para remediación.

**Plantilla Workbook (Secciones Sugeridas)**
1. Ingest Overview
2. Error Budget / SLO
3. Latencia p95/p99
4. Top Failing Dependencies
5. Capacity & RU (Cosmos) / DTU (SQL) / CPU (AKS)
6. Cost Hotspots

**🧠 Alerta de Examen**: RU/s (Cosmos) es métrica por contenedor/DB; DTU/vCore concierne SQL; mezclarlas suele ser distracción en preguntas.

---

## 5. Conectar e Integrar Servicios 🔗

Objetivo: diseñar integración desacoplada, resiliente y escalable usando mensajería, eventos y APIs.

### 5.1 Azure Service Bus
- Protocolos: AMQP 1.0, HTTP fallback.
- Entidades: Queues, Topics (con Subs), Dead-Letter Queue (DLQ), Sessions, Scheduled Messages.
- Filters: SQL, Correlation, Boolean combinables.

Características Clave:
| Feature | Uso | Nota |
| --- | --- | --- |
| Sessions | Orden por clave | Requiere session-enabled queue/topic |
| Dead-letter | Aislar mensajes problemáticos | Inspección manual o proceso automático |
| Duplicate Detection | Idempotencia leve | `MessageId` + ventana temporal |
| Transactions | Atómico send/complete | Dentro misma namespace |
| Deferral | Procesar más tarde | Mantiene orden relativo |

**Ejemplo (C# Envío)**
```csharp
await sender.SendMessageAsync(new ServiceBusMessage(body){ SessionId = orderId, MessageId = Guid.NewGuid().ToString() });
```

**🧠 Alerta de Examen**: Service Bus = enterprise messaging (orden, sesiones, transacciones). Storage Queue = simple, económico, sin topics.

### 5.2 Event Grid
- Modelo push reactivo, baja latencia (~sub-segundos) para eventos discretos.
- Fuentes: Storage Blob, Key Vault, Resource Groups, Custom Topics.
- Handlers: Functions, WebHooks, Logic Apps, Event Hubs, Queue.

Filtrado avanzado:
| Tipo | Ejemplo | Caso |
| --- | --- | --- |
| Subject BeginsWith | `/blobServices/default/containers/images/` | Carpeta lógica |
| Data ContentType | `image/png` | Procesar solo PNG |
| Event Type | `Microsoft.Storage.BlobCreated` | Solo creación |

Retry: 24h exponencial. Dead-letter endpoint opcional (Storage). 

### 5.3 Event Hubs
- Ingestión streaming (telemetría alto volumen). Paralelismo vía Partitions.
- Consumer Groups: vistas independientes de offset.
- Capture automático -> Blob / ADLS para batch/archivado.

Throughput Units (Standard) vs Kafka endpoint (compatibilidad). Dedicated para > 40 MB/s.

### 5.4 Storage Queue vs Service Bus vs Event Grid vs Event Hubs
| Necesidad | Storage Queue | Service Bus | Event Grid | Event Hubs |
| --- | --- | --- | --- | --- |
| Simple FIFO aproximado | ✔️ | Sessions | ❌ | ❌ |
| Pub/Sub | Indirecto (multi-lectores) | ✔️ (Topics) | ✔️ (multi subs) | Consumer Groups (stream) |
| Orden garantizado clave | ❌ | ✔️ (SessionId) | ❌ | Partición (no cross) |
| Transacciones | ❌ | ✔️ | ❌ | ❌ |
| Reintentos push | N/A | Pull | ✔️ (automático) | N/A (pull) |
| Altísimo volumen streaming | ❌ | ❌ | ❌ | ✔️ |
| Enrutamiento selectivo | Básico | Filtros subs | Filtros avanzados | Consumidor aplica |

**🧠 Alerta de Examen**: Event Grid = eventos reactivos (estado cambió). Service Bus = comandos/workflow. Event Hubs = flujo continuo telemetría. Storage Queue = simple desacople económico.

### 5.5 API Management (APIM)
Capas: Inbound -> Backend -> Outbound -> On-Error policies.

Policies comunes:
| Policy | Propósito |
| --- | --- |
| `validate-jwt` | Autenticación/claims |
| `rate-limit-by-key` | Protección cuota consumidor |
| `rewrite-uri` | Versionado limpio |
| `cache-store` / `cache-lookup` | Cache respuesta |
| `set-backend-service` | Enrutamiento multi-backend |

Versioning: Path (`/v2/`), Header, Query param.
Developer Portal: onboarding, suscripciones, keys.

### 5.6 Azure SignalR Service
- Real-time (WebSockets fallback). Escalar broadcast, grupos, usuarios.
- Typical: API (negotiate) + cliente JS -> hub Functions/ASP.NET.

**🧠 Alerta de Examen**: Escenario dashboard tiempo real -> SignalR; no confundir con Event Grid (eventos a handlers, no a navegadores directamente).

### 5.7 Logic Apps
- Designer declarativo, conectores (SaaS/Enterprise), stateful vs stateless.
- Retries automáticos, control flujo (Scopes, Until, ForEach Concurrent).
- Integración con Managed Identity para APIs protegidas.

### 5.8 Webhooks & Retries
Patrones de robustez:
- Validar firma (HMAC) -> integridad.
- Idempotency-Key (header) + store statuses.
- Retry exponencial c/ jitter (Rand[0.8,1.2]).

### 5.9 Patrones de Mensajería
| Patrón | Problema | Solución |
| --- | --- | --- |
| Idempotencia | Duplicados | Store processed IDs + upsert |
| DLQ Reprocess | Mensajes envenenados | Analizar, corregir, reenviar |
| Outbox | Doble escritura DB + mensaje | Transacción local + publicador asíncrono |
| Saga | Transacciones distribuidas | Compensating actions |
| Correlación | Multi-hop tracking | Propagar traceparent |

### 5.10 Matriz Decisión Mensajería
| Criterio | Mejor Opción | Razón |
| --- | --- | --- |
| Evento discreto de sistema | Event Grid | Bajo costo push + filtros |
| Flujo telemetría IoT | Event Hubs | Alto throughput particionado |
| Orquestar workflow empresarial | Service Bus | Sesiones, transacciones |
| Desacoplar simple microservicios | Storage Queue | Simplicidad + coste |
| Notificación navegador | SignalR | Canal persistente |

**🧠 Alerta de Examen**: Pregunta típica mezcla “event” vs “message”. Mensaje = intención/comando (Service Bus). Evento = hecho consumible múltiple (Event Grid). Stream = secuencia ordenada continua (Event Hubs).

**⚠️ Pitfall:** Usar Event Grid para backpressure de alto volumen continuo (debes usar Event Hubs o colas con consumo controlado).

**Checklist Integración**
- Definir contratos (schema) versionados (avro/json) + backward compatibility.
- Establecer política DLQ (monitoreo + alerta).
- Implementar correlación (traceparent) en mensajes.
- Configurar retry con deduplicación (MessageId / Idempotency-Key).
- Segregar tenants vía namespaces/keys (APIM + quotas).

---

## 6. Desplegar y Configurar Infraestructura (Transversal)

### 6.1 Gobernanza & Organización de Recursos
- Resource Groups: agrupación lógica y ciclo de vida. Un recurso solo en un RG.
- Tags: metadatos clave-valor (`Environment=Prod`). Policies `Modify` para aplicar tags faltantes.
- Azure Policy: forzar reglas (localizaciones permitidas, naming, SKUs). Initiative = conjunto de policies.
- Management Groups: jerarquía multi-subscriptions.
- Blueprints (legacy) reemplazado por Template Specs / Azure Verified Modules (AVM).

**🧠 Alerta de Examen**: Policy valida antes/aplica (deny/modify); RBAC controla acceso; confundirse es distracción típica.

### 6.2 Infraestructura como Código (IaC) Patrones
- Parametrización por entorno, no duplicar plantillas.
- Modos despliegue: Incremental vs Complete (complete elimina recursos ausentes).
- Bicep modules para reutilizar (`main.bicep` + `modules/`).
- Deployment Scripts dentro ARM para pasos imperativos puntuales.
- Terraform: remote state en Blob (`backend azurerm`). `terraform import` para adoptar recursos existentes.
- Validación: `what-if`, `az deployment group validate`, `terraform plan`.

**Comparativa Rápida**
| Aspecto | Bicep | Terraform |
| --- | --- | --- |
| Nativo Azure | ✔️ | ❌ (multi-cloud) |
| Estado (state) | No (control plano) | Sí (tfstate) |
| Módulos ecosistema | Creciendo (AVM) | Muy amplio |
| Velocidad nuevas features | Inmediata | Retraso proveedor |

### 6.3 Azure Developer CLI (`azd`)
- Flujo: `azd init` -> `azd up` -> `azd pipeline config` -> `azd monitor`.
- Administra entornos (`.azure/<env>`). Integra código + infraestructura (Bicep/Terraform).
- Plantillas: web + db, functions, container apps.

### 6.4 Control de Código & DevOps
- Estrategias ramas: trunk-based (deploy rápido) vs GitFlow (ramas largas).
- PR validations: build + tests + análisis (CodeQL, SAST).
- Secrets: Key Vault (GitHub Action `azure/keyvault-secrets`). Evitar secrets en variables de pipeline.
- Artefactos: ACR, Azure Artifacts, GitHub Packages.

### 6.5 Testing & Quality Gates
- Unit: xUnit, Jest, PyTest.
- Integración: Azurite (Storage), Cosmos Emulator, Service Bus local (explorer/emuladores 3rd), contenedores Docker.
- Load: Azure Load Testing, k6.
- Security: Dependabot, Trivy, CodeQL.
- Quality Gate: coverage mínimo (ej. 70%), lint sin errores, `terraform plan` sin drift.

**Checklist Práctico Infra**
- Crear módulo Bicep (Storage + Function + App Insights) y desplegarlo vía `azd up`.
- Añadir pipeline GitHub con ambientes (dev/test/prod) y approvals.
- Integrar Key Vault references en App Service (Managed Identity).
- Ejecutar test integración contra emuladores antes de deploy.

---

## 7. Guías de Escenario & Árboles de Decisión

### 7.1 API Serverless con Storage e Identidad
Requisitos: bursts, mínimo mantenimiento, secretos seguros, logging.
Solución:
1. Azure Functions (Consumption/Premium) HTTP trigger.
2. API Management delante (throttling + caching + portal).
3. Key Vault + identidad administrada.
4. Cosmos DB o Azure SQL según relacionalidad.
5. App Insights (telemetría distribuida).
6. CI/CD GitHub Actions + Bicep.
Enfoque examen: diferencia APIM vs proxies Functions, secured secrets, elección DB.

### 7.2 Canal Pedidos Event-Driven
1. Web App publica mensaje Service Bus (SessionId=OrderId).
2. Function ServiceBusTrigger + Durable orchestration invoca APIs downstream.
3. Cosmos DB almacena estado; change feed impulsa actualizaciones en tiempo real.
4. Event Grid notifica externos (status changed).
5. Monitor con KQL errores orquestación.
Foco: locking, sesiones, change feed, orquestaciones durables.

### 7.3 Microservicios Contenerizados AKS
1. AKS CNI, pools múltiples (system/user), autoscaler.
2. ACR Premium + identidad administrada.
3. App Gateway Ingress Controller + WAF.
4. Key Vault CSI driver secretos.
5. GitHub Actions build + push + deploy manifiestos.
Foco: diferencia Container Apps vs AKS (control granular), secretos, networking.

### 7.4 Integración Híbrida Logic Apps
1. Logic App Standard con VNet integration.
2. Gateway on-prem / ISE (legacy) si se requiere.
3. Conectores: SQL, Outlook, Teams, Service Bus.
4. Managed Identity + endpoints privados.
5. Diagnósticos -> Log Analytics.
Foco: diferencia Consumption vs Standard, autenticación conectores.

### 7.5 Lift & Shift Web App
App Service Windows (Standard) + deployment slots + Azure SQL Managed Instance + Key Vault + App Insights.
Foco: elegir tier App Service correcto, integración certificados y DNS.

**🧠 Alerta de Examen**: Container Apps vs AKS: si piden Dapr + auto scale + menor gestión -> Container Apps; si requieren control de red avanzado (CNI granular, DaemonSets) -> AKS.

---

## 8. Plan de Práctica (Hands-on)

| Semana | Foco | Actividades |
| --- | --- | --- |
| 1 | Compute & Deployment | Crear App Service + Functions, slots, Bicep deployment |
| 2 | Storage & Data | Reglas lifecycle Storage, procesador queue, change feed Cosmos, SQL DB con MI |
| 3 | Security & Identity | OAuth en web, managed identities, Key Vault refs, Storage private endpoint |
| 4 | Monitoring & Integration | Alertas App Insights, dashboards KQL, desplegar APIM, flujos Service Bus/Event Grid |
| 5 | Review & Practice | E2E deployment CI/CD, resolver escenarios, practicar preguntas |

Completar mini-labs, documentar resultados y reprocesar áreas débiles.

**🧠 Alerta de Examen**: Preguntas de escenario suelen mapear a combos (Functions + Event Grid + Key Vault + Managed Identity) — reconoce patrones clave.

---

## 9. Escenarios Estilo Examen (Resumen Rápido)
1. **Compute:** Necesitas workloads en contenedores, escalado HTTP y Dapr integrado con control de revisiones. *Respuesta:* Azure Container Apps.
2. **Storage:** Archivar documentos 10 años con legal hold y permitir eliminación tras liberarla. *Respuesta:* Blob immutability (legal hold + time-based retention).
3. **Security:** API llama Microsoft Graph en nombre del usuario tras invocación por SPA. *Respuesta:* Flujo OAuth On-Behalf-Of (`AcquireTokenOnBehalfOf`).
4. **Integration:** Recibir eventos de Resource Group y filtrar por subject. *Respuesta:* Event Grid + Advanced Filters.
5. **Monitoring:** Correlacionar latencia request con dependencias multi-servicio. *Respuesta:* Application Insights distributed tracing (Operation Id).
6. **DevOps:** Forzar naming convention recursos. *Respuesta:* Azure Policy (naming policy).

Revisa cada uno y mapea a secciones previas para reforzar retención.

---

## 10. Tablas de Referencia Rápida

### 10.1 Comparativa Compute ⚙️
| Requisito | App Service | Functions | Container Apps | AKS | ACI |
| --- | --- | --- | --- | --- | --- |
| Hosting PaaS web gestionado | Sí | Limitado (HTTP) | Parcial (ingress microservicios) | No | No |
| Event-driven serverless | No | Sí | Sí (KEDA) | Add-on KEDA | Externo |
| Microservicios con Dapr | No | No | Sí (nativo) | Sí (instalar) | No |
| Control completo SO | No | No | Nivel contenedor | Sí | Contenedor |
| Scale to zero | No | Sí (Cons/Premium) | Sí | No | Sí |
| Networking complejo | Premium/Isolated | Premium/Dedicated | Sí | Sí | Sí (VNet) |

### 10.2 Opciones Storage 📦
| Tipo Dato | Servicio | Claves |
| --- | --- | --- |
| Objetos binarios | Blob Storage | Tiers Hot/Cool/Archive, lifecycle, static site |
| Big Data analytics | ADLS Gen2 | Namespace jerárquico, ACLs |
| Mensajería simple | Queue Storage | Económico, at-least-once |
| Mensajería enterprise | Service Bus | FIFO (sessions), transacciones |
| SMB/NFS shares | Azure Files | Snapshots, AD auth |
| NoSQL documentos | Cosmos DB | Distribución global, baja latencia |
| Relacional | Azure SQL | HA, serverless, TDE |

### 10.3 Flujos Identidad 🔐
| Escenario | Flujo | Notas |
| --- | --- | --- |
| Web app server-side | Authorization Code | Cliente confidencial secret/cert |
| SPA -> API | Auth Code + PKCE | MSAL.js, tokens en memoria |
| Daemon | Client Credentials | Preferir cert |
| API -> API | On-Behalf-Of | `AcquireTokenOnBehalfOf` |
| CLI/Dispositivo | Device Code | Login fuera de banda |

### 10.4 Límites Hosting Functions ⚡
| Plan | Máx Ejecución | Escalado | VNet | Cold Start |
| --- | --- | --- | --- | --- |
| Consumption | 10 min (5 default) | Auto hasta ~200 | No | Posible |
| Premium | Ilimitado | Elástico pre-warmed | Sí | Mínimo |
| Dedicated | Ilimitado | Manual/Autoscale | Sí | Ninguno |

### 10.5 Parámetros Queue Service Bus ✉️
| Propiedad | Default | Nota |
| --- | --- | --- |
| TTL mensaje máx | 14 días | Ajustar `DefaultMessageTimeToLive` |
| Lock duration | 30 s | Extender hasta 5 min |
| Max delivery count | 10 | Luego pasa a DLQ |
| Tamaño cola | 1–80 GB Std / ilimitado Premium | Depende tier |

### 10.6 Cosmos DB Throughput 🌌
| Tamaño Item (KB) | Point Read RU | Write RU | Notas |
| --- | --- | --- | --- |
| 1 | 1 | 5 | Index impacta |
| 4 | 1 | 10 | Mayor tamaño => +RU |
| Query (partition key) | 3–5 | N/A | Filtra por PK |
| Query cross-partition | 15+ | N/A | Evitar si posible |

### 10.7 Mapa Alertas Monitoring 🧪
| Requisito | Alerta Recomendada |
| --- | --- |
| Errores Functions >1% | Log alert (`requests | where success == false`) |
| Throttling Cosmos | Métrica `Throttled Requests` / RU usado |
| CPU App Service >80% | Métrica CPU Percentage |
| Capacidad Storage cerca límite | Métrica Used Capacity |
| Dead-letter Service Bus | Métrica Dead-letter count |

**🧠 Alerta de Examen**: Elegir RU vs DTU vs CPU es pista del servicio implicado.

---

## 11. Chuleta CLI & PowerShell

### Azure CLI Básico
```bash
az login
az account set --subscription "Azure Dev"
az group create --name rg-az204 --location eastus
az deployment group create --resource-group rg-az204 --template-file main.bicep
```

### Comandos Clave por Servicio
- App Service: `az webapp create`, `az webapp deployment slot swap`, `az webapp config appsettings set`
- Functions: `func azure functionapp publish`, `az functionapp create`, `az functionapp config appsettings set`
- Storage: `az storage account create`, `az storage blob upload`, `az storage queue message put`
- Cosmos DB: `az cosmosdb sql container throughput update`, `az cosmosdb restorable-database list`
- Service Bus: `az servicebus namespace create`, `az servicebus queue create`, `az servicebus queue authorization-rule keys list`
- API Management: `az apim create`, `az apim api import`, `az apim api release create`
- Monitoring: `az monitor metrics list`, `az monitor alert create`, `az monitor log-analytics workspace create`

### PowerShell Destacado
```powershell
Connect-AzAccount
New-AzResourceGroup -Name rg-az204 -Location eastus
New-AzStorageAccount -ResourceGroupName rg-az204 -Name staz204demo -SkuName Standard_LRS
Set-AzWebApp -ResourceGroupName rg-az204 -Name contoso-api -AppSettings @{ "KeyVaultReferenceIdentity" = "SystemAssigned" }
```

Usar módulos `Az.*` (Websites, Functions, ServiceBus, Resources, Monitor).

**🧠 Alerta de Examen**: `az deployment group create` despliega a RG; para nivel suscripción usar `az deployment sub create`.

---

## 12. Apéndices 📚

> Referencia rápida: 🧠 crítico examen • 💡 optimización/diseño • ⚠️ errores comunes • 📊 coste • 🔐 seguridad.

### 12.1 Cuotas & Límites Clave (Seleccionado)
| Servicio | Límite (Default) | Notas |
| --- | --- | --- |
| Functions (Consumption) | ~200 instancias | Concurrency depende trigger |
| Tamaño mensaje Service Bus | 256 KB Std / 1 MB Premium | Payload grande -> claim-check |
| TTL máx Service Bus | 14 días | Config en cola/topic |
| Ingress Storage Account | Hasta ~50 Gbps | Varía región & redundancia |
| Partición lógica Cosmos | 20 GB | Reparticionar si se acerca |
| Slots App Service | 0/0/5/20/20 | Free/Shared/Basic/Standard/Premium |
| Revisions Container Apps | 100 | Limpiar antiguas |
| Intentos entrega Event Grid | ~24h (≈25) | Backoff exponencial |
| Node Pools AKS | ~100 | Examen se enfoca en separación roles |

### 12.2 Matriz Decisión (Expandida)
| Escenario | Preocupación | Elegir | Razón |
| --- | --- | --- | --- |
| Cache key-value ultra rápida | Sub-ms | Redis | In-memory |
| Ingesta 1M eventos/min | Throughput | Event Hubs | Particionado |
| Reaccionar a blob upload | Near real-time | Event Grid | Push nativo |
| Workflow negocio approvals | Orquestación | Logic Apps | Conectores |
| Saga compleja codificada | Estado determinista | Durable Functions | Code-first |
| DB global multi-región | <10 ms lectura | Cosmos DB | Replicación multi-region |

### 12.3 Snippets Bicep Comunes
**Key Vault Reference**
```bicep
resource kv 'Microsoft.KeyVault/vaults@2023-02-01' existing = { name: kvName }
output kvUri string = kv.properties.vaultUri
```
**Service Bus Queue**
```bicep
resource sb 'Microsoft.ServiceBus/namespaces@2022-10-01-preview' = {
  name: sbName
  location: location
  sku: { name: 'Standard' tier: 'Standard' }
}
resource queue 'Microsoft.ServiceBus/namespaces/queues@2022-10-01-preview' = {
  name: '${sb.name}/orders'
  properties: { maxDeliveryCount: 10 lockDuration: 'PT45S' }
}
```

### 12.4 Azure Policy (Aplicar Tag)
```json
{
  "properties": {
    "displayName": "Append CostCenter Tag",
    "mode": "All",
    "parameters": { "costCenter": { "type": "String" } },
    "policyRule": {
      "if": { "field": "tags['CostCenter']", "exists": "false" },
      "then": { "effect": "modify", "details": { "operations": [ { "operation": "add", "field": "tags['CostCenter']", "value": "[parameters('costCenter')]" } ] } }
    }
  }
}
```

### 12.5 Patrones KQL (Extendido)
```kql
// Requests lentos correlacionados con dependencias fallidas
dependencyFailures = dependencies | where success == false | project operation_Id, target, type;
requests
| where duration > 1s
| join kind=leftouter dependencyFailures on operation_Id
| summarize fails=countif(success1 == false), avgDur=avg(duration) by operation_Name
| order by fails desc
```

### 12.6 Resiliencia & Manejo Errores
| Tipo Falla | Mitigación | Feature Azure |
| --- | --- | --- |
| Red transitoria | Retry + jitter | SDK / Polly |
| Mensaje venenoso | DLQ tras N intentos | Service Bus DLQ |
| Hot partition Cosmos | Rediseñar partición | Nuevas claves PK |
| Throttling 429 | Backoff exponencial | SDK Cosmos |
| Rotación secreto | Fetch bajo demanda + cache TTL | Key Vault + App Config |

### 12.7 Recetas Código Rápidas
**Blob Upload (Python)**
```python
from azure.identity import DefaultAzureCredential
from azure.storage.blob import BlobClient
credential = DefaultAzureCredential()
blob = BlobClient(account_url="https://staz204.blob.core.windows.net", container_name="images", blob_name="logo.png", credential=credential)
with open("logo.png", "rb") as f:
    blob.upload_blob(f, overwrite=True)
```
**Cosmos CRUD (JS)**
```javascript
const { CosmosClient } = require('@azure/cosmos');
const client = new CosmosClient({ endpoint, key });
const container = client.database('appdb').container('items');
await container.items.create({ id: '1', tenantId: 't1', status: 'new' });
const { resource } = await container.item('1', 't1').read();
```
**Service Bus Send/Receive (C#)**
```csharp
await using var client = new ServiceBusClient(connStr);
ServiceBusSender sender = client.CreateSender("orders");
await sender.SendMessageAsync(new ServiceBusMessage("{ 'id': 1 }") { MessageId = Guid.NewGuid().ToString() });
ServiceBusProcessor proc = client.CreateProcessor("orders", new ServiceBusProcessorOptions { MaxConcurrentCalls = 4, AutoCompleteMessages = false });
proc.ProcessMessageAsync += async args => { await args.CompleteMessageAsync(args.Message); };
proc.ProcessErrorAsync += e => Task.CompletedTask;
await proc.StartProcessingAsync();
```
**Key Vault Secret (Node)**
```javascript
const { DefaultAzureCredential } = require('@azure/identity');
const { SecretClient } = require('@azure/keyvault-secrets');
const credential = new DefaultAzureCredential();
const client = new SecretClient('https://kv-demo.vault.azure.net', credential);
const secret = await client.getSecret('SqlPassword');
```
**Feature Flag (.NET App Configuration)**
```csharp
builder.Configuration.AddAzureAppConfiguration(options => {
  options.Connect(new Uri(appConfigEndpoint), new DefaultAzureCredential())
         .UseFeatureFlags();
});
```

### 12.8 Diferenciadores que Engañan (Examen)
| Servicios Similares | Diferenciador |
| --- | --- |
| Event Grid vs Event Hubs | Notificación reactiva vs stream alto throughput |
| Service Bus vs Storage Queue | Sesiones, topics, transacciones vs simplicidad |
| Functions vs Logic Apps | Code-first vs workflow/connectors |
| App Configuration vs Key Vault | Flags/config vs secretos/keys/certs |
| Private Endpoint vs Service Endpoint | IP privada vs acceso reforzado público |

### 12.9 Profundidad Precios (Resumen) 📊
DISCLAIMER: Verificar portal; examen evalúa comparativos y selección correcta de tier.

#### App Service Plan Tiers
| Tier | Uso Núcleo | Límite Scale-out | Features | Nota |
| --- | --- | --- | --- | --- |
| Free/Shared | Dev/test | Shared | Sin SLA | Entradas básicas |
| Basic | Bajo tráfico dedicado | Por tamaño | SSL, custom domain | Económico |
| Standard | Prod web/API | 10 | Slots (5), backups, autoscale | Default típico |
| Premium v2/v3 | Prod mayor | 30 | Mejor HW, VNet, más memoria | Latencia menor |
| Isolated v2 | Aislamiento | 200 | Single-tenant, compliance | Coste alto |

#### Functions Hosting
| Plan | Facturación | Max Exec | Escala | Caso |
| --- | --- | --- | --- | --- |
| Consumption | Ejecuciones + GB-s | 10 min | Dinámico | Carga impredecible |
| Premium | vCPU+Mem segundos | Ilimitado | Pre-warm elástico | Baja latencia + VNet |
| Dedicated | Plan App Service | Ilimitado | Manual/Autoscale | Consolidación |
| Container Apps | vCPU/Mem + requests | Ilimitado | KEDA | Workloads mixtos |

#### Service Bus Tiers
| Tier | Entidades | Features | Uso |
| --- | --- | --- | --- |
| Basic | Queues | Sin topics/sessions | Simple |
| Standard | Queues+Topics | Sessions, transacciones | Enterprise común |
| Premium | Todo | Dedicado, VNet, latencia estable | Alto throughput |

#### Event Hubs Tiers
| Tier | Unidades | Features | Nota |
| --- | --- | --- | --- |
| Basic | TUs | Sin Capture/Kafka | Simple |
| Standard | TUs | Capture, Kafka | Producción |
| Premium | CUs | Dedicado menos latencia | Crítico |
| Dedicated | Capacity Units | Aislado masivo | Muy alto volumen |

#### Cosmos DB Modos
| Modo | Billing | Fortaleza | Consideración |
| --- | --- | --- | --- |
| Provisioned | RU/s fijado | Predecible | Riesgo sobre-provisión |
| Autoscale | 0–Max rango | Maneja picos | Paga max/hora |
| Serverless | Por RU consumida | Bajos volúmenes | Límites rendimiento |

#### API Management Tiers
| Tier | Escala | Features | Caso |
| --- | --- | --- | --- |
| Consumption | Serverless | Pay per call | Bajo volumen |
| Basic/Standard | Unidades | Núcleo gateway | Producción media |
| Premium | Multi-región, VNet | Híbrido global | Enterprise |
| Isolated | Dedicado | Compliance alto | Regulado |

#### Azure Cache for Redis
| Tier | Features | Caso |
| --- | --- | --- |
| Basic | Single node | Dev/test |
| Standard | Prim/Replica | Prod base |
| Premium | Clustering, persistencia | HA & escala |
| Enterprise | Módulos, active-active | Multi-región |

#### Key Vault Cost Drivers
| Operación | Factura | Nota |
| --- | --- | --- |
| get/set secret | Sí | Cache reduce coste |
| sign/verify key | Sí | HSM más caro |
| list | Sí | Evitar list completos |
| Event notifications | Costo Event Grid | Manejar selectivamente |

#### Quick Wins Coste
| Escenario | Optimización |
| --- | --- |
| Tráfico nocturno bajo Functions | Consumption / escala-in |
| RU/s Cosmos sobre-provision | Autoscale / script ajuste |
| App Service sobredimensionado | Right-size tier menor |
| Acceso secreto frecuente | Cache / reference |
| Logs AKS voluminosos | Ajustar diagnósticos |

**🧠 Alerta de Examen**: Seleccionar el tier mínimo que cumple requisito (e.g. necesidad VNet en mensajería -> Premium; global gateway multi-región -> APIM Premium).

---

## 13. Preguntas de Práctica & Racionales
Cada pregunta incluye la MEJOR respuesta; el racional refuerza el concepto. Nombres de servicios se mantienen en inglés.

**1. (Integration)** Necesitas enrutar ciertos mensajes de un topic de Service Bus a un microservicio de fraude sólo cuando `amount > 5000`. *Respuesta:* Subscription con filtro SQL `amount > 5000`. *Racional:* Filtrado broker-side evita cambios en productores.

**2. (Compute / Functions)** Una Function debe mantener estado entre múltiples llamadas API externas y soportar aprobación manual. *Respuesta:* Durable Functions (human interaction pattern). *Racional:* Orchestrator + external event pausa/reanuda de forma determinista.

**3. (Integration / API)** Requieres transformación por request, rate limiting y versionado para una API existente en Functions. *Respuesta:* API Management. *Racional:* Policies cubren preocupaciones transversales sin redeploy.

**4. (Events)** Reacción near real-time a creación de blobs sin polling. *Respuesta:* Event Grid subscription en Storage account. *Racional:* Eventos push nativos `BlobCreated`.

**5. (Monitoring)** Correlacionar latencia de requests con dependencias en microservicios. *Respuesta:* Application Insights distributed tracing (Operation Id). *Racional:* Misma operación agrupa request + dependencias.

**6. (DevOps)** Forzar naming convention en recursos desplegados. *Respuesta:* Azure Policy (naming). *Racional:* Policy aplica reglas de compliance, no RBAC.

**7. (Security / Identity)** API llama Microsoft Graph en nombre del usuario tras invocación de SPA. *Respuesta:* OAuth On-Behalf-Of (`AcquireTokenOnBehalfOf`). *Racional:* Intercambia token delegado por downstream scopes.

**8. (Messaging / Resiliency)** Procesamiento efectivamente-once de pedidos en cola. *Respuesta:* Consumidor idempotente + llave dedupe. *Racional:* Service Bus es at-least-once; idempotencia elimina duplicados.

**9. (Configuration)** Config dinámica + feature flags sin reinicio. *Respuesta:* Azure App Configuration + feature flags. *Racional:* Almacén central, soporte targeting.

**10. (Monitoring)** Identificar dependencia fallando que dispara p95. *Respuesta:* KQL join `requests` y `dependencies` por `operation_Id`. *Racional:* Correlación precisa.

**11. (Security / Networking)** Exponer microservicios con WAF, path routing y mTLS backend. *Respuesta:* Application Gateway (WAF). *Racional:* L7 gateway con WAF + mTLS.

**12. (Containers)** Canary 5% tráfico para contenedor. *Respuesta:* Azure Container Apps revisions (traffic split). *Racional:* Routing ponderado nativo.

**13. (Containers)** Job nocturno batch contenedor sin gestionar cluster. *Respuesta:* Container Apps Jobs. *Racional:* Serverless programado.

**14. (Security)** Reducir latencia de secretos frecuentes + permitir rotación. *Respuesta:* Cache en memoria + Key Vault reference. *Racional:* Menos round trips, rotación transparente.

**15. (Storage / Analytics)** Append ingest archivos grandes + jerarquía analítica. *Respuesta:* ADLS Gen2. *Racional:* Namespace jerárquico + ACL.

**16. (API Protection)** Limitar 1000 clientes a 100 calls/min cada uno. *Respuesta:* APIM rate-limit policy. *Racional:* Política inbound por key.

**17. (Events)** Necesitas CloudEvents 1.0 para partner. *Respuesta:* Event Grid custom topic. *Racional:* Formato CloudEvents soportado.

**18. (Monitoring / Governance)** Consultar fallos de despliegue multi-suscripción. *Respuesta:* Activity Log (KQL). *Racional:* Control-plane events centralizados.

**19. (Compute)** Reducir cold start en HTTP orquestaciones sensibles a latencia. *Respuesta:* Functions Premium pre-warmed. *Racional:* Instancias siempre calientes.

**20. (DevOps / IaC)** Infra efímera por PR y teardown tras merge. *Respuesta:* Bicep/Terraform módulos + pipeline create/destroy. *Racional:* Reproducibilidad y limpieza automática.

**21. (Compute)** Contenedores sin administración + Dapr pub/sub + scale to zero. *Respuesta:* Azure Container Apps. *Racional:* Dapr integrado y servidorless.

**22. (Functions)** Necesitas baja latencia predecible y ejecuciones largas. *Respuesta:* Functions Premium plan. *Racional:* Quita límite y minimiza cold start.

**23. (Dev Productivity)** Un solo comando para infra + código con plantillas opinadas. *Respuesta:* Azure Developer CLI (`azd`). *Racional:* Orquesta environment + infra + deploy.

**24. (Storage Compliance)** Registros inmutables financieros, retención tiempo + legal hold. *Respuesta:* Blob immutable (time-based + legal hold). *Racional:* WORM cumplimiento.

**25. (Storage Lifecycle)** Política hot->cool 30d, archive 180d, delete 7 años. *Respuesta:* Blob Lifecycle Management. *Racional:* Reglas automáticas.

**26. (Cosmos DB)** Picos 10x ocasionales, minimizar intervención. *Respuesta:* Autoscale provisioned throughput. *Racional:* Escala dentro rango.

**27. (Cosmos DB)** Proyectar cambios a índice de búsqueda. *Respuesta:* Change Feed + processor. *Racional:* Stream incremental.

**28. (Identity)** API acepta cuentas enterprise y personales. *Respuesta:* `common` multi-tenant endpoint. *Racional:* Work/school + MSA.

**29. (Storage Security)** Acceso granular temporal a un blob vía identidad. *Respuesta:* User Delegation SAS. *Racional:* Firmado con Azure AD, no key.

**30. (Secrets)** Evitar secretos en código y permitir rotación para DB. *Respuesta:* Managed Identity + Key Vault secret reference. *Racional:* Sin credencial estática.

**31. (Graph)** Sync nocturno con permisos de aplicación. *Respuesta:* Client Credentials. *Racional:* Sin usuario interactivo.

**32. (Messaging Ordering)** Garantizar orden por cliente. *Respuesta:* Service Bus Sessions. *Racional:* FIFO por SessionId.

**33. (Messaging Routing)** Filtrado por metadata sin cambiar productor. *Respuesta:* Topic subscriptions + SQL filters. *Racional:* Broker rules.

**34. (Events Azure)** Notificación creación Resource Group. *Respuesta:* Event Grid subscription (Azure Subscription events). *Racional:* Eventos sistema.

**35. (Streaming vs Events)** 100k events/s telemetría. *Respuesta:* Event Hubs. *Racional:* Alta ingesta particionada.

**36. (API External)** Portal dev con keys y transformaciones. *Respuesta:* API Management. *Racional:* Gateway + portal + policies.

**37. (Monitoring Analytics)** Top 5 dependencias más lentas 30 min. *Respuesta:* KQL sobre `dependencies` agregando duración. *Racional:* Agregación telemetría.

**38. (Alerting)** Notificar si error rate Functions >5% en 5 min. *Respuesta:* Log alert (KQL) o métrica derivada. *Racional:* Ratio calculado requiere KQL.

**39. (Cosmos Throttling)** 429 en batch nocturno sin cambiar código. *Respuesta:* Elevar RU temporal o configurar autoscale. *Racional:* Capacidad para absorber pico.

**40. (Cost Optimization)** App Service Premium v3 infrautilizado <10% CPU sin necesidad extra. *Respuesta:* Reducir a Standard. *Racional:* Ahorro mismo feature set.

**41. (Idempotency)** Evitar efectos duplicados at-least-once. *Respuesta:* Consumidor idempotente + store processed IDs. *Racional:* Neutraliza redelivery.

**42. (Networking)** Acceso interno privado a App Service. *Respuesta:* Private Endpoint (o Access Restrictions + VNet). *Racional:* IP privada interna.

**43. (Workflow Approval)** Paso humano en orquestación basada en código. *Respuesta:* Durable Functions (external event). *Racional:* Espera estado persistente.

**44. (Canary Containers)** Blue/green 10% sin gestionar AKS. *Respuesta:* Container Apps revisiones. *Racional:* Split nativo.

**45. (CI/CD Environments)** Entorno preview por PR destruido al merge. *Respuesta:* Pipeline IaC create/destroy. *Racional:* Entorno efímero reproducible.

**46. (Feature Flags)** Liberar feature a 5% usuarios. *Respuesta:* App Configuration feature flags (filters). *Racional:* Targeting gradual.

**47. (Key Vault Perf)** Latencia por alto volumen firmas. *Respuesta:* Premium (HSM) o cache key local para no regulado. *Racional:* Menos operaciones remotas.

**48. (Data Lake)** ACL POSIX + jerarquía + analítica. *Respuesta:* ADLS Gen2. *Racional:* ACL granular + integración big data.

**49. (SPA Auth)** Evitar exponer secreto en SPA. *Respuesta:* Auth Code + PKCE. *Racional:* Sustituye implicit inseguro.

**50. (Troubleshooting)** 500s intermitentes bajo picos. Primer paso. *Respuesta:* App Insights Failures + Live Metrics correlación. *Racional:* Aísla rápidamente cause (app vs dependencia).

**🧠 Alerta de Examen**: Cuando la pregunta mezcla “evento” y “mensaje” busca: evento = hecho broadcast (Event Grid); mensaje = comando/routing (Service Bus); stream = telemetría continuo (Event Hubs).