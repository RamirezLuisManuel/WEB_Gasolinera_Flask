# 1. Descripción General
WEB_Gasolinera_Flask es una herramienta digital diseñada para la localización de estaciones de servicio y gestión de información de combustible. La aplicación permite a los usuarios buscar ciudades o códigos postales para visualizar la ubicación exacta de las sucursales en un mapa interactivo, integrando la API de OpenStreetMap (Nominatim) y la librería Leaflet.js.

# 2. Configuración del Entorno y Creación
Para asegurar un entorno de desarrollo limpio y reproducible, se siguieron estos pasos:

## Creación del directorio raíz

**mkdir flask_gas_app**

**cd flask_gas_app**

## Entorno Virtual
Se aisló el proyecto para la gestión de dependencias:

**python -m venv venv**

## Activación del ambiente

**venv\Scripts\activate**

## Instalación de dependencias
Se instalaron las librerías necesarias para el servidor web y la comunicación con APIs externas:

**pip install flask requests**

# 3. Estructura del Proyecto
El proyecto implementa la arquitectura modular de Flask, organizando los recursos de la siguiente manera:

  flask_gas_app/
  
  ├── app.py              # Núcleo de la aplicación y lógica de rutas
  
  ├── static/             # Recursos estáticos
  
  │   ├── css/            # Hojas de estilo (style.css)
  
  │   └── images/         # Iconos y recursos visuales
  
  └── templates/          # Vistas HTML (Jinja2)
  
    ├── index.html      # Pantalla de bienvenida
    
    └── map.html        # Buscador y mapa interactivo

# 4. Implementación del Backend (Flask)
El archivo app.py actúa como el motor de la aplicación, gestionando peticiones HTTP y la integración con servicios de geolocalización externos.

## Consumo de API Externa
Se utiliza la librería requests para consultar la API de Nominatim, enviando parámetros de búsqueda (q) y recibiendo coordenadas geográficas (latitud y longitud) en formato JSON.

## Lógica de Rutas
Se configuraron rutas dinámicas que inyectan migas de pan (breadcrumbs) para mejorar la navegación del usuario:

**/: Renderiza el inicio.**

**/buscar: Gestiona la búsqueda de locaciones y la visualización del mapa.**

# 5. Frontend y Tecnologías de Interfaz
La interfaz se diseñó para ser intuitiva y funcional, utilizando tecnologías modernas de mapeo.

## Mapa Interactivo (Leaflet.js)
En la vista map.html, se integra la librería Leaflet para renderizar mapas basados en capas de OpenStreetMap (CartoDB Positron). Se implementaron marcadores dinámicos que muestran la estación de servicio encontrada con pop-ups informativos.

## Diseño y Estética

**Breadcrumbs:** Sistema de navegación jerárquica para evitar que el usuario se pierda.

**Feedback Visual:** Implementación de mensajes de error en caso de no encontrar ubicaciones y estilos personalizados mediante style.css.

**Componentes:** Uso de formularios limpios y botones de acción clara (BUSCAR ESTACIONES).

# 6. Proceso de Implementación Paso a Paso

## Paso A: Pantalla de Bienvenida (Index)
Se creó un punto de entrada que establece la identidad visual de la marca (GASStation) y ofrece un acceso directo al servicio principal de búsqueda.

## Paso B: Buscador y Geolocalización
Se implementó un formulario que captura la entrada del usuario y la procesa en el backend para obtener datos geográficos precisos.

## Paso C: Renderizado Dinámico del Mapa
Mediante condicionales de Jinja2 ({% if lat %}), el mapa solo se carga cuando existe una búsqueda exitosa, optimizando el rendimiento de la aplicación.

# 7. Ejecución y Evidencia
Para poner en marcha el servidor de desarrollo:

**python app.py**

**Resultado esperado:** La aplicación estará disponible en http://127.0.0.1:5000.

**Nota Técnica:** El desarrollo se realizó bajo el modo debug=True, facilitando la corrección de errores en tiempo real y la actualización inmediata de los templates modificados.

##  Vista Index
<img src="https://github.com/RamirezLuisManuel/WEB_Gasolinera_Flask/blob/main/static/images/Inicio.png?raw=true" width="400" alt="Vista Index">

## Vista Mapa / Buscador
<img src="https://github.com/RamirezLuisManuel/WEB_Gasolinera_Flask/blob/main/static/images/Mapa.png?raw=true" width="400" alt="Vista Mapa">
