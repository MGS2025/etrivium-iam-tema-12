# Tema 12 — Contenido Teórico

> **Título oficial**: Periféricos: conectividad y administración. Elementos de impresión. Elementos de almacenamiento. Elementos de visualización y digitalización.
>
> **Bloque**: Parte II — Técnico
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid
> **Versión**: v1.0 — Pendiente validación
> **Fecha generación**: 2026-07-02
> **Fuentes**: Ver tema-12-fuentes.md · **Diagramas**: Ver tema-12-diagramas.md · **Cambios**: Ver tema-12-changelog.md
>
> *Extensión: ~11.000 palabras · 12 diagramas SVG embebidos · 4 tipos de callout transversales*

---

## Convenciones del documento

Este tema incluye cuatro tipos de **cajas callout** para facilitar el estudio:

> **[DATO CLAVE EXAMEN]** Información de alta densidad memorística, con alta probabilidad de aparecer en el test oficial.

> **[EJERCICIO RESUELTO]** Problema + solución paso a paso (cálculo de capacidad, elección de RAID, dimensionado de una imagen digitalizada…).

> **[EJEMPLO AYTO MADRID]** Aplicación real de la teoría al entorno municipal (puesto de usuario, impresión en red, digitalización de expedientes, archivo electrónico).

> **[REFERENCIA CRUZADA]** Enlace conceptual a otros temas del temario oficial.

Los términos técnicos se mantienen en su nomenclatura habitual (driver, buffer, spooler, RAID, firmware…). Las fuentes se referencian con etiquetas breves tipo `[USB-IF]` o `[NTI-DIGIT]` — el registro completo está en `tema-12-fuentes.md`. Las unidades de medida (Gbps, ppp, W) se glosan la primera vez que aparecen.

---

## 1. Tipología y clasificación de periféricos

### 1.1. Qué es un periférico y su papel en el sistema de información

Un **periférico** es todo dispositivo que se conecta a la unidad central de proceso (la placa base con su CPU y su memoria) para **introducir, extraer, comunicar o almacenar** información, quedando *fuera* del núcleo de cómputo pero al servicio de él [ISO7498]. El prefijo «peri-» (alrededor) describe bien su posición: son los elementos que rodean al procesador y le permiten relacionarse con el mundo exterior y con el usuario.

En el modelo clásico de un sistema informático se distinguen la **unidad central** (CPU, memoria principal y buses internos, tratados en el Tema 11) y las **unidades periféricas**. Sin periféricos, un ordenador sería incapaz de recibir órdenes, mostrar resultados o conservar datos de forma permanente: el teclado, la pantalla, la impresora, el disco y la tarjeta de red son las «manos, ojos y oídos» del sistema.

> **[REFERENCIA CRUZADA]** El **Tema 11** describe la arquitectura del ordenador y sus componentes internos (CPU, memoria, placa base, buses); este **Tema 12** se ocupa de todo lo que se conecta a esa arquitectura desde el exterior. Los buses de comunicación con periféricos y el modelo OSI que enmarca la conectividad se retoman en los temas de comunicaciones (**Tema 33** y **Tema 34**).

### 1.2. Clasificación por función

La clasificación más importante para el examen es la **funcional**, según la dirección del flujo de datos entre el periférico y la unidad central [ISO7498]:

- **Periféricos de entrada**: introducen datos en el sistema. Ejemplos: teclado, ratón, escáner, lector de código de barras, micrófono, webcam, lector de tarjetas, pantalla táctil (en su faceta de captura).
- **Periféricos de salida**: extraen o presentan información procesada. Ejemplos: monitor, impresora, proyector, altavoces, auriculares.
- **Periféricos de entrada/salida (E/S o mixtos)**: combinan ambas funciones. Ejemplos: pantalla táctil, impresora multifunción (imprime y escanea), tarjeta de red, módem, unidades de almacenamiento (leen y escriben).
- **Periféricos de comunicación**: conectan el equipo con otros sistemas o redes. Ejemplos: tarjeta de red (Ethernet o Wi-Fi), módem, router, adaptador Bluetooth.
- **Periféricos de almacenamiento**: conservan datos de forma persistente. Ejemplos: disco duro (HDD), unidad de estado sólido (SSD), memoria USB, grabadora óptica, NAS.

> **[DATO CLAVE EXAMEN]** Un mismo dispositivo puede pertenecer a varias categorías. La **pantalla táctil** y la **impresora multifunción** son de **entrada/salida**; una **unidad de almacenamiento** es de E/S (lee y escribe) y a la vez de almacenamiento. Cuando el examen pida «clasifique», atienda a la función que se destaque en el enunciado.

Otras clasificaciones complementarias:

- **Por su ubicación**: internos (integrados en la caja o la placa: disco interno, tarjeta gráfica) o externos (conectados por un puerto: impresora, escáner).
- **Por su necesidad**: básicos o imprescindibles (teclado, monitor) y complementarios o auxiliares (escáner, webcam).

### 1.3. Periféricos locales, compartidos y en red

- **Periférico local**: conectado directamente a un único equipo por un puerto físico (USB, HDMI).
- **Periférico compartido**: conectado a un equipo que lo comparte con otros a través de la red (una impresora conectada por USB a un PC que la publica).
- **Periférico en red**: dispone de su propia interfaz de red e IP, y es accesible por cualquier equipo autorizado sin depender de un PC intermediario. Las **impresoras de red** y los **NAS** (Network Attached Storage) son los ejemplos típicos.

> **[EJEMPLO AYTO MADRID]** En una oficina de atención al ciudadano de un distrito, cada puesto tiene periféricos **locales** (teclado, monitor, lector de DNI electrónico) y comparte periféricos **en red** (impresoras multifunción departamentales y escáneres de digitalización de expedientes). Este reparto reduce costes de consumibles y facilita la administración centralizada de colas de impresión.

### 1.4. El bus, el controlador y el puerto: cómo dialoga el periférico con el equipo

Para que un periférico funcione intervienen cuatro elementos encadenados:

