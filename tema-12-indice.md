# Tema 12 — Índice

> **Título oficial**: Periféricos: conectividad y administración. Elementos de impresión. Elementos de almacenamiento. Elementos de visualización y digitalización.
>
> **Bloque**: Parte II — Técnico (Temas 11-40)
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid

---

## Estructura del tema

1. **Tipología y clasificación de periféricos**
   1.1. Qué es un periférico y su papel en el sistema de información
   1.2. Clasificación por función (entrada, salida, entrada/salida, comunicación, almacenamiento)
   1.3. Periféricos locales, compartidos y en red
   1.4. El bus, el controlador y el puerto: cómo dialoga el periférico con el equipo

2. **Conectividad**
   2.1. Interfaces físicas: concepto de puerto e interfaz
   2.2. USB (versiones, USB-C, Power Delivery)
   2.3. HDMI y DisplayPort
   2.4. Thunderbolt y otros estándares (eSATA, SAS, serie/paralelo heredados)
   2.5. Conectividad inalámbrica: Bluetooth y Wi-Fi
   2.6. Tecnologías inalámbricas emergentes (NFC, UWB, Wi-Fi 6E/7, Thread/Matter)
   2.7. Protocolos y controladores: drivers y compatibilidad
   2.8. Plug & Play y gestión automática de dispositivos

3. **Administración de periféricos**
   3.1. Configuración del sistema: instalación de dispositivos
   3.2. Paneles de control y utilidades (Windows y Linux)
   3.3. Gestión y mantenimiento: actualización de controladores
   3.4. Diagnóstico y resolución de problemas
   3.5. Seguridad en dispositivos: control de accesos
   3.6. Protección frente a amenazas (BadUSB, DLP, cifrado de soportes)

4. **Elementos de impresión**
   4.1. Impresión convencional: tecnologías (láser, inyección, matricial, térmica)
   4.2. Tipos de consumibles (tóner, cartuchos, cabezales, papel)
   4.3. Impresión en red y lenguajes de descripción de página (PCL, PostScript, PDF)
   4.4. Impresión 3D (FDM, SLA, SLS)

5. **Elementos de almacenamiento**
   5.1. Tipos de dispositivos: magnéticos, ópticos y de estado sólido
   5.2. Tecnologías y formatos: interfaces y capacidades
   5.3. Sistemas de archivos (FAT32, exFAT, NTFS, ext4, APFS)
   5.4. Gestión del almacenamiento: particionado y formateo
   5.5. Copias de seguridad
   5.6. Sistemas de protección y redundancia (RAID)

6. **Elementos de visualización y digitalización**
   6.1. Tecnologías de digitalización (escáneres, sensores CCD/CIS, OCR)
   6.2. Dispositivos de visualización: monitores, proyectores y pantallas táctiles
   6.3. Modelos de color (RGB, CMYK, HSV/HSL, CIELAB)
   6.4. Formatos y compresión de imágenes. Filtrado
   6.5. Norma Técnica de Interoperabilidad: requisitos de la imagen electrónica
   6.6. El proceso de digitalización certificada
   6.7. Conservación y disponibilidad. Normativa

---

## Conceptos clave para memorizar

| Concepto | Dato clave |
|---|---|
| Periférico | Dispositivo que se conecta a la unidad central para introducir, extraer, comunicar o almacenar datos |
| Clasificación funcional | Entrada, salida, entrada/salida (E/S), comunicación y almacenamiento |
| Puerto vs interfaz | El puerto es el conector físico; la interfaz es el conjunto de reglas físicas y lógicas de la conexión |
| Controlador (driver) | Software que traduce entre el sistema operativo y el hardware del periférico |
| Plug & Play (PnP) | El sistema detecta, identifica y configura el dispositivo automáticamente al conectarlo |
| USB | Bus serie universal; USB4 hasta 40 Gbps; USB-C es el conector reversible que soporta datos, vídeo y Power Delivery |
| USB Power Delivery | Entrega de energía por USB-C, hasta 240 W (USB PD 3.1) |
| HDMI / DisplayPort | Interfaces de vídeo y audio digital; DisplayPort admite MST (varias pantallas en cadena) |
| Thunderbolt | Interfaz de alto rendimiento sobre conector USB-C; TB4 garantiza 40 Gbps y hasta 2 pantallas 4K |
| Bluetooth | Inalámbrico de corto alcance (WPAN), banda 2,4 GHz; BLE optimiza el consumo |
| Wi-Fi | Red inalámbrica (WLAN) IEEE 802.11; Wi-Fi 6 (802.11ax), Wi-Fi 6E (6 GHz), Wi-Fi 7 (802.11be) |
| NFC | Comunicación de campo cercano (<4 cm) a 13,56 MHz; pagos y emparejamiento |
| Láser vs inyección | Láser: tóner + fusión térmica, alta velocidad; inyección: gotas de tinta, mejor color fotográfico |
| PostScript / PCL | Lenguajes de descripción de página; PostScript (Adobe) es independiente del dispositivo |
| Impresión 3D | Fabricación aditiva capa a capa; FDM (filamento), SLA (resina), SLS (polvo sinterizado) |
| Magnético / óptico / SSD | HDD (platos), CD/DVD/Blu-ray (láser), SSD (memoria flash NAND, sin partes móviles) |
| Sistema de archivos | Estructura lógica que organiza datos en un soporte: FAT32, exFAT, NTFS, ext4, APFS |
| Partición | División lógica de un disco; esquemas MBR (máx. 2 TB) y GPT (moderno, sin ese límite) |
| RAID | Redundancia por combinación de discos: RAID 0 (rendimiento), 1 (espejo), 5 (paridad), 10 (espejo + banda) |
| Regla 3-2-1 | 3 copias, en 2 soportes distintos, 1 de ellas fuera de las instalaciones |
| Modelo de color | RGB (aditivo, pantalla), CMYK (sustractivo, impresión), CIELAB (independiente del dispositivo) |
| Resolución de escaneo | Se mide en ppp (píxeles por pulgada); la NTI exige ≥ 200 ppp para documentos en soporte papel |
| Compresión con/sin pérdida | Sin pérdida: PNG, TIFF, GIF; con pérdida: JPEG (fotografía), controlada por factor de calidad |
| NTI Digitalización | Norma Técnica de Interoperabilidad de Digitalización de Documentos (ENI, RD 4/2010) |
| Copia auténtica | Imagen electrónica firmada (con CSV o firma electrónica) con el mismo valor que el original |

---

*Tiempo estimado de estudio: 12-14 horas*
*Extensión del contenido: ~11.000 palabras · 12 diagramas SVG embebidos*
