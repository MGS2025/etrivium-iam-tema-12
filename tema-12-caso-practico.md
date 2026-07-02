# Tema 12 — Casos Prácticos

> **Título oficial**: Periféricos: conectividad y administración. Elementos de impresión. Elementos de almacenamiento. Elementos de visualización y digitalización.
>
> **Formato**: 3 casos prácticos sobre supuestos reales del Ayuntamiento de Madrid. Cada caso suma **10 puntos**.
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid

Los tres casos recorren las cuatro partes del tema: el **Caso 1** trabaja la **conectividad y la administración** de un puesto de usuario (interfaces, drivers, Plug & Play y seguridad de dispositivos); el **Caso 2**, los **elementos de impresión** (elección de tecnología, impresión en red, consumibles y coste); y el **Caso 3**, el **almacenamiento y la digitalización** (RAID, copias de seguridad y digitalización certificada conforme a la NTI).

---

## Caso 1 — Puesto de trabajo de una Oficina de Atención a la Ciudadanía

### Enunciado

Se prepara el puesto de un empleado de una Oficina de Atención a la Ciudadanía de un distrito. El puesto debe llevar: un **portátil** que se conecta a una **estación de acoplamiento (docking)** mediante un solo cable, **dos monitores**, teclado y ratón inalámbricos, un **lector de DNI electrónico** y acceso a una **impresora multifunción en red** del departamento. Al conectar por primera vez el lector de DNI, Windows lo detecta pero aparece con un aviso en el Administrador de dispositivos y no funciona. Además, la política de seguridad municipal prohíbe el uso de memorias USB no autorizadas.

### Cuestiones

**Cuestión 1 — Conectividad del docking (2 puntos).** ¿Qué interfaz permite que un solo cable lleve del portátil al docking datos, vídeo para los monitores y energía de carga? Justifique por qué es la idónea.

**Cuestión 2 — Multipantalla (2 puntos).** Se quieren conectar dos monitores desde el docking. ¿Qué interfaz de vídeo permite encadenar varios monitores en serie y con qué tecnología? Cite también la alternativa de consumo.

**Cuestión 3 — El lector de DNI que no funciona (3 puntos).** Interprete el aviso del Administrador de dispositivos y proponga los pasos de diagnóstico y resolución en orden correcto.

**Cuestión 4 — Seguridad de dispositivos (3 puntos).** Explique cómo se aplica la prohibición de memorias USB no autorizadas y otras dos medidas de protección de la información en el puesto exigibles por el Esquema Nacional de Seguridad.

### Solución orientativa

- **C1**: La interfaz idónea es **Thunderbolt (sobre conector USB-C)**, o USB4 con USB Power Delivery: un único cable transporta **datos (PCIe), vídeo (DisplayPort) y energía** (hasta 240 W con USB PD 3.1), que es justo lo que hace una docking station. *(§2.2, §2.4)*
- **C2**: **DisplayPort** admite **MST (Multi-Stream Transport)**, que permite encadenar los dos monitores en serie (*daisy-chain*) desde una sola salida. La alternativa del ámbito de consumo sería **HDMI**, aunque normalmente requiere una salida por monitor. *(§2.3)*
- **C3**: El aviso indica un **problema de controlador (driver)**. Pasos: (1) comprobar lo físico (cable/puerto del lector); (2) verificar en el Administrador de dispositivos que aparece el dispositivo; (3) **instalar/actualizar el driver** del fabricante (el genérico puede no bastar), preferiblemente **firmado**; (4) si el fallo surgió tras una actualización, **revertir (rollback)**; (5) consultar el visor de eventos y, si procede, probar el lector en otro equipo para aislar. *(§3.4, §2.7)*
- **C4**: La prohibición de USB se implementa con **políticas de control de dispositivos/puertos** (por directiva de grupo, GPO) que bloquean las clases de almacenamiento extraíble no autorizadas, junto a **listas blancas** de dispositivos permitidos. Otras dos medidas del ENS: **cifrado del disco del portátil** con BitLocker (soporte perdido = ilegible) y **borrado seguro** del disco al dar de baja el equipo; también valen soluciones **DLP** y antivirus con análisis de extraíbles. *(§3.5, §3.6)*