1. **El puerto**: el conector físico (el «enchufe») donde se inserta el cable o el propio dispositivo.
2. **La interfaz / bus**: el conjunto de líneas eléctricas y reglas de señalización que transportan los datos (USB, PCI Express, SATA). El bus puede ser **serie** (bit a bit por una o pocas líneas: USB, SATA) o **paralelo** (varios bits a la vez: los antiguos puertos LPT/IDE). Hoy predomina el **serie de alta velocidad**, porque evita los problemas de sincronización (*skew*) del paralelo a altas frecuencias.
3. **El controlador de hardware (host controller)**: el circuito de la placa base que gestiona ese bus.
4. **El controlador de software (driver)**: el programa que traduce las órdenes genéricas del sistema operativo al lenguaje concreto del dispositivo (§2.7).

> **[DATO CLAVE EXAMEN]** No confunda **puerto** (conector físico), **interfaz/bus** (reglas y líneas de transmisión) y **controlador**. Y dentro de «controlador» distinga el **host controller** (hardware) del **driver** (software). El examen suele jugar con estos matices.

---

## 2. Conectividad

### 2.1. Interfaces físicas: concepto de puerto e interfaz

Una **interfaz** define cómo se conectan físicamente y cómo se entienden lógicamente dos dispositivos: forma del conector, número de líneas, niveles de tensión, protocolo de señalización y velocidad. La evolución de las interfaces ha ido en una dirección clara: **de paralelo a serie, de específico a universal y de cableado a inalámbrico**, buscando más velocidad, menos cables y conexión en caliente (*hot-plug*).

### 2.2. USB (Universal Serial Bus)

El **USB** [USB-IF] es el bus de conexión de periféricos más extendido. Es **serie**, admite **conexión en caliente** y **Plug & Play**, permite **alimentar** dispositivos por el propio cable y organiza los dispositivos en una topología en estrella (mediante concentradores o *hubs*), con un máximo teórico de 127 dispositivos por controlador.

Conviene separar dos ejes que a menudo se confunden: la **versión** (velocidad y protocolo) y el **conector** (forma física).

**Versiones (velocidad):**

| Versión | Nombre comercial | Velocidad máxima |
|---|---|---|
| USB 2.0 | Hi-Speed | 480 Mbps |
| USB 3.2 Gen 1 | SuperSpeed (5G) | 5 Gbps |
| USB 3.2 Gen 2 | SuperSpeed (10G) | 10 Gbps |
| USB 3.2 Gen 2×2 | SuperSpeed (20G) | 20 Gbps |
| USB4 | USB4 (basado en Thunderbolt 3) | 40 Gbps (hasta 80 Gbps en USB4 v2) |

**Conectores (forma física):** Tipo A (el rectangular clásico), Tipo B (impresoras), Mini y Micro (dispositivos antiguos) y, sobre todo, **USB-C (Tipo C)**: pequeño, **reversible** (da igual la orientación), y capaz de transportar **datos, vídeo (DisplayPort/HDMI en modo alternativo) y energía** por el mismo cable.

> **[DATO CLAVE EXAMEN]** **USB-C es un conector, no una velocidad.** Un puerto USB-C puede ser internamente USB 2.0 o USB4: por fuera son idénticos. No confunda «USB-C» (forma) con «USB4» (protocolo).

**USB Power Delivery (USB PD):** el estándar de entrega de energía sobre USB-C. Negocia dinámicamente la tensión y la corriente entre fuente y consumidor, alcanzando hasta **240 W** en USB PD 3.1, suficiente para cargar portátiles y monitores. Por eso un único cable USB-C puede sustituir al cargador propietario, al cable de vídeo y al de datos.

> **[EJERCICIO RESUELTO]** *¿Cuánto tarda, en el mejor caso teórico, en transferirse un archivo de 4 GB por un puerto USB 2.0 (480 Mbps) frente a uno USB 3.2 Gen 2 (10 Gbps)?* — Convertimos: 4 GB = 32 Gbit (4 × 8). USB 2.0: 32 Gbit ÷ 0,48 Gbps ≈ **66,7 s**. USB 3.2 Gen 2: 32 Gbit ÷ 10 Gbps ≈ **3,2 s**. La diferencia (más de 20×) explica por qué las copias masivas de expedientes exigen puertos modernos. *(En la práctica la velocidad real es menor por la sobrecarga del protocolo y el soporte.)*

### 2.3. HDMI y DisplayPort

Son las dos grandes **interfaces de vídeo y audio digital** para conectar equipos a monitores, televisores y proyectores.

- **HDMI (High-Definition Multimedia Interface)** [HDMI]: dominante en el ámbito de consumo (televisores, consolas, proyectores). Transporta vídeo y audio digital por un mismo cable. HDMI 2.1 admite 4K a 120 Hz y 8K, e incluye canal de retorno de audio (eARC).
- **DisplayPort** [VESA-DP]: estándar abierto de VESA, más habitual en el ámbito profesional e informático. Su gran ventaja es **MST (Multi-Stream Transport)**: permite encadenar varios monitores en serie (*daisy-chain*) desde una sola salida. DisplayPort 2.1 alcanza anchos de banda muy altos (hasta 80 Gbps).

> **[DATO CLAVE EXAMEN]** Diferencie: **HDMI** = consumo/audiovisual, un monitor por puerto; **DisplayPort** = profesional, admite **varios monitores en cadena (MST)**. Ambos son digitales y llevan vídeo + audio. El antiguo **VGA** era analógico (ya en desuso) y el **DVI**, de transición.

### 2.4. Thunderbolt y otros estándares

- **Thunderbolt** [TB]: interfaz de altísimo rendimiento desarrollada por Intel. Desde Thunderbolt 3 utiliza el **conector USB-C** y combina en un único cable **datos (PCIe), vídeo (DisplayPort) y energía**. **Thunderbolt 4** garantiza 40 Gbps, dos pantallas 4K o una 8K, y sirvió de base para el estándar **USB4**. Es la interfaz típica de las **estaciones de acoplamiento (docking stations)**: con un solo cable el portátil obtiene monitores, red, teclado, ratón y carga.
- **eSATA**: versión externa de la interfaz SATA de discos; hoy marginal frente a USB.
- **SAS (Serial Attached SCSI)**: interfaz de discos de servidor, de alta fiabilidad.
- **Puertos heredados**: serie (RS-232, COM) y paralelo (LPT/Centronics) para impresoras y equipos industriales antiguos; **PS/2** para teclado y ratón. Se mantienen por compatibilidad en algunos equipos, pero han sido desplazados por USB.

