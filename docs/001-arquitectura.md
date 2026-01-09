# Arquitectura de Jenkins

Comprender la arquitectura de Jenkins es fundamental para poder configurarlo correctamente, escalarlo y operarlo de forma segura en entornos reales. Jenkins sigue un modelo **master-slave** (actualmente denominado **controller–agent**), que separa la gestión central de la ejecución de trabajos.

## Componentes principales

La arquitectura de Jenkins se basa en los siguientes elementos:

* **Controller (antes Master)**
* **Agents (antes Slaves)**
* **Jobs / Pipelines**
* **Plugins**
* **Workspace**

Cada uno cumple un rol específico dentro del sistema.

## Controller (Nodo principal)

El **Controller** es el corazón de Jenkins. Se encarga de:

* Gestionar la configuración global
* Exponer la interfaz web
* Planificar y orquestar la ejecución de jobs
* Asignar trabajos a los agentes disponibles
* Gestionar credenciales, plugins y usuarios

> ⚠️ Buena práctica: el controller **no debería ejecutar builds pesados**, ya que esto puede afectar a la estabilidad y rendimiento del sistema.

## Agents (Nodos de ejecución)

Los **Agents** son los nodos donde se ejecutan realmente los pipelines y jobs.

Características:

* Ejecutan tareas asignadas por el controller
* Pueden ser máquinas físicas, virtuales o contenedores
* Pueden tener diferentes entornos (Java, Node, Docker, etc.)

Tipos comunes de agentes:

* **Estáticos**: máquinas siempre disponibles
* **Dinámicos**: creados bajo demanda (Docker, Kubernetes)

Este enfoque permite **escalar Jenkins horizontalmente**.

## Comunicación Controller–Agent

La comunicación entre el controller y los agents suele realizarse mediante:

* SSH
* JNLP (Java Web Start / inbound agents)

El controller envía las instrucciones y los agents devuelven:

* Logs de ejecución
* Resultados de los pasos
* Artefactos generados

## Jobs y Pipelines

Un **Job** representa una tarea automatizada. Puede ser:

* Freestyle job
* Pipeline
* Multibranch Pipeline

Los **Pipelines** son la forma moderna y recomendada de trabajar en Jenkins, ya que permiten definir el flujo completo como código.

Cada pipeline se compone de:

* Stages
* Steps
* Conditions

## Workspace

El **Workspace** es el directorio donde Jenkins:

* Clona el repositorio
* Ejecuta los comandos del pipeline
* Genera artefactos

Cada job tiene su propio workspace, lo que evita interferencias entre ejecuciones.

## Plugins

Jenkins basa gran parte de su funcionalidad en un sistema de **plugins**.

Los plugins permiten:

* Integración con sistemas de control de versiones (Git)
* Soporte para Docker y Kubernetes
* Notificaciones (Slack, email)
* Gestión de credenciales
* Análisis de calidad de código

> ⚠️ Recomendación: instalar solo los plugins necesarios para reducir riesgos de seguridad y problemas de compatibilidad.

## Arquitectura típica de Jenkins

Un despliegue habitual en producción suele seguir este esquema:

* 1 Controller
* Varios Agents especializados (build, test, deploy)
* Agents efímeros para cargas variables
* Almacenamiento persistente para:

  * Configuración
  * Logs
  * Artefactos

Este modelo permite alta flexibilidad y escalabilidad.

## Jenkins y entornos cloud

En entornos modernos, Jenkins suele integrarse con:

* Docker (agents como contenedores)
* Kubernetes (agents efímeros por pod)
* Cloud providers (autoescalado)

Esto permite optimizar recursos y ejecutar pipelines de forma aislada.
