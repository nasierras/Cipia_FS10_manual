# Cipia-FS10 (Manual de Producto)
## Acerca de este manual
### Público objetivo
Este manual del producto está destinado a los equipos de desarrollo de productos, soporte técnico y servicios profesionales dentro de los proveedores de servicios telemáticos (TSP) y los proveedores de plataformas de software, que planean utilizar las capacidades telemáticas de video Cipia-FS10 como parte de su oferta de productos.

### Alcance del documento
Los objetivos principales de este documento son describir el valor, el propósito, la funcionalidad, las características y las interfaces de usuario del dispositivo Cipia-FS10.
### Documentación relacionada
Los siguientes documentos deben usarse junto con este manual para proporcionar a los equipos una imagen completa que cubra el alcance del trabajo, las herramientas y los recursos disponibles y/o necesarios para el proceso de integración exitoso.
- [Manual de Integración Cipia-FS10](01_Cipia-FS10_Integration_Manual_ES.md)
- [Manual de inicio rápido Cipia-FS10 EVK](02_Cipia-FS10_EVK_Start_Guide_ES.md)
- [Descripción de los protocolos OTA de Cipia-FS10](03_Cipia-FS10_OTA_Protocols_Description_ES.md)
- [Descripción de la API de la aplicación del instalador](04_Cipia-FS10_Installer_App_Manual_ES.md)
- [Manual del instalador de la aplicación](05_Cipia-FS10_Installer_App_Manual_ES.md)
- [Documento API de Middleware](06_Cipia-FS10_Middleware_document_ES.md)
- [Manual de protocolo serial Cipia-FS10](07_Cipia-FS10_Serial_Protocol_manual_ES.md)