### Criterios de evaluación

| Criterio | Puntos |
|---|---|
| Identifica Thunderbolt/USB4 (USB-C) con datos+vídeo+energía y lo justifica | 2 |
| Explica DisplayPort con MST para multipantalla y cita HDMI como alternativa | 2 |
| Diagnóstico ordenado (físico→driver→rollback→aislar) del lector de DNI | 3 |
| Control de puertos USB (GPO/listas blancas) + 2 medidas del ENS (cifrado, borrado seguro/DLP) | 3 |

---

## Caso 2 — Renovación del parque de impresión de un distrito

### Enunciado

Un distrito quiere racionalizar su impresión. Hoy hay muchas impresoras de inyección pequeñas en cada mesa, con alto coste de tinta y documentos con datos personales que a veces quedan olvidados en las bandejas. Se plantea sustituirlas por **impresoras multifunción láser en red** compartidas. El volumen es alto (informes, notificaciones), predomina el **texto en blanco y negro** y ocasionalmente se imprimen **carteles en color**. También se emite un pequeño número de **formularios multicopia por presión** en la unidad de recaudación.

### Cuestiones

**Cuestión 1 — Elección de tecnología (3 puntos).** Justifique por qué la impresión **láser** es la adecuada para el grueso del trabajo, e indique qué tecnología conviene mantener para los formularios multicopia y por qué.

**Cuestión 2 — Impresión en red (2 puntos).** Explique el papel del **spooler (cola de impresión)** y cite un protocolo de impresión moderno y un lenguaje de descripción de página.

**Cuestión 3 — Seguridad e impresión (2 puntos).** ¿Qué mecanismo evita que las notificaciones con datos personales queden olvidadas en la bandeja? Descríbalo.

**Cuestión 4 — Consumibles y coste (3 puntos).** Compare el consumible de una láser frente a una de inyección y explique con qué criterio económico se decide en un parque grande. Proponga dos medidas de configuración centralizada para ahorrar.

### Solución orientativa

- **C1**: La **láser** ofrece **alta velocidad y bajo coste por página**, ideal para grandes volúmenes de texto en blanco y negro (informes, notificaciones); el tóner se fija por calor. Para los **formularios multicopia por presión** conviene mantener una **impresora matricial (de impacto)**, la única que genera **copia por presión** sobre papel autocopiativo. La inyección se reservaría, si acaso, a color fotográfico puntual. *(§4.1)*
- **C2**: El **spooler** recibe los trabajos, los pone en **cola** y los envía en orden a la impresora, liberando enseguida la aplicación del usuario y gestionando prioridades, pausas y reintentos. Protocolo moderno: **IPP** (Internet Printing Protocol); lenguaje de descripción de página: **PostScript** o **PCL** (también PDF directo). *(§4.3)*
- **C3**: La **impresión con liberación segura (pull printing)**: el trabajo se retiene en la cola y el documento **solo se imprime cuando el usuario se identifica** con su tarjeta o PIN en el equipo. Evita que documentos con datos personales queden a la vista. *(§4.3, §3.5)*
- **C4**: La láser usa **tóner** (cartucho de polvo de **alto rendimiento**, miles de páginas), frente a los **cartuchos de tinta** de la inyección, de menor rendimiento y mayor coste por página. La decisión se toma por **coste por página (CPP)** y rendimiento del consumible. Medidas de ahorro por configuración centralizada (GPO): **doble cara (dúplex) y blanco y negro por defecto**, y **cuotas/retención** de impresión. *(§4.2, §3.2)*

### Criterios de evaluación

| Criterio | Puntos |
|---|---|
| Justifica la láser (velocidad/CPP) y mantiene matricial para copia por presión | 3 |
| Explica el spooler + cita IPP y PostScript/PCL | 2 |
| Describe correctamente el *pull printing* | 2 |
| Compara tóner vs tinta, criterio CPP y 2 medidas de ahorro centralizadas | 3 |

---

## Caso 3 — Almacenamiento y digitalización de expedientes

### Enunciado

