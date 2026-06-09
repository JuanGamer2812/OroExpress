<div align="center">
  <h1><b>Sistema de Monitoreo SmartBus - IoT</b></h1>
  <p><b>Simulación en Node-RED de rutas y telemetría de buses</b></p>

  <img src="https://img.shields.io/badge/Node--RED-8F0000?style=for-the-badge&logo=node-red&logoColor=white" alt="Node-RED">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript">
  <img src="https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D" alt="Vue.js">
  <img src="https://img.shields.io/badge/Leaflet-199900?style=for-the-badge&logo=leaflet&logoColor=white" alt="Leaflet">
</div>

<br>

Este repositorio contiene un flujo de Node-RED diseñado para simular y visualizar la telemetría de una flota de transporte público en la provincia de El Oro. El sistema modela rutas referenciales que conectan puntos clave como la Terminal Terrestre de Machala, Puerto Bolívar, la Universidad Técnica de Machala (UTMACH), Santa Rosa, Pasaje y El Guabo.

Este desarrollo es un proyecto académico orientado a la automatización local y al diseño de paneles de control operativos. 

> **Nota técnica:** En su etapa actual, este proyecto es una simulación de software. No utiliza conectividad IoT con hardware físico real en los vehículos. Los datos de posicionamiento global (GPS), tiempos estimados de llegada (ETA), niveles de ocupación y variaciones de tráfico son calculados matemáticamente en tiempo real por el motor del flujo.

<hr>

## Características Principales

* **Motor de Simulación en Tiempo Real:** Actualiza la ubicación de cada unidad cada segundo utilizando la fórmula de Haversine para calcular distancias entre paradas.
* **Dashboard Interactivo:** Construido con la librería FlowFuse, presenta una interfaz gráfica con:
  * Mapa en vivo renderizado con Leaflet.js.
  * Panel de control para pausar, reanudar o alterar la velocidad de la simulación.
  * Indicadores clave de rendimiento (KPIs) como ocupación promedio y alertas de retraso.
  * Tabla de telemetría completa exportable a CSV.
* **Sistema de Alertas:** Detección automática de unidades con ocupación crítica (mayor al 92%) o retrasos significativos.
* **APIs Locales Integradas:** Endpoints HTTP disponibles para consumir los datos de la simulación desde clientes externos o aplicaciones como Postman.

## Requisitos Previos

Para ejecutar este flujo en tu entorno local, necesitas tener instalado:
* Node.js (versión LTS recomendada)
* Node-RED
* El nodo `@flowfuse/node-red-dashboard` (versión 1.30.2 o superior)

## Instalación y Despliegue

1. Inicia tu servidor local de Node-RED.
2. Accede a la interfaz del editor (generalmente en `http://localhost:1880`).
3. Dirígete al menú principal (esquina superior derecha) y selecciona **Import**.
4. Pega el contenido del archivo JSON proporcionado en este repositorio.
5. Haz clic en **Deploy** para inicializar el sistema.
6. El panel de control estará disponible en la ruta `/dashboard/buses` (ej. `http://localhost:1880/dashboard/buses`).

## Endpoints de la API Local

<details>
  <summary><b>Haz clic aquí para ver la documentación de los Endpoints</b></summary>
  <br>
  El flujo expone dos rutas HTTP para pruebas de integración:

  **GET `/api/buses/routes`**
  <br>
  Devuelve el catálogo en formato JSON de todas las rutas y paradas configuradas en el sistema.

  **GET `/api/buses/telemetry`**
  <br>
  Devuelve un snapshot en tiempo real con la ubicación exacta, velocidad, estado y ocupación de toda la flota activa.
</details>

<br>

<div align="right">
  <b>Juan Pablo Añazco Lapo, Carlos Enrique Espinoza Cevallos</b><br>
  <i>Estudiantes de Tecnologías de la Información - 6to "B"</i>
</div>