## Tabla de contenidos
El siguiente manual está distribuido en la siguiente organización:
1. [Acerca de este manual](#Acerca-de-este-manual)
2. [Descripción general de Cipia-FS10](#Descripción-general-de-Cipia-FS10)
3. [Cipia-FS10 Hardware and Interfaces](#Cipia-FS10-hardware-and-interfaces)
   - [Conceptos básicos del dispositivo Cipia-FS10](#Conceptos-básicos-del-dispositivo-Cipia-FS10)
   - [Bloques de construcción del sistema](#Bloques-de-construcción-del-sistema)
   - [Especificación de hardware](#Especificaciones-del-hardware)
   - Cable de instalación y pines
   - Cumplimiento ambiental
   - Certificaciones y estándares de la industria
4. Uso de Cipia-FS10
   - Arquitectura de la solución
   - Estados y modos de operación
   - Características y funciones del modo estándar
   - Aprovisionamiento y mantenimiento de Cipia-FS10
        - Cambios en el archivo de configuración
        - Gestión de archivos de configuración por Cipia-FS10
        - Entorno de depuración
        - Proceso de instalación y calibración
        - Inscripción de identificación de conductor
        - Gestión de archivos de audio
        - Restablecimiento del dispositivo
        - Propiedades del dispositivo
   - Integración con Mobileye 6/8
   - Eventos Cipia-FS10
   - Configuración
   - Interfaces de comunicación
        - Conexión RS232
        - USB
        - Bluetooth
        - Wi-Fi
        - LTE (en inglés)
   - Priorización de canales de comunicación
   - Seguridad de las comunicaciones
        - MQTT
        - SSH
5.	Cipia-FS10 HMI
6.	Kit de prueba y evaluación
7.	Control de errores del sistema
8.	Avisos de normas y reglamentos
    - FCC
    - IC
    - RED

## Descripción general de Cipia-FS10
[Ir al Inicio](#cipia-fs10-manual-de-producto) | [Tabla de contenidos](#Tabla-de-contenidos)

Cipia-FS10 es un dispositivo de videotelemática con capacidades integradas de visión artificial. Está diseñado para mejorar la seguridad del conductor y la flota a través de aplicaciones de videotelemática. El dispositivo Cipia-FS10 detecta la somnolencia del conductor, las distracciones y las acciones peligrosas, proporcionando alertas del conductor en tiempo real, así como alertas e información personalizadas del administrador de flotas a través de su servidor de gestión de flotas.

El dispositivo Cipia-FS10 es un dispositivo en el automóvil que incorpora el motor de software de monitoreo del conductor de Cipia y está destinado a las ventas en el segmento de posventa de gestión de flotas. Los clientes objetivo incluyen proveedores de servicios telemáticos (TSP), distribuidores, revendedores e integradores, así como grandes flotas comerciales con su propia solución telemática.

El sistema tiene recursos de hardware de visión artificial integrados y está destinado a proporcionar capacidades de monitoreo, alerta e informes en tiempo real cuando el conductor está somnoliento, dormido o no está atento a la carretera.

El sistema puede conectarse opcionalmente a un sistema telemático a bordo, u otro dispositivo conectado  en el vehículo, para informar eventos de seguridad en tiempo real a la aplicación de back-end (en caso de que no esté equipado con sus propios recursos de conectividad celular).

Las principales características y funciones del sistema Cipia-FS10 incluyen:
- **Análisis del estado del controlador**
Las capacidades de análisis del estado del controlador Cipia-FS10 incluyen la detección de:
  -	**Distracción del conductor:** basada en la dirección de la mirada y el análisis de otros rasgos faciales, alerta cuando el conductor no está mirando al centro de la carretera. Las alertas se correlacionan con el estado del vehículo (velocidad, marcha, etc.)
  -	**Somnolencia del conductor (fatiga):** informar y alertar cuando el conductor está somnoliento o dormido.
  -	**Uso del teléfono móvil:** alerta cuando el conductor sostiene su teléfono móvil.
  -	**Uso del cigarrillo:** alertar cuando se identifica al conductor como fumador.
  -	**Uso del cinturón de seguridad:** alerta cuando el vehículo se está moviendo pero el conductor no usa el cinturón de seguridad.
- **Detección de identidad del conductor**
Después de un breve proceso de inscripción, que permite agregar un controlador específico a la base de datos del dispositivo, cuando se reconoce un controlador, el sistema informa su ID. Esta información se puede utilizar para las políticas de autenticación de conductores dentro de la flota.

- **A prueba de manipulaciones**
El sistema puede informar cuando la cámara tiene diferentes fallas, como sobreexposición, cámara bloqueada, desconexión de cables, desplazamiento del dispositivo, etc.

- **Informes de eventos de ADAS**
El sistema puede conectarse opcionalmente también a un dispositivo Mobileye, desde el cual puede recibir y analizar varios eventos ADAS que luego pueden analizarse, filtrarse e informarse al servidor para proporcionar una solución completa de seguridad para el conductor y la flota.

- **Captura de vídeo**
Cipia-FS10 permite la captura de vídeo de las siguientes maneras:
   - **De forma autónoma:** active la captura de video del conductor durante unos segundos antes y después de un evento de seguridad detectado por los algoritmos de visión artificial.
   - **Desde el dispositivo conectado:** active la captura de video del conductor durante unos segundos antes y después de un evento de seguridad detectado por un dispositivo conectado.
   - **Comando del servidor (instantáneo):** active la duración predefinida, la captura de video inmediata del controlador una vez que se recibe un comando del backend.
   - **Comando del servidor (DVR):** recupere imágenes del búfer de grabación de video digital en curso en la tarjeta SD, de acuerdo con los marcos de tiempo definidos en el comando.
   - 
- **Métodos de alerta e informes**
Cipia-FS10 informa sobre comportamientos y eventos detectados a:
   - **Conductor:** alertas auditivas (tanto señales como del habla), visuales y/o hápticas (por ejemplo, vibración del asiento o del cinturón de seguridad) al detectar un comportamiento no deseado.
   - **Administrador de flota:** alertas en tiempo real de eventos peligrosos con o sin imágenes de video capturadas alrededor del momento del evento detectado.

## Cipia-FS10 - hardware e interfaces
[Ir al Inicio](#Cipia-FS10-Manual-de-Producto) | [Tabla de Contenidos](#Tabla-de-contenidos)

### Conceptos básicos del dispositivo Cipia-FS10
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Cipia-FS10---hardware-e-interfaces)
<div align="center">
  <img src="images/FS10_device.png" alt="FIG01" width="80%">
  <p align="center"><strong>Fig. 1</strong> - Imagen del dispositivo Cipia-FS10.</p>
</div>

- **Dimensiones** – Las dimensiones del producto son (excluyendo accesorios de montaje) 120mm (L) X 95mm (W) X 30mm. El dispositivo Cipia-FS10 no compromete el campo de visión del conductor de una manera incómoda o ilegal.
- **Peso:** el dispositivo pesa ~390 g, incluido el arnés y el brazo de montaje.
- **Ajuste de la orientación del dispositivo:** el dispositivo tiene un brazo de montaje que permite el movimiento 3D y proporciona la mayor flexibilidad de instalación mientras mantiene la cara del conductor dentro del punto de vista de la cámara. El brazo de montaje se puede bloquear y se puede instalar en la consola o en el parabrisas, utilizando adhesivo de doble cara y/o tornillos. Las cabezas de tornillo especiales son solo para uso profesional.

<div align="center">
  <img src="images/FS10_coordinate_systems.png" alt="FIG02" width="25%">
  <p align="center"><strong>Fig. 2</strong> - Sistema coordenado del dispositivo Cipia-FS10.</p>
</div>

En el diagrama anterior, el eje *x* apunta al controlador.
- **Cable  de instalación:** el cable de instalación está conectado/soldado a la placa interna y sale de la superficie de la carcasa a través de un alivio de tensión de silicona que garantiza la elasticidad y la resistencia contra la tracción. Todos los cables están cubiertos por una sola chaqueta que sale de la carcasa del dispositivo.
- **Cámara y ventana de LED IR:** la carcasa incluye una cubierta transparente IR para la lente de la cámara y los LED IR. La iluminación IR no es visible para el conductor.
- **Cámara externa orientada hacia la carretera:**  Las versiones de Cipia-FS10 Plus admiten la conexión de una cámara orientada hacia adelante (carretera) para monitorear, grabar e informar eventos de la carretera y / o video continuo.

<div align="center">
  <img src="images/FS10_dashcam.png" alt="FIG03" width="30%">
  <p align="center"><strong>Fig. 3</strong> - Cámara delantera para Cipia-FS10 Plus.</p>
</div>

- **Interfaces de usuario:** existen las siguientes interfaces mecánicas para las características de usuario.

<div align="center">
  <img src="images/FS10_parts.png" alt="FIG04" width="80%">
  <p align="center"><strong>Fig. 4</strong> - Interfaz de dispositivo.</p>
</div>

|Interfaz|Descripción|
|--------|-----------|
|Puerta de SD|Tarjetas SIM/SD. Utilizado por técnicos e instaladores durante la instalación o servicio|
|Botón funcional|Activación/ restablecimiento de HW ó activación de eventos|
|LED de conductor|El LED rojo se utiliza para proporcionar retroalimentación visual al conductor|
|Parlante|Para señales audible y alertas|
|Micrófono|Para la grabación de voz de cabina (configurable)|
|LED del Sistema|LED Tricolor para reportar los eventos del sistema|
|Botón de Volumen|Control de volumen (configurable)|
|Puerto USB (micro)|Puerto micro USB para el servicio de depuración y la carga de datos en caso de que los eventos y las secuencias de video no se puedan cargar de forma inalámbrica.|

### Bloques de construcción del sistema
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Cipia-FS10---hardware-e-interfaces)

El siguiente diagrama muestra los principales bloques de construcción, interconexiones e interfaces del dispositivo Cipia-FS10.

<div align="center">
  <img src="images/FS10_blocks.png" alt="FIG05" width="80%">
  <p align="center"><strong>Fig. 5</strong> - Diagrama de bloques interno.</p>
</div>

### Especificación de hardware
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Cipia-FS10---hardware-e-interfaces)

|Componente|Descripción|
|----------|-----------|
|**Núcleo de la plataforma**||
|Procesador principal (SOC)|Ambarella CV25|
|RAM|1GB|
|ROM|8GB|
|Tarjeta de memoria|Ranura para tarjeta Micro SD – Hasta 1TB, exFAT, SDHC/SDXC|
|Perro guardián|- Controlado por SW: para la recuperación de aplicaciones|
| |-HW controlado – para la recuperación del sistema|
|Sensor de movimiento|Acelerómetro 3D / (±16g, 12bit, 100Hz o mejor)|
|Sistema operativo|Linux based|
|**Interfaz del controlador**||
|Botones físicos| - 1 x configurable, multipropósito|
| | +/- Teclas de volumen|
|LEDs| - 1 x Estado del sistema (3 colores)|
| | - 3 x eventos del conductor|
|Micrófono interno|Alta sensibilidad, omnidireccional|
|Bocina interna|Max 85dB @ 1m / 2W, 600Hz ~ 20Khz|
|**Comunicación inalámbrica**||
|Celular| - LTE CAT4|
| | - FDD 1/2/3/4/5/7/8/12/13/17/20/28 (Territorios/aplicaciones no compatibles: Japón, FirstNet)|
| | - GSM 850/900/1800/1900|
| | - WCDMA 1/2/4/5/8 (DC-HSPA+)|
| | - 3FF, Micro SIM (interna)|
|Módulo GNSS| - 50 canales, NMEA 0183, soporte AGPS|
| | - Soporte de sistemas satelitales: GPS, GLONASS, Galileo
|LAN inalámbrica| - Wi-Fi – 802.11 b / g / n / ac,|
| | - Bandas de frecuencia - 2.4G (B1-13) / 5G (B36-165)|
| | - Soporte de modo dual AP y / o Hotspot|
|Bluetooth | BLE V4.2|
|**Cámaras integradas**||
|Hacia el conductor (DMS) | - Sensor de imagen monocromo de 1,2 MP (1280 x 960)|
| |Enfoque fijo. Profundidad de visión 40-111cm min|
| |VOAF: 510, VFOV: 390|
| |Obturador global IR 940nm|
| |30 fps|
| | - F# 2.05|
| | - LEDs IR x 2|
|Orientación a la carretera||
|(Modelos FS10-XXX-ADS)| - 2MP (1920x1280), sensor de imagen de 2.8μ|
| | - Amplio rango dinámico – 120dB|
| | - Excepcional sensibilidad a la luz baja: 0.01Lux|
| | - 30 fps|
| | - F# 2.9|
| | - VOAF: 620, VFOV: 340|
| | - Interfaz física – Conector FAKRA|
| | - Tipo de interfaz FPD-LINK III|
| | - Alimentación: 12 V, ±8 %, pico de 400 mA, AVG de <150 mA|
| | - Carcasa: Aleación de aluminio|
|**Interfaces de comunicación**||
|RS-232| - 1 x RS-232 (Tx, Rx, GND)|
|USB| - 1 x USB 2.0 Dispositivo/host (puerto Micro-USB)|
|**Control de periféricos**||
|GPIO| - 1 x sentido de encendido.|
| | - 1 x entrada (0 – VCC). Digital o analógico.|
| | - 1 x salida de colector abierto.|
| | - 1 x E/S – Totalmente configurable por SW.|
|**Potencia**||
|Potencia de entrada| - Conexión directa de la batería del vehículo (9V-32V)|
| | - Cumple con ISO 7637 y 16750|
|Batería interna| Li-Ion 3.7V / 550mAh - Admite un minuto de funcionalidad completa y apagado ordenado en el corte de energía.|
|Corriente promedio @ inactivo|<3mA @ 12V|
|Corriente media @ activo| - FS10-LOC: <475mA @12V|
| | - FS10-LTE @12V <540 mA|

### Cable de instalación y pines
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Cipia-FS10---hardware-e-interfaces)

El cable de instalación Cipia-FS10 consta de 2 partes:
1. Cable estilo Pigtail de un metro de largo, conectado internamente a la placa principal del dispositivo y con conector automotriz de 10 pines en el extremo.

*****IMAGEN*****

2. Cable de extensión de un metro de largo equipado con un conector automotriz mate y cables abiertos en el extremo.

*****IMAGEN*****

Esta estructura garantiza que los instaladores tengan la máxima flexibilidad en caso de que sea necesario cambiar la configuración de la instalación o corregir el hardware.

La siguiente tabla describe el pinout del dispositivo FS10:
|Pin|Señal|Observación|
|---|-----|-----------|
|1|PWR_IN|Rojo|
|2|PWR_GND|Negro|
|3|PWR_IGN|Morado|
|4|RS232_TxD|Amarillo/Naranja|
|5|RS232_RxD|Gris/Naranja|
|6|COM_GND|Blanco|
|7|GP_IN|Verde|
|8|GP_OUT|Azul|
|9|GP_IO|Gris|
|10|Repuesto|Rojo/Negro|

Para grantizar el mínimo de conexiones para que el Cipia-FS10 funcione, los pines (1), (2) y (3) son requeridos.

### Cumplimiento ambiental
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Cipia-FS10---hardware-e-interfaces)

El dispositivo Cipia-FS10 cumple con los estándares ambientales detallados en la siguiente tabla:

|Variable|Descripción|
|--------|-----------|
|**Rango de temperatura**| - Temperatura de funcionamiento (arranque/funcionamiento): -30 °C a +70 °C|
| | - Continuo (rendimiento completo): -20 °C a +40 °C|
| | - De la batería: -20°C a +60°C|
| | - Almacenamiento: -30 °C a +80 °C|
|**Humedad** | - 95% ±5% HR @ +40°C, sin condensación|
|**IP** | - IP40|
|**Empaquetado** | - ASTM/ ISTA|
|**RoHS** | - RoHS II|
|**REACH/COP** | - Cumple con REACH/POP (Unión Europea)|
|**Minerales de conflicto** |  - Cumple con la ley de minerales de conflicto|
|**Vibración** |  - ISO16750|
|**Choque mecánico** |  - ISO16750|
|**UV** | - Material plástico resistente a los rayos UV|

### Certificaciones y estándares de la industria
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Cipia-FS10---hardware-e-interfaces)

El dispositivo Cipia-FS10 cumple con los siguientes estándares de certificación:
- FCC IDENTIFIER: XMR201903EG25GCE/RED
- IC (Canada Industrial)
- RCM
- E-mark
- RSSC (solo los modelos LTE)
- PTCRB (solo los modelos LTE)
- GCF (solo los modelos LTE)
- IEC62471 (Protección Visual)

## Uso de Cipia-FS10
[Ir al Inicio](#Cipia-FS10-Manual-de-Producto) | [Tabla de Contenidos](#Tabla-de-contenidos)
### Arquitectura de la solución
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Uso-de-Cipia-FS10)
El siguiente diagrama muestra los diversos bloques de construcción e interfaces opcionales del Cipia-FS10 cuando se integra en un entorno de solución telemática
   
### Estados y modos de operación
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Uso-de-Cipia-FS10)
La aplicación Cipia-FS10 tiene tres modos operativos:
1. Modo de instalación y calibración: utilizado durante la instalación por un técnico profesional / certificado.
2. Modo de mantenimiento: utilizado durante debug el mantenimiento por técnicos o ingenieros de aplicaciones de campo.
3. Modo estándar: se utiliza durante el funcionamiento normal del sistema.

En la tabla siguiente se definen los atributos principales de cada uno de estos modos operativos.
El dispositivo Cipia-FS10 mantiene dos indicadores en su memoria no volátil para designar si el dispositivo se instaló profesionalmente y si se calibró. Estos indicadores se establecen/borran de acuerdo con los eventos de transición de modo descritos en el diagrama siguiente y pueden ser consultados por el lado del servidor como parte de la consulta de propiedades del dispositivo (consulte el Manual de integración de Cipia-FS10).

*****IMAGEN*****

Los diferentes modos de operación y atributos per cada uno se detallan en la tabla a continuación.

|Número|Modo|Actividades y atributos|
|------|----|-----------------------|
|1| - Instalación y calibración | - El motor lógico de monitoreo de vehículos y conductores está inactivo.|
| | | - Todos los módulos de comunicación están habilitados independientemente de la configuración de configuración.|
| | | - Adquisición y almacenamiento de ángulos de instalación física para su posterior detección de manipulaciones.|
| | | - Gestión de archivos de configuración por instalador/técnico.|
| | | - Proceso de calibración de la cámara.|
| | | - Inscripción en Face ID.|
|2| - Mantenimiento | - El estado del vehículo y la lógica de supervisión del conductor están activos.|
| | | - Todos los canales de comunicación están habilitados independientemente de la configuración de configuración.|
| | | - Acceso completo a NVM, RAM, SD tarjeta por usuarios autorizados.|
| | | - Acceso completo a los recursos de depuración por parte de usuarios autorizados.|
| | | - Gestión de archivos de configuración local.|
| | | - Inscripción en Face ID.|
| | | - Inyección de vídeo pregrabado.|
| | | - Actualizaciones de la biblioteca, OS/App/DMS.|
|3 | Estándar | - El estado del vehículo y la lógica de supervisión del conductor están activos.|
| | | - El sistema funciona de acuerdo con la configuración del archivo de configuración.|
| | | - Gestión de archivos de configuración desde el servidor a través de protocolos definidos.|

### Características y funciones del modo estándar
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Uso-de-Cipia-FS10)