El servicio de archivo del Ayuntamiento debe **digitalizar expedientes en papel** y conservarlos en un **servidor con varios discos**. Requisitos: que la avería de un disco no detenga el servicio ni pierda datos; que exista una estrategia de **copias de seguridad** frente a borrados y *ransomware*; y que las imágenes digitalizadas tengan **validez jurídica** para poder devolver el papel al ciudadano. Algunos expedientes escaneados en color superan los **5 GB** por archivo.

### Cuestiones

**Cuestión 1 — Redundancia de disco (2 puntos).** Proponga un nivel **RAID** adecuado para el servidor y explique qué protege y qué NO protege el RAID.

**Cuestión 2 — Copias de seguridad (3 puntos).** Diseñe una estrategia de copias conforme a la regla **3-2-1** y explique la diferencia entre copia **completa**, **incremental** y **diferencial**.

**Cuestión 3 — Sistema de archivos (2 puntos).** El recurso de red debe admitir archivos de más de 5 GB. ¿Qué sistema de archivos **no** serviría y cuáles sí? Justifique.

**Cuestión 4 — Digitalización certificada (3 puntos).** Enumere los pasos del proceso de **digitalización certificada** según la NTI y explique qué requisitos (resolución, formato, firma) convierten la imagen en **copia auténtica**.

### Solución orientativa

- **C1**: Un nivel adecuado es **RAID 5** (striping con paridad, tolera 1 fallo, mínimo 3 discos) o **RAID 6/10** para mayor exigencia. El RAID **protege frente a la avería de un disco** (continuidad del servicio), pero **NO es una copia de seguridad**: no protege frente a un borrado accidental, un cifrado por *ransomware* ni un desastre. Se necesitan **RAID y backup**. *(§5.6)*
- **C2**: Estrategia **3-2-1**: **3 copias** (los datos de producción + 2), en **2 tipos de soporte** distintos (p. ej. disco en NAS + cinta o nube), con **1 copia fuera** de las instalaciones (*offsite*). Tipos: **completa** (todo; restauración simple, ocupa más), **incremental** (solo lo cambiado desde la última copia; ligera, pero restaurar exige la completa + toda la cadena), **diferencial** (lo cambiado desde la última completa; restauración con completa + última diferencial). Además, **verificar restauraciones** periódicamente. *(§5.5)*
- **C3**: **FAT32 no serviría**, porque no admite archivos de más de **4 GB** y los expedientes superan 5 GB. Sirven **exFAT** (para extraíbles) y, en un servidor, **NTFS** (Windows) o **ext4** (Linux), que además aportan permisos y *journaling*. Para un recurso de red compartido, lo habitual es NTFS/ext4 con acceso por SMB/NFS. *(§5.3)*
- **C4**: Pasos NTI: (1) **captura** con escáner a **≥ 200 ppp**; (2) **optimización/OCR** sin alterar el contenido; (3) **metadatos** mínimos obligatorios; (4) **firma electrónica o CSV** por el órgano/funcionario habilitado; (5) **incorporación** al expediente y al archivo electrónico. La imagen debe ser **fiel**, en un **formato del catálogo de estándares** (preferible **PDF/A** para archivo), con **metadatos** y **firma/CSV** que garanticen integridad y autenticidad. Así se obtiene una **copia auténtica** (art. 27 Ley 39/2015) que permite devolver el papel. *(§6.5, §6.6)*

### Criterios de evaluación

| Criterio | Puntos |
|---|---|
| Propone RAID 5/6/10 y distingue «RAID protege avería de disco» de «RAID no es backup» | 2 |
| Diseña la estrategia 3-2-1 y distingue completa/incremental/diferencial | 3 |
| Descarta FAT32 (límite 4 GB) y propone NTFS/ext4/exFAT justificando | 2 |
| Enumera el proceso NTI (≥200 ppp, PDF/A, metadatos, firma/CSV) y lo liga a copia auténtica | 3 |

---

*Estos tres casos cubren los ejes del tema aplicados al Ayuntamiento de Madrid. Las soluciones son orientativas: en el examen se valorará el razonamiento y la correcta aplicación de los conceptos, no la literalidad.*