### 2.5. Conectividad inalámbrica: Bluetooth y Wi-Fi

La conexión sin cables se apoya en dos grandes familias, que se diferencian por su **alcance** y su **propósito**:

- **Bluetooth** [BT-SIG]: red inalámbrica de **área personal (WPAN)**, de **corto alcance** (típicamente hasta 10 m en clase 2), en la banda de 2,4 GHz. Diseñada para conectar periféricos cercanos: teclado, ratón, auriculares, altavoces, impresoras. Forma redes *ad hoc* llamadas **piconets**. La variante **BLE (Bluetooth Low Energy)** minimiza el consumo, clave en dispositivos a pilas y en el Internet de las Cosas (IoT). Las versiones 5.x mejoran alcance y velocidad, y **LE Audio** moderniza el audio inalámbrico.
- **Wi-Fi** [IEEE802.11]: red inalámbrica de **área local (WLAN)**, definida por la familia de normas **IEEE 802.11**, pensada para dar acceso a la red y a Internet con mayor alcance y velocidad. Trabaja en las bandas de 2,4 GHz, 5 GHz y 6 GHz:

| Generación | Norma | Banda | Notas |
|---|---|---|---|
| Wi-Fi 4 | 802.11n | 2,4 / 5 GHz | Introduce MIMO |
| Wi-Fi 5 | 802.11ac | 5 GHz | Mayor velocidad, MU-MIMO |
| Wi-Fi 6 | 802.11ax | 2,4 / 5 GHz | Eficiencia en entornos densos (OFDMA) |
| Wi-Fi 6E | 802.11ax | + 6 GHz | Amplía a la banda de 6 GHz |
| Wi-Fi 7 | 802.11be | 2,4 / 5 / 6 GHz | Multi-Link Operation, canales de 320 MHz |

> **[DATO CLAVE EXAMEN]** **Bluetooth = WPAN, corto alcance, periféricos personales; Wi-Fi = WLAN, acceso a red, mayor alcance.** Ambos comparten la banda de 2,4 GHz (de ahí posibles interferencias). La seguridad Wi-Fi se cifra con **WPA2** y **WPA3** (este último obligatorio en entornos que exijan alta seguridad).

### 2.6. Tecnologías inalámbricas emergentes

- **NFC (Near Field Communication)**: comunicación de campo cercano a 13,56 MHz y **muy corto alcance (< 4 cm)**. Usos: pagos con móvil, validación de tarjetas de transporte, emparejamiento rápido de dispositivos.
- **UWB (Ultra-Wideband)**: banda ultraancha, ideal para **localización de precisión** (etiquetas, «buscar mi dispositivo», apertura de vehículos).
- **Thread y Matter**: protocolos del hogar/edificio inteligente. **Matter** es el estándar de interoperabilidad que unifica dispositivos IoT de distintos fabricantes; **Thread** es la red de malla de baja potencia sobre la que suele funcionar.
- **Zigbee y Z-Wave**: redes de malla de bajo consumo para domótica y sensores.

### 2.7. Protocolos y controladores: drivers y compatibilidad

Un **controlador de dispositivo (driver)** [MS-DEVMGR] es el software que actúa de **traductor** entre el sistema operativo y el hardware concreto del periférico. El sistema operativo emite órdenes genéricas («imprime esta página», «lee este sector») y el driver las convierte en las señales específicas que ese modelo de impresora o disco entiende. Sin el driver adecuado, el dispositivo no funciona o lo hace en modo genérico limitado.

Tipos y conceptos clave:

- **Driver genérico vs específico**: el sistema incluye drivers genéricos (clase) que dan funcionalidad básica (una memoria USB como «dispositivo de almacenamiento masivo»); el driver del fabricante desbloquea todas las funciones.
- **Firmware**: software grabado en el propio periférico que controla su electrónica interna. Se actualiza para corregir fallos o añadir funciones.
- **Compatibilidad**: un driver se desarrolla para un sistema operativo y arquitectura concretos (Windows x64, Linux, macOS). La falta de driver para una versión de SO es causa frecuente de que un periférico antiguo deje de funcionar tras una actualización.
- **Firma de controladores (driver signing)**: los sistemas modernos exigen que los drivers estén **firmados digitalmente** por el fabricante, para garantizar su origen e integridad y evitar código malicioso en el núcleo del sistema.

> **[REFERENCIA CRUZADA]** La instalación, actualización y mantenimiento de los controladores como parte de la administración del sistema operativo se desarrolla en el **Tema 27** (Administración del sistema operativo y software de base). Los sistemas operativos concretos (Windows, Linux) que gestionan estos drivers son objeto del **Tema 14**.

### 2.8. Plug & Play y gestión automática de dispositivos

**Plug & Play (PnP)** [MS-DEVMGR] es la capacidad del sistema para **detectar, identificar y configurar automáticamente** un dispositivo al conectarlo, sin intervención manual del usuario. El proceso típico es:

1. **Detección**: al conectar el dispositivo, el bus (p. ej. USB) genera un evento y el sistema detecta el nuevo hardware.
2. **Identificación**: el dispositivo comunica sus identificadores de fabricante y producto (VID/PID) y su clase.
3. **Asignación de recursos**: el sistema le asigna los recursos necesarios (direcciones, interrupciones) evitando conflictos.
4. **Carga del driver**: el sistema busca el driver adecuado —local, en Windows Update o en el repositorio de la distribución Linux— y lo carga.
5. **Disponibilidad**: el dispositivo queda listo para usarse.

En Linux este cometido lo cumplen el subsistema **udev** y **sysfs**, que crean automáticamente los nodos de dispositivo y aplican reglas. En Windows lo hace el gestor **PnP** con el **Administrador de dispositivos**.

> **[DATO CLAVE EXAMEN]** Plug & Play = detección + identificación + configuración **automáticas**. No lo confunda con **hot-plug** (conexión y desconexión «en caliente», con el equipo encendido), aunque suelen ir juntos: USB es a la vez PnP y hot-plug.

---

## 3. Administración de periféricos

### 3.1. Configuración del sistema: instalación de dispositivos

Instalar un periférico consiste en conectarlo, dotar al sistema del **driver** correcto y **configurarlo** (parámetros, permisos, valores por defecto). Con PnP, muchos dispositivos quedan operativos al conectarlos; otros (impresoras de red, escáneres profesionales) requieren instalar software del fabricante y definir su dirección o cola.

- En **Windows**, la instalación se apoya en el **Administrador de dispositivos** y en **Windows Update**, que descarga controladores automáticamente [MS-DEVMGR].
- En **Linux**, la mayoría de drivers están incluidos en el propio **kernel** o se instalan como módulos; la impresión se gestiona con **CUPS** y el escaneo con **SANE** [LINUX-UDEV].

### 3.2. Paneles de control y utilidades

Cada sistema ofrece herramientas para ver y administrar los periféricos:

| Función | Windows | Linux |
|---|---|---|
| Ver/gestionar hardware | Administrador de dispositivos | `lsusb`, `lspci`, `lshw`, sysfs |
| Configuración general | Configuración / Panel de control | Herramientas del entorno de escritorio |
| Impresión | Dispositivos e impresoras | CUPS (interfaz web `localhost:631`) |
| Escaneo | Software del fabricante / Fax y Escáner | SANE (`scanimage`, `simple-scan`) |
| Discos y particiones | Administración de discos | `fdisk`, `parted`, `gparted`, `lsblk` |

> **[EJEMPLO AYTO MADRID]** En un parque de cientos de equipos, la instalación no se hace máquina por máquina: se usan **directivas de grupo (GPO)** y herramientas de despliegue centralizado para instalar impresoras de red, distribuir drivers firmados y fijar la configuración (impresora por defecto del distrito, doble cara y blanco y negro para ahorrar consumibles). Así se garantiza homogeneidad y control.

### 3.3. Gestión y mantenimiento: actualización de controladores

Mantener los drivers al día corrige fallos, mejora el rendimiento y **cierra vulnerabilidades de seguridad**. La actualización puede ser:

- **Automática**: mediante Windows Update o el gestor de paquetes de Linux.
- **Manual**: descargando el controlador del sitio del fabricante (necesario para hardware especializado o muy nuevo).

Buenas prácticas: usar solo **drivers firmados**, mantener un punto de restauración antes de cambios delicados y actualizar también el **firmware** de impresoras, escáneres y controladoras de disco cuando el fabricante publique correcciones.

> **[REFERENCIA CRUZADA]** El diagnóstico de incidencias del puesto de usuario y su resolución (incluida la asistencia remota) se tratan con detalle en el **Tema 29** (Control remoto de puesto de usuario y gestión de la resolución de incidencias).

### 3.4. Diagnóstico y resolución de problemas

Un método ordenado ante un periférico que falla:

1. **Comprobar lo físico**: cable, puerto, alimentación, LED de estado. Muchos fallos son un cable suelto o un puerto averiado.
2. **Verificar el sistema**: ¿aparece el dispositivo en el Administrador de dispositivos o en `lsusb`? Un dispositivo desconocido o con un aviso indica problema de driver.
3. **Revisar el driver**: reinstalar, actualizar o revertir (*rollback*) a la versión anterior si el problema surgió tras una actualización.
4. **Consultar registros**: el visor de eventos de Windows o `dmesg`/journalctl en Linux muestran los mensajes del sistema al conectar el dispositivo.
5. **Aislar**: probar el periférico en otro equipo (¿falla el dispositivo o el equipo?) y otro dispositivo en el mismo puerto.
6. **Conflictos de recursos** o compatibilidad de versión de SO como últimas hipótesis.

> **[DATO CLAVE EXAMEN]** El diagnóstico va **de lo físico y sencillo a lo lógico y complejo**: primero cable y alimentación, después driver y sistema. Empezar reinstalando el sistema operativo ante un cable suelto es el error clásico.

### 3.5. Seguridad en dispositivos: control de accesos

Los periféricos son una **vía de entrada y salida de datos** y, por tanto, un vector de riesgo. El control de accesos busca que **solo dispositivos y usuarios autorizados** interactúen con el sistema:

- **Control de puertos y dispositivos**: políticas que permiten o bloquean el uso de puertos USB y clases de dispositivos (por ejemplo, impedir memorias USB en puestos sensibles).
- **Autenticación de usuario** antes de usar recursos compartidos (impresión con liberación por tarjeta o PIN, *pull printing*).
- **Listas blancas de dispositivos**: solo se admiten los periféricos previamente autorizados por su identificador.

### 3.6. Protección frente a amenazas

- **BadUSB y dispositivos maliciosos**: un USB puede simular ser un teclado y ejecutar comandos, o transportar malware. Mitigación: deshabilitar el autoarranque, controlar clases de dispositivo y usar antivirus con análisis de soportes extraíbles.
- **Fuga de información (DLP, Data Loss Prevention)**: soluciones que impiden copiar datos sensibles a soportes externos o los cifran automáticamente.
- **Cifrado de soportes**: **BitLocker** (Windows) y **LUKS** (Linux) cifran discos y memorias, de modo que un soporte perdido o robado sea ilegible [MS-DEVMGR][ENS].
- **Borrado seguro**: al retirar un disco, se sobrescribe o destruye para que los datos no sean recuperables.

> **[EJEMPLO AYTO MADRID]** El **Esquema Nacional de Seguridad** [ENS] obliga a proteger los soportes de información que contienen datos personales de la ciudadanía. En la práctica: los portátiles municipales se cifran con BitLocker, las memorias USB no autorizadas se bloquean por política, y los discos de equipos que se dan de baja se someten a **borrado seguro** o destrucción física certificada antes de su retirada.

> **[REFERENCIA CRUZADA]** Los conceptos generales de seguridad de los sistemas de información (amenazas, criptografía, firma digital) se desarrollan en el **Tema 32**, y la protección de la confidencialidad y disponibilidad en el puesto de usuario en el **Tema 25**.

---

## 4. Elementos de impresión

### 4.1. Impresión convencional: tecnologías

Una **impresora** es un periférico de salida que plasma sobre un soporte físico (normalmente papel) la información generada por el equipo. Las tecnologías principales [HP-PRINT]:

- **Láser**: un haz láser dibuja la imagen sobre un tambor fotoconductor cargado eléctricamente; el **tóner** (polvo) se adhiere a las zonas marcadas y se **fija al papel por calor y presión** (fusor). Ventajas: alta **velocidad**, bajo coste por página y texto nítido. Ideal para volúmenes altos de documentos.
- **Inyección de tinta (inkjet)**: un cabezal proyecta **gotas microscópicas de tinta** líquida sobre el papel. Ventajas: excelente reproducción del color y de fotografías, equipos económicos. Inconvenientes: mayor coste por página y cabezales que pueden secarse.
- **Matricial (de impacto)**: una cabeza con agujas golpea una cinta entintada contra el papel. Obsoleta salvo donde se necesita **copia por presión** (papel autocopiativo, formularios continuos multicopia).
- **Térmica**: aplica calor sobre papel termosensible (tickets, etiquetas) o transfiere tinta de una cinta por calor (transferencia térmica).

> **[DATO CLAVE EXAMEN]** **Láser** = tóner + fusión por calor, rápida, para documentos; **inyección** = tinta líquida en gotas, mejor color/foto; **matricial** = impacto, única que hace copia por presión; **térmica** = calor sobre papel especial, tickets y etiquetas.

### 4.2. Tipos de consumibles

- **Tóner**: cartucho de polvo para láser. Alto rendimiento (miles de páginas).
- **Cartuchos de tinta**: depósitos líquidos para inyección; los sistemas de **tanque recargable** reducen mucho el coste por página.
- **Cabezal de impresión**: en inyección puede ir integrado en el cartucho o ser una pieza permanente.
- **Papel y otros soportes**: distintos gramajes, tamaños (A4, A3), etiquetas, transparencias.
- **Tambor, fusor y cinta**: piezas de mantenimiento de las láser y matriciales.

El **coste por página (CPP)** y el **rendimiento del consumible** son los criterios económicos que guían la elección en un parque grande.

### 4.3. Impresión en red y lenguajes de descripción de página

Una **impresora en red** dispone de su propia IP y es accesible por muchos equipos. Elementos clave:

- **Servidor de impresión y cola (spooler)**: recibe los trabajos, los pone en **cola** y los envía a la impresora en orden, liberando enseguida la aplicación del usuario. Gestiona prioridades, pausas y reintentos.
- **Protocolos de impresión**: **IPP (Internet Printing Protocol)**, el estándar moderno (base de AirPrint y de la impresión sin driver), y los antiguos LPD/LPR y puerto RAW 9100.
- **Lenguajes de descripción de página (PDL)**: describen la página de forma independiente del papel concreto. Los principales son **PostScript** (Adobe, independiente del dispositivo, potente en artes gráficas), **PCL** (HP, muy extendido en ofimática) y, cada vez más, **PDF** directo [HP-PRINT][ISO32000].

> **[EJEMPLO AYTO MADRID]** En las dependencias municipales predominan **impresoras multifunción en red** con impresión segura por liberación (*pull printing*): el usuario envía el trabajo, la cola lo retiene y el documento solo se imprime cuando el usuario se identifica con su tarjeta en el equipo. Así se evita que documentos con datos personales queden olvidados en la bandeja y se reduce el desperdicio de papel y tóner.

### 4.4. Impresión 3D

La **impresión 3D** o **fabricación aditiva** construye objetos físicos **capa a capa** a partir de un modelo digital [ISO3664]. Frente a la fabricación sustractiva (que quita material), la aditiva **añade** material solo donde hace falta. Tecnologías principales:

- **FDM (Modelado por Deposición Fundida)**: deposita **filamento termoplástico fundido** capa a capa. Es la más común y económica.
- **SLA (Estereolitografía)**: solidifica **resina líquida** con un láser o luz UV. Gran precisión y acabado.
- **SLS (Sinterizado Selectivo por Láser)**: un láser **sinteriza (funde parcialmente) polvo** (plástico o metal). Permite geometrías complejas sin soportes.

El flujo típico: modelo 3D (CAD) → **laminado (slicing)** en capas → generación de instrucciones (código G) → impresión. Aplicaciones en la Administración: prototipado, señalética, piezas de repuesto y accesibilidad (maquetas táctiles, reproducciones para museos municipales).

---

## 5. Elementos de almacenamiento

### 5.1. Tipos de dispositivos: magnéticos, ópticos y de estado sólido

El **almacenamiento secundario** conserva los datos de forma **persistente** (a diferencia de la memoria RAM, volátil). Se clasifica por la tecnología de grabación:

- **Magnéticos**: graban la información como polaridades magnéticas.
  - **Disco duro (HDD)**: platos rígidos que giran mientras un cabezal lee/escribe. Gran capacidad a bajo coste; más lento y sensible a golpes por tener partes móviles.
  - **Cinta magnética**: soporte secuencial de altísima capacidad y bajo coste, usado para **copias de seguridad y archivo a largo plazo** (LTO).
- **Ópticos**: leen y graban con un **láser** [ISO9660].
  - **CD** (~700 MB), **DVD** (4,7 GB una capa), **Blu-ray** (25-100 GB). En retroceso frente al almacenamiento en red y la nube.
- **Estado sólido (SSD)**: memoria **flash NAND**, **sin partes móviles**. Mucho más rápido, silencioso y resistente que un HDD; menor capacidad por euro. Se conecta por SATA o, para máximo rendimiento, por **NVMe sobre PCIe** (formato M.2).
- **Memorias flash extraíbles**: memorias USB (*pendrives*) y tarjetas SD/microSD, basadas también en flash NAND.

> **[DATO CLAVE EXAMEN]** **HDD** = magnético, partes móviles, mucha capacidad barata, más lento. **SSD** = flash, sin partes móviles, muy rápido, más caro por GB. El **SSD NVMe** (PCIe) es mucho más rápido que el **SSD SATA**. La **cinta** sigue siendo el rey del archivo masivo a largo plazo por su coste por TB.

### 5.2. Tecnologías y formatos: interfaces y capacidades

Las **interfaces de almacenamiento** conectan el soporte con el equipo:

- **SATA**: interfaz estándar de discos internos (HDD y SSD 2,5"), hasta 6 Gbps.
- **NVMe (PCIe)**: protocolo de alto rendimiento para SSD, aprovecha el paralelismo de la memoria flash; velocidades de varios GB/s.
- **SAS**: interfaz de discos de servidor, fiable y con doble puerto.
- **USB**: para soportes externos.

Las **capacidades** se miden en múltiplos del byte. Conviene recordar la diferencia entre prefijos **decimales** (SI: 1 TB = 10¹² bytes, usados por los fabricantes) y **binarios** (1 TiB = 2⁴⁰ bytes, usados por muchos sistemas operativos): por eso un disco «de 1 TB» aparece como ~931 GiB en el sistema.

### 5.3. Sistemas de archivos

Un **sistema de archivos (file system)** es la estructura lógica que **organiza los datos** en el soporte: cómo se nombran, se localizan (directorios) y se controla el espacio libre y los permisos [APFS-NTFS]. Los principales:

| Sistema de archivos | Ámbito | Notas |
|---|---|---|
| **FAT32** | Universal | Muy compatible; límite de **4 GB por archivo** |
| **exFAT** | Extraíbles | Sucesor de FAT32 sin el límite de 4 GB; ideal para USB/SD grandes |
| **NTFS** | Windows | Permisos, cifrado (EFS), *journaling*, cuotas |
| **ext4** | Linux | Sistema estándar de Linux, con *journaling* |
| **APFS** | macOS | Optimizado para SSD, instantáneas |
| **ISO 9660 / UDF** | Ópticos | Discos CD/DVD/Blu-ray |

> **[DATO CLAVE EXAMEN]** **FAT32** es el más compatible pero **no admite archivos mayores de 4 GB**; para soportes extraíbles grandes se usa **exFAT**. **NTFS** aporta **permisos y journaling** en Windows; **ext4** es el equivalente en Linux. El *journaling* (registro por diario) permite recuperar la coherencia del sistema tras un corte de energía.

### 5.4. Gestión del almacenamiento: particionado y formateo

- **Particionar** es dividir un disco físico en varias unidades lógicas independientes. Dos esquemas de tabla de particiones:
  - **MBR (Master Boot Record)**: heredado; máximo **2 TB** y 4 particiones primarias.
  - **GPT (GUID Partition Table)** [UEFI-GPT]: moderno, asociado a **UEFI**, sin el límite de 2 TB y con muchas particiones. Es el estándar actual.
- **Formatear** es crear en la partición la estructura de un sistema de archivos concreto, dejándola lista para almacenar datos. El **formateo rápido** solo reinicia las tablas de asignación; el **formateo completo** además verifica el soporte.

> **[EJERCICIO RESUELTO]** *Una unidad de red del Ayuntamiento debe guardar imágenes TIFF de expedientes de hasta 6 GB por archivo y ser accesible desde equipos Windows y Linux. ¿Qué sistema de archivos NO serviría y por qué?* — **FAT32 no serviría**, porque no admite archivos de más de 4 GB. Servirían **exFAT** (extraíbles) o, en un servidor, **NTFS**/**ext4**. Para un recurso de red compartido lo habitual es un servidor con NTFS o ext4 y acceso por protocolo de red (SMB/NFS).

### 5.5. Copias de seguridad

Una **copia de seguridad (backup)** es un duplicado de los datos que permite **restaurarlos** tras un borrado, avería, ataque (*ransomware*) o desastre. Tipos:

- **Completa (full)**: copia todos los datos. Restauración simple; ocupa y tarda más.
- **Incremental**: copia solo lo cambiado **desde la última copia** (completa o incremental). Rápida y ligera; para restaurar hace falta la completa y **toda** la cadena de incrementales.
- **Diferencial**: copia lo cambiado **desde la última copia completa**. Restauración con solo dos piezas (completa + última diferencial); ocupa más que la incremental.

Métricas de referencia: **RPO (Recovery Point Objective)**, cuántos datos se está dispuesto a perder (frecuencia de copia), y **RTO (Recovery Time Objective)**, en cuánto tiempo hay que restaurar el servicio.

> **[DATO CLAVE EXAMEN]** Regla **3-2-1**: mantener **3 copias** de los datos, en **2 tipos de soporte** distintos, con **1 copia fuera** de las instalaciones (*offsite*). Una copia que nunca se ha probado a restaurar no es una copia fiable: hay que **verificar las restauraciones** periódicamente.

> **[REFERENCIA CRUZADA]** Los sistemas de almacenamiento corporativos, su virtualización y las políticas y procedimientos de backup y recuperación (incluidos entornos físicos y virtuales) se desarrollan en el **Tema 26**.

### 5.6. Sistemas de protección y redundancia (RAID)

**RAID (Redundant Array of Independent Disks)** combina varios discos para lograr **más rendimiento, más capacidad y/o tolerancia a fallos** [SNIA-RAID]. Los niveles más preguntados:

| Nivel | Técnica | Tolerancia a fallo | Uso |
|---|---|---|---|
| **RAID 0** | *Striping* (reparto sin redundancia) | **Ninguna** | Máximo rendimiento; si falla un disco se pierde todo |
| **RAID 1** | *Mirroring* (espejo) | 1 disco | Copia idéntica; alta fiabilidad, mitad de capacidad útil |
| **RAID 5** | *Striping* + **paridad** distribuida | 1 disco | Buen equilibrio capacidad/seguridad; mínimo 3 discos |
| **RAID 6** | *Striping* + **doble paridad** | 2 discos | Como RAID 5 pero soporta 2 fallos; mínimo 4 discos |
| **RAID 10 (1+0)** | Espejo + reparto | 1 por espejo | Alto rendimiento y fiabilidad; mínimo 4 discos |

> **[DATO CLAVE EXAMEN]** **RAID 0 no es redundancia** (solo rendimiento; ningún disco de respaldo). **RAID 1** = espejo. **RAID 5** = paridad, tolera 1 fallo (mínimo 3 discos). **RAID 6** = doble paridad, tolera 2 fallos. Y, sobre todo: **RAID no es una copia de seguridad** — protege frente a la avería de un disco, no frente a un borrado, un cifrado por *ransomware* o un desastre. Se necesitan ambos: RAID **y** backup.

---

## 6. Elementos de visualización y digitalización

### 6.1. Tecnologías de digitalización

**Digitalizar** es convertir información del mundo físico (un documento en papel, una fotografía) en una **representación digital** que el ordenador pueda procesar y almacenar. El dispositivo típico es el **escáner**.

- **Funcionamiento**: una fuente de luz ilumina el documento y un **sensor** capta la luz reflejada, línea a línea, convirtiéndola en valores digitales (píxeles).
- **Tipos de sensor**: **CCD (Charge-Coupled Device)**, de mayor calidad y profundidad, y **CIS (Contact Image Sensor)**, más compacto y económico.
- **Tipos de escáner**: plano (superficie de cristal), de alimentación de hojas (ADF, para lotes de documentos), de tambor (artes gráficas) y de mano.
- **Resolución**: se mide en **ppp (puntos/píxeles por pulgada, dpi)**. A más ppp, más detalle y mayor tamaño de archivo.
- **Profundidad de color (bits por píxel)**: 1 bit (blanco y negro), 8 bits (256 grises), 24 bits (color verdadero).
- **OCR (Reconocimiento Óptico de Caracteres)**: software que convierte la imagen de un texto en **texto editable y buscable**. Es esencial para que un expediente escaneado sea localizable por su contenido.

> **[DATO CLAVE EXAMEN]** La **resolución** se mide en **ppp** y determina el detalle y el tamaño del archivo. El **OCR** transforma la imagen de un documento en texto seleccionable/buscable, pero **no cambia** que el fichero siga conteniendo la imagen; se suele generar un **PDF con capa de texto** (PDF buscable).

### 6.2. Dispositivos de visualización: monitores, proyectores y pantallas táctiles

- **Monitores**: presentan la información en pantalla. Tecnologías:
  - **LCD/LED**: cristal líquido retroiluminado por LED. Es el estándar actual.
  - **OLED**: cada píxel emite su propia luz; negros perfectos y gran contraste.
  Parámetros: **resolución** (Full HD 1920×1080, 4K UHD 3840×2160), **tamaño** (pulgadas), **tasa de refresco** (Hz), **tiempo de respuesta** (ms) y **relación de aspecto** (16:9).
- **Proyectores**: proyectan la imagen sobre una superficie ampliada. Tecnologías DLP y LCD; usados en salas de reuniones y formación.
- **Pantallas táctiles**: son de **entrada/salida** (muestran y captan el toque). Tecnologías:
  - **Resistiva**: dos capas que se tocan al presionar; funciona con cualquier objeto, menor precisión.
  - **Capacitiva**: detecta la conductividad del dedo; multitáctil, nítida (la de los móviles y quioscos modernos).

> **[EJEMPLO AYTO MADRID]** Los **quioscos de autoservicio** y las **pantallas de gestión de turnos** de las oficinas de atención a la ciudadanía usan pantallas **táctiles capacitivas**, robustas y multitáctiles. Su elección atiende también a criterios de **accesibilidad** (altura, contraste, tamaño de los elementos), tratados en el Tema 25.

### 6.3. Modelos de color

Un **modelo de color** describe numéricamente los colores. Los que hay que conocer [CIE]:

- **RGB (Rojo, Verde, Azul)**: modelo **aditivo**. Parte del negro y **suma** luz de colores; al sumar los tres al máximo se obtiene blanco. Es el de **pantallas, cámaras y escáneres**.
- **CMYK (Cian, Magenta, Amarillo, Negro)**: modelo **sustractivo**. Parte del blanco del papel y **resta** luz con tintas; es el de la **impresión**. La K (negro) mejora la profundidad y ahorra tinta.
- **HSV / HSL**: describen el color por **tono, saturación y brillo/luminosidad**; más intuitivos para el diseño.
- **CIELAB (L·a·b)**: espacio **independiente del dispositivo** definido por la CIE, que abarca todos los colores perceptibles; se usa como referencia para convertir con fidelidad entre RGB y CMYK (gestión de color, perfiles ICC).

> **[DATO CLAVE EXAMEN]** **RGB = aditivo, luz, pantallas** (suma → blanco). **CMYK = sustractivo, tintas, impresión** (resta → negro). Por eso un color vivo en pantalla (RGB) puede verse más apagado impreso (CMYK): sus **gamas** no coinciden. **CIELAB** es el modelo de referencia independiente del dispositivo.

### 6.4. Formatos y compresión de imágenes. Filtrado

Una imagen digital puede almacenarse como:

- **Mapa de bits (raster)**: matriz de píxeles. Al ampliarla pierde calidad (pixela). Formatos: JPEG, PNG, GIF, TIFF, BMP.
- **Vectorial**: descrita por fórmulas geométricas; escala sin pérdida. Formatos: SVG, EPS. Ideal para logotipos y planos.

La **compresión** reduce el tamaño del archivo [ISO15948]:

- **Sin pérdida (lossless)**: reconstruye la imagen **exacta**. Formatos **PNG, TIFF, GIF**. Para documentos, logotipos y archivo fiel.
- **Con pérdida (lossy)**: descarta información poco perceptible para reducir mucho el tamaño. Formato **JPEG**, controlado por un **factor de calidad**. Ideal para **fotografías**; desaconsejado para texto (aparecen artefactos alrededor de las letras).

| Formato | Compresión | Uso típico |
|---|---|---|
| **JPEG** | Con pérdida | Fotografía; factor de calidad ajustable |
| **PNG** | Sin pérdida | Gráficos, transparencia, capturas |
| **GIF** | Sin pérdida | Animaciones simples, 256 colores |
| **TIFF** | Sin pérdida (o sin comprimir) | Digitalización de alta calidad, archivo |
| **SVG** | Vectorial | Logotipos, iconos, diagramas |
| **PDF/A** | Documento | Archivo a largo plazo (ISO 19005) |

El **filtrado** aplica algoritmos a los píxeles para mejorar o transformar la imagen: **suavizado** (reduce ruido), **realce/nitidez** (resalta bordes), **umbralización** (binariza a blanco y negro, útil antes del OCR) y corrección de brillo/contraste. En digitalización, el filtrado previo mejora la legibilidad y el rendimiento del OCR.

> **[EJERCICIO RESUELTO]** *¿Cuánto ocupa, sin comprimir, una página A4 digitalizada a 300 ppp en color de 24 bits?* — Un A4 mide 8,27 × 11,69 pulgadas. A 300 ppp: 2.481 × 3.507 píxeles ≈ **8,7 millones de píxeles**. A 24 bits (3 bytes) por píxel: ≈ **26 MB sin comprimir**. Comprimida en JPEG de calidad media baja a ~1-2 MB, o en TIFF sin pérdida a varios MB. Esto explica por qué la NTI fija resoluciones mínimas razonables (200 ppp) y no exageradas: equilibrar fidelidad y tamaño de archivo.

### 6.5. Norma Técnica de Interoperabilidad: requisitos de la imagen electrónica

La digitalización en la Administración no es libre: está regulada por el **Esquema Nacional de Interoperabilidad (ENI)**, aprobado por el **Real Decreto 4/2010** [RD4-2010], y desarrollado por la **Norma Técnica de Interoperabilidad (NTI) de Digitalización de Documentos** (Resolución de 19 de julio de 2011) [NTI-DIGIT]. Su finalidad: que un documento en papel se convierta en una **imagen electrónica** válida, íntegra y con garantías, capaz de sustituir al original en el expediente electrónico.

Requisitos que la NTI fija para la **imagen electrónica** [NTI-DIGIT]:

- **Fidelidad con el original**: la imagen debe ser un reflejo exacto del documento en papel.
- **Resolución mínima**: **200 píxeles por pulgada (ppp)** para documentos en soporte papel (tanto en blanco y negro, como en escala de grises o color, según el original).
- **Formatos admitidos**: los recogidos en la NTI de **Catálogo de estándares** (habitualmente **PDF, PDF/A, TIFF, JPEG, PNG**), priorizando los de archivo a largo plazo (PDF/A).
- **Metadatos mínimos obligatorios** de la imagen electrónica, que la describen y permiten su gestión y búsqueda.
- **Firma**: la imagen se **firma electrónicamente** (o se le asocia un **CSV, Código Seguro de Verificación**) para garantizar su **integridad y autenticidad**.

> **[DATO CLAVE EXAMEN]** La NTI de Digitalización exige una **resolución mínima de 200 ppp** para el papel, formatos del catálogo de estándares (PDF/A, TIFF…), **metadatos mínimos** y **firma electrónica o CSV** de la imagen. El objetivo es obtener una imagen electrónica **fiel, íntegra y auténtica**.

### 6.6. El proceso de digitalización certificada

La **digitalización certificada** (o «copia auténtica de documentos en papel») produce una **imagen electrónica con el mismo valor que el original** en papel, de modo que este puede incluso destruirse conforme a la política de gestión documental. El proceso, según la NTI [NTI-DIGIT][NTI-COPIA][L39-2015]:

1. **Captura de la imagen** con el escáner, respetando resolución y formato exigidos.
2. **Optimización opcional** (enderezado, recorte, mejora de contraste, OCR) **sin alterar el contenido**.
3. **Generación de metadatos** mínimos obligatorios.
4. **Firma electrónica** de la imagen por el órgano o el funcionario habilitado (o sello electrónico de la Administración), o asignación de CSV.
5. **Incorporación al expediente electrónico** y, en su caso, al **archivo electrónico**.

El resultado es una **copia auténtica** (art. 27 de la Ley 39/2015) [L39-2015], con plena validez jurídica.

> **[EJEMPLO AYTO MADRID]** En el registro y las oficinas de asistencia en materia de registro del Ayuntamiento, cuando un ciudadano presenta documentación en papel, se **digitaliza** conforme a la NTI: se escanea a ≥ 200 ppp, se genera un **PDF/A**, se le añaden metadatos y se **firma con el sello electrónico** del Ayuntamiento o se le asigna un **CSV**. La imagen resultante es una **copia auténtica** que se incorpora al expediente electrónico; el original en papel se devuelve al interesado. Así se cumple el principio de administración electrónica de la Ley 39/2015.

### 6.7. Conservación y disponibilidad. Normativa

Digitalizar es solo el principio: los documentos electrónicos deben **conservarse** de forma que sigan siendo **accesibles, legibles e íntegros** a lo largo del tiempo, incluso durante décadas. Retos y respuestas:

- **Obsolescencia de formatos y soportes**: se combate usando **formatos de archivo a largo plazo** (**PDF/A**, ISO 19005) [ISO32000], normalizados y no propietarios, y migrando periódicamente los datos a soportes vigentes.
- **Integridad**: firmas electrónicas, sellos de tiempo y CSV que permiten verificar que el documento no se ha alterado; **resellado** de firmas antes de que caduquen sus certificados.
- **Disponibilidad y redundancia**: copias de seguridad (§5.5) y RAID (§5.6), con copias *offsite*, para que un desastre no destruya el archivo electrónico.
- **Marco normativo**: además del **ENI** [RD4-2010] y sus NTI [NTI-DIGIT], la **Ley 39/2015** [L39-2015] (documentos y copias auténticas, art. 26 y 27), el **Esquema Nacional de Seguridad** [ENS] (protección de la información) y el **RGPD/LOPDGDD** [RGPD] cuando la documentación contiene datos personales.

> **[REFERENCIA CRUZADA]** Los principios básicos del **Esquema Nacional de Interoperabilidad (ENI)** y del **Esquema Nacional de Seguridad (ENS)** se estudian de forma monográfica en el **Tema 39**. La digitalización de este tema es la aplicación práctica del ENI al ciclo de vida del documento electrónico.

> **[DATO CLAVE EXAMEN]** Para el **archivo a largo plazo** el formato de referencia es **PDF/A** (ISO 19005): normalizado, autocontenido y no dependiente de software propietario. La conservación exige, además del formato, **integridad** (firma/sello/CSV, resellado) y **disponibilidad** (backup y redundancia).

---

*Fin del contenido teórico del Tema 12. Consulte el catálogo de diagramas (`tema-12-diagramas.md`), el banco de preguntas (`tema-12-test.md`) y los casos prácticos (`tema-12-caso-practico.md`) para completar el estudio.*