En la tabla siguiente se enumeran todas las características y funciones compatibles con el
dispositivo Cipia-FS10 en modo de funcionamiento estándar.

|Número|Función|Descripción|
|------|-------|-----------|
|1| Lógica de monitoreo de vehículos y conductores| - El dispositivo Cipia-FS10 supervisa todos los parámetros y condiciones enumerados en la sección Eventos del archivo de configuración y activa eventos cuando se cumplen las condiciones.|
|2| Gestión de eventos en memoria | - Cada evento generado por la aplicación Cipia-FS10 está asociado con un
identificador numérico único y se registra en NVM hasta que se recibe un ACK del GW de comunicación del servidor que indica que el mensaje se recibió correctamente.|
| | - El número máximo de eventos registrados antes de que el sistema comience a anularse se establece en el archivo de configuración.|
|3| ID de viaje Tras la detección de un evento de encendido (Logic Rise de la línea IGN),
o tras la detección de un cambio de conductor sin apagar el motor, el
dispositivo Cipia-FS10 establece un nuevo ID de viaje como el número
del viaje anterior + 1.
Cada evento generado por el dispositivo Cipia-FS10 se envía al backend
FMS con el ID de viaje como parte de la estructura del mensaje.
El ID de viaje es un entero de 3 bytes y se restablece a 0 al alcanzar
D16,777,215.
4 Gestión de datos
del vehículo
La biblioteca DMS utiliza datos del vehículo para activar, desactivar o
adaptar correctamente inattentiveness desatentos.
Si la información del vehículo está disponible, la aplicación principal
informa de los siguientes parámetros a la biblioteca DMS:
• Velocidad del vehículo (desde GPS): cuando los datos GPS no están
disponibles o no están actualizados, o son inexactos (puntuación de
baja calidad), la aplicación principal transfiere un valor acordado que
designa la "velocidad no disponible" a la biblioteca. La aplicación
principal aplica el algoritmo de "detección de movimiento" mientras los
datos GPS no están disponibles y si el vehículo no se mueve,
'velocidad = 0' se informa a la biblioteca para evitar que la biblioteca
informe eventos innecesarios.
• Dirección del vehículo (estado de marcha adelante / marcha atrás):
si el indicador del interruptor de marcha atrás está conectado a una de
las entradas del dispositivo y la entrada está configurada
correctamente como señal de "marcha atrás", cada vez que se detecta
una marcha atrás, los eventos DMS se desactivan.
• Estado del indicador de giro (intermitentes): si el indicador de giro
está conectado a una de las entradas del dispositivo.
• Velocidad de guiñada del vehículo : designa el cambio en el ángulo
de rumbo del vehículo en comparación con el ángulo de rumbo
anterior recibido del receptor GPS, siempre que los datos GPS estén
disponibles y sean precisos.

### Aprovisionamiento y mantenimiento de Cipia-FS10
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Uso-de-Cipia-FS10)

#### Cambios en el archivo de configuración
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Aprovisionamiento-y-mantenimiento-de-Cipia-FS10)

#### Gestión de archivos de configuración por Cipia-FS10
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Aprovisionamiento-y-mantenimiento-de-Cipia-FS10)

#### Entorno de depuración
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Aprovisionamiento-y-mantenimiento-de-Cipia-FS10)

#### Proceso de instalación y calibración
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Aprovisionamiento-y-mantenimiento-de-Cipia-FS10)

#### Inscripción de identificación de conductor
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Aprovisionamiento-y-mantenimiento-de-Cipia-FS10)

#### Gestión de archivos de audio
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Aprovisionamiento-y-mantenimiento-de-Cipia-FS10)

#### Restablecimiento del dispositivo
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Aprovisionamiento-y-mantenimiento-de-Cipia-FS10)

#### Propiedades del dispositivo
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Aprovisionamiento-y-mantenimiento-de-Cipia-FS10)

### Integración con Mobileye 6/8
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Uso-de-Cipia-FS10)

### Eventos Cipia-FS10
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Uso-de-Cipia-FS10)

### Configuración
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Uso-de-Cipia-FS10)

### Interfaces de comunicación
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Uso-de-Cipia-FS10)

#### Conexión RS232
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Interfaces-de-comunicación)

#### USB
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Interfaces-de-comunicación)

#### Bluetooth
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Interfaces-de-comunicación)

#### Wi-Fi
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Interfaces-de-comunicación)

#### LTE (US)
[Tabla de Contenidos](#Tabla-de-contenidos) | [Inicio de sección](#Interfaces-de-comunicación)

### Priorización de canales de comunicación

### Seguridad de las comunicaciones
#### MQTT
#### SSH

## Cipia-FS10 HMI

## Kit de prueba y evaluación

## Control de errores del sistema

## Avisos de normas y reglamentos
### FCC
### IC
### RED





## Licencia
Todos los derechos están reservados por [Cipia Vision Ltd](https://www.cipia.com) formerly Eyesight - 2023.
