# Introducción a Jenkins

Jenkins es una herramienta de **automatización y orquestación** ampliamente utilizada en entornos de desarrollo de software para implementar procesos de **Integración Continua (CI)** y **Entrega/Despliegue Continuos (CD)**.

Su objetivo principal es automatizar tareas repetitivas dentro del ciclo de vida del software, como la compilación, ejecución de pruebas, análisis de calidad y despliegue de aplicaciones, reduciendo errores humanos y acelerando la entrega de valor.

## ¿Qué es Jenkins?

Jenkins es un **servidor de automatización open source**, escrito en Java, que permite crear pipelines que describen cómo se construye, prueba y despliega una aplicación.

Funciona mediante:

* **Jobs** o tareas automatizadas
* **Pipelines** definidos como código
* Un amplio ecosistema de **plugins** que lo integran con prácticamente cualquier tecnología moderna

## ¿Por qué usar Jenkins?

Jenkins se ha convertido en una herramienta clave en DevOps por los siguientes motivos:

* **Automatización** de procesos repetitivos
* **Integración continua** tras cada cambio en el código
* **Ejecución automática de tests**
* **Despliegues controlados y reproducibles**
* **Gran ecosistema de plugins**
* **Integración con Git, Docker, Kubernetes, cloud providers, etc.**

Todo ello permite detectar errores de forma temprana y mejorar la calidad del software.

## Jenkins dentro de CI/CD

En un flujo típico de CI/CD, Jenkins actúa como el **orquestador central**:

1. Un desarrollador sube cambios al repositorio (Git)
2. Jenkins detecta el cambio mediante un webhook o polling
3. Se ejecuta automáticamente el pipeline:
   * Build
   * Tests
   * Análisis de calidad
   * Empaquetado
   * Despliegue
4. Se notifica el resultado (éxito o fallo)

Este enfoque permite entregar software de forma **rápida, segura y continua**.

## Jenkins como “Pipeline as Code”

Uno de los conceptos clave de Jenkins moderno es **Pipeline as Code**, que permite definir todo el proceso de CI/CD en un archivo versionado (normalmente un `Jenkinsfile`).

Ventajas:

* El pipeline se versiona junto al código
* Cambios auditables y revisables
* Reproducibilidad entre entornos
* Menor dependencia de configuración manual