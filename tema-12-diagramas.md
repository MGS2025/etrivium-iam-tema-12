# Tema 12 — Catálogo de Diagramas

> **Título oficial**: Periféricos: conectividad y administración. Elementos de impresión. Elementos de almacenamiento. Elementos de visualización y digitalización.
>
> **Versión**: v1.0
> **Fecha**: 2026-07-02
> **Autor**: ETRIVIUM
> **Formato**: SVG inline (zero-dependencias, escalable, imprimible, accesible con role/aria-label)
> **Paleta**: Ayuntamiento de Madrid #0055a0 (primario) + #d13c3c (alertas) + #2d8659 (ventajas) + #e89822 (callouts)

---

## Índice de diagramas

| ID | Título | Sección | Tipo | Formato |
|---|---|---|---|---|
| D1 | Clasificación funcional de los periféricos | §1.2 | Mapa | 680×320 |
| D2 | Del puerto al driver: la cadena de conexión | §1.4 | Flujo | 680×240 |
| D3 | Interfaces de vídeo: HDMI, DisplayPort y USB-C/Thunderbolt | §2.3-2.4 | Comparativa | 680×300 |
| D4 | Evolución de la velocidad USB | §2.2 | Barras | 680×320 |
| D5 | Inalámbricas: alcance frente a uso | §2.5-2.6 | Escala | 680×300 |
| D6 | El ciclo Plug & Play | §2.8 | Flujo | 680×260 |
| D7 | Tecnologías de impresión comparadas | §4.1 | Comparativa | 680×320 |
| D8 | Tipos de almacenamiento secundario | §5.1 | Estructura | 680×320 |
| D9 | Niveles RAID más frecuentes | §5.6 | Comparativa | 680×340 |
| D10 | La regla 3-2-1 de las copias de seguridad | §5.5 | Concepto | 660×300 |
| D11 | Modelos de color: RGB aditivo y CMYK sustractivo | §6.3 | Comparativa | 680×300 |
| D12 | Proceso de digitalización certificada (NTI) | §6.6 | Flujo | 680×300 |

---

## D1 · Clasificación funcional de los periféricos

**Sección**: §1.2 — Clasificación por función
**Propósito**: Fijar las cinco categorías funcionales con ejemplos.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Clasificación funcional de los periféricos en cinco categorías: entrada, salida, entrada/salida, comunicación y almacenamiento, con ejemplos">
  <style>.t{font:700 13px system-ui,sans-serif;fill:#fff}.s{font:11px system-ui,sans-serif;fill:#fff}.h{font:700 14px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="26" text-anchor="middle" class="h">Periféricos según la dirección del flujo de datos</text>
  <rect x="30" y="50" width="130" height="110" rx="8" fill="#0055a0"/><text x="95" y="76" text-anchor="middle" class="t">ENTRADA</text><text x="95" y="100" text-anchor="middle" class="s">Teclado</text><text x="95" y="118" text-anchor="middle" class="s">Ratón</text><text x="95" y="136" text-anchor="middle" class="s">Escáner</text>
  <rect x="180" y="50" width="130" height="110" rx="8" fill="#2d8659"/><text x="245" y="76" text-anchor="middle" class="t">SALIDA</text><text x="245" y="100" text-anchor="middle" class="s">Monitor</text><text x="245" y="118" text-anchor="middle" class="s">Impresora</text><text x="245" y="136" text-anchor="middle" class="s">Altavoces</text>
  <rect x="330" y="50" width="150" height="110" rx="8" fill="#003d73"/><text x="405" y="76" text-anchor="middle" class="t">ENTRADA/SALIDA</text><text x="405" y="100" text-anchor="middle" class="s">Pantalla táctil</text><text x="405" y="118" text-anchor="middle" class="s">Multifunción</text><text x="405" y="136" text-anchor="middle" class="s">Disco (lee/escribe)</text>
  <rect x="500" y="50" width="150" height="110" rx="8" fill="#e89822"/><text x="575" y="76" text-anchor="middle" class="t">COMUNICACIÓN</text><text x="575" y="100" text-anchor="middle" class="s">Tarjeta de red</text><text x="575" y="118" text-anchor="middle" class="s">Módem</text><text x="575" y="136" text-anchor="middle" class="s">Bluetooth</text>
  <rect x="180" y="185" width="320" height="90" rx="8" fill="#6ea3d2"/><text x="340" y="213" text-anchor="middle" class="t">ALMACENAMIENTO</text><text x="340" y="238" text-anchor="middle" class="s">HDD · SSD · memoria USB · NAS · grabadora óptica</text><text x="340" y="258" text-anchor="middle" class="s">Conservan los datos de forma persistente</text>
  <text x="672" y="308" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: ISO 7498]</text>
</svg>
```

---

## D2 · Del puerto al driver: la cadena de conexión

**Sección**: §1.4 — El bus, el controlador y el puerto
**Propósito**: Distinguir puerto (físico), interfaz/bus, host controller (hardware) y driver (software).

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 240" role="img" aria-label="Cadena de conexión de un periférico: puerto, interfaz o bus, controlador de hardware y controlador de software o driver, hasta el sistema operativo">
  <style>.t{font:700 12px system-ui,sans-serif;fill:#fff}.s{font:10px system-ui,sans-serif;fill:#fff}.h{font:700 14px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="28" text-anchor="middle" class="h">Cómo dialoga el periférico con el equipo</text>
  <rect x="24" y="70" width="118" height="80" rx="8" fill="#003d73"/><text x="83" y="98" text-anchor="middle" class="t">PUERTO</text><text x="83" y="118" text-anchor="middle" class="s">Conector físico</text><text x="83" y="134" text-anchor="middle" class="s">(el «enchufe»)</text>
  <rect x="164" y="70" width="118" height="80" rx="8" fill="#0055a0"/><text x="223" y="98" text-anchor="middle" class="t">INTERFAZ/BUS</text><text x="223" y="118" text-anchor="middle" class="s">Líneas y reglas</text><text x="223" y="134" text-anchor="middle" class="s">USB, PCIe, SATA</text>
  <rect x="304" y="70" width="118" height="80" rx="8" fill="#2d8659"/><text x="363" y="98" text-anchor="middle" class="t">HOST CONTROLLER</text><text x="363" y="118" text-anchor="middle" class="s">Circuito de placa</text><text x="363" y="134" text-anchor="middle" class="s">(hardware)</text>
  <rect x="444" y="70" width="118" height="80" rx="8" fill="#e89822"/><text x="503" y="98" text-anchor="middle" class="t">DRIVER</text><text x="503" y="118" text-anchor="middle" class="s">Traductor SO↔HW</text><text x="503" y="134" text-anchor="middle" class="s">(software)</text>
  <rect x="584" y="70" width="72" height="80" rx="8" fill="#6ea3d2"/><text x="620" y="104" text-anchor="middle" class="t">SISTEMA</text><text x="620" y="122" text-anchor="middle" class="t">OPERATIVO</text>
  <g stroke="#888" stroke-width="2" marker-end="url(#a2)"><path d="M142 110 L162 110"/><path d="M282 110 L302 110"/><path d="M422 110 L442 110"/><path d="M562 110 L582 110"/></g>
  <defs><marker id="a2" markerWidth="8" markerHeight="8" refX="6" refY="4" orient="auto"><path d="M0 0 L8 4 L0 8 z" fill="#888"/></marker></defs>
  <text x="672" y="228" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: USB-IF; MS-DEVMGR]</text>
</svg>
```

---

## D3 · Interfaces de vídeo: HDMI, DisplayPort y USB-C/Thunderbolt

**Sección**: §2.3-2.4 — HDMI, DisplayPort y Thunderbolt
**Propósito**: Comparar las tres grandes interfaces de vídeo digital.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 300" role="img" aria-label="Comparativa de HDMI, DisplayPort y USB-C con Thunderbolt según ámbito, multipantalla y contenido transportado">
  <style>.t{font:700 13px system-ui,sans-serif;fill:#fff}.s{font:11px system-ui,sans-serif;fill:#333}.hd{font:700 12px system-ui,sans-serif;fill:#0055a0}.h{font:700 14px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="26" text-anchor="middle" class="h">Interfaces de vídeo y audio digital</text>
  <rect x="30" y="46" width="200" height="40" rx="6" fill="#0055a0"/><text x="130" y="71" text-anchor="middle" class="t">HDMI</text>
  <rect x="240" y="46" width="200" height="40" rx="6" fill="#2d8659"/><text x="340" y="71" text-anchor="middle" class="t">DisplayPort</text>
  <rect x="450" y="46" width="200" height="40" rx="6" fill="#e89822"/><text x="550" y="71" text-anchor="middle" class="t">USB-C / Thunderbolt</text>
  <rect x="30" y="96" width="200" height="180" rx="6" fill="#eef3f9"/><rect x="240" y="96" width="200" height="180" rx="6" fill="#eef6f0"/><rect x="450" y="96" width="200" height="180" rx="6" fill="#fbf1e2"/>
  <text x="130" y="122" text-anchor="middle" class="hd">Ámbito consumo/AV</text><text x="130" y="150" text-anchor="middle" class="s">TV, consolas,</text><text x="130" y="168" text-anchor="middle" class="s">proyectores</text><text x="130" y="200" text-anchor="middle" class="s">1 pantalla/puerto</text><text x="130" y="232" text-anchor="middle" class="s">Vídeo + audio</text><text x="130" y="256" text-anchor="middle" class="s">eARC (2.1: 4K/120)</text>
  <text x="340" y="122" text-anchor="middle" class="hd">Ámbito profesional</text><text x="340" y="150" text-anchor="middle" class="s">PC y monitores</text><text x="340" y="168" text-anchor="middle" class="s">estándar abierto VESA</text><text x="340" y="200" text-anchor="middle" class="s">Varias en cadena (MST)</text><text x="340" y="232" text-anchor="middle" class="s">Vídeo + audio</text><text x="340" y="256" text-anchor="middle" class="s">Muy alto ancho de banda</text>
  <text x="550" y="122" text-anchor="middle" class="hd">Todo en un cable</text><text x="550" y="150" text-anchor="middle" class="s">Conector USB-C</text><text x="550" y="168" text-anchor="middle" class="s">reversible</text><text x="550" y="200" text-anchor="middle" class="s">TB4: 40 Gbps, 2×4K</text><text x="550" y="232" text-anchor="middle" class="s">Datos + vídeo + energía</text><text x="550" y="256" text-anchor="middle" class="s">Base de USB4 · docks</text>
  <text x="672" y="294" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: HDMI; VESA-DP; TB]</text>
</svg>
```

---

## D4 · Evolución de la velocidad USB

**Sección**: §2.2 — USB
**Propósito**: Visualizar el salto de velocidad entre versiones (escala logarítmica aproximada por altura).

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Barras de velocidad máxima de las versiones USB: USB 2.0 480 Mbps, USB 3.2 Gen1 5 Gbps, Gen2 10 Gbps, Gen 2x2 20 Gbps y USB4 40 Gbps">
  <style>.t{font:700 12px system-ui,sans-serif;fill:#fff}.l{font:11px system-ui,sans-serif;fill:#333}.h{font:700 14px system-ui,sans-serif;fill:#0055a0}.v{font:700 12px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="26" text-anchor="middle" class="h">Velocidad máxima por versión de USB</text>
  <line x1="60" y1="270" x2="650" y2="270" stroke="#ccc" stroke-width="1"/>
  <rect x="80" y="230" width="80" height="40" rx="4" fill="#6ea3d2"/><text x="120" y="255" text-anchor="middle" class="t">480 Mb</text><text x="120" y="290" text-anchor="middle" class="l">USB 2.0</text>
  <rect x="200" y="180" width="80" height="90" rx="4" fill="#0055a0"/><text x="240" y="215" text-anchor="middle" class="t">5 Gb</text><text x="240" y="290" text-anchor="middle" class="l">3.2 Gen 1</text>
  <rect x="320" y="140" width="80" height="130" rx="4" fill="#0055a0"/><text x="360" y="180" text-anchor="middle" class="t">10 Gb</text><text x="360" y="290" text-anchor="middle" class="l">3.2 Gen 2</text>
  <rect x="440" y="100" width="80" height="170" rx="4" fill="#003d73"/><text x="480" y="140" text-anchor="middle" class="t">20 Gb</text><text x="480" y="290" text-anchor="middle" class="l">3.2 Gen 2×2</text>
  <rect x="560" y="60" width="80" height="210" rx="4" fill="#2d8659"/><text x="600" y="100" text-anchor="middle" class="t">40 Gb</text><text x="600" y="290" text-anchor="middle" class="l">USB4</text>
  <text x="340" y="312" text-anchor="middle" class="v">USB-C es el conector; la versión (protocolo) fija la velocidad</text>
  <text x="672" y="312" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: USB-IF]</text>
</svg>
```

---

## D5 · Inalámbricas: alcance frente a uso

**Sección**: §2.5-2.6 — Conectividad inalámbrica
**Propósito**: Situar NFC, Bluetooth y Wi-Fi por alcance y propósito.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 300" role="img" aria-label="Tecnologías inalámbricas ordenadas por alcance creciente: NFC menos de 4 centímetros, Bluetooth hasta 10 metros red personal, Wi-Fi decenas de metros red local">
  <style>.t{font:700 13px system-ui,sans-serif;fill:#fff}.s{font:11px system-ui,sans-serif;fill:#fff}.l{font:11px system-ui,sans-serif;fill:#555}.h{font:700 14px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="26" text-anchor="middle" class="h">Del contacto casi físico a la red local</text>
  <rect x="30" y="70" width="180" height="150" rx="10" fill="#d13c3c"/><text x="120" y="100" text-anchor="middle" class="t">NFC</text><text x="120" y="128" text-anchor="middle" class="s">&lt; 4 cm · 13,56 MHz</text><text x="120" y="152" text-anchor="middle" class="s">Pagos, validación,</text><text x="120" y="170" text-anchor="middle" class="s">emparejamiento</text><text x="120" y="200" text-anchor="middle" class="s">Muy corto alcance</text>
  <rect x="250" y="70" width="180" height="150" rx="10" fill="#0055a0"/><text x="340" y="100" text-anchor="middle" class="t">Bluetooth (WPAN)</text><text x="340" y="128" text-anchor="middle" class="s">~10 m · 2,4 GHz</text><text x="340" y="152" text-anchor="middle" class="s">Teclado, ratón,</text><text x="340" y="170" text-anchor="middle" class="s">auriculares · BLE</text><text x="340" y="200" text-anchor="middle" class="s">Periféricos personales</text>
  <rect x="470" y="70" width="180" height="150" rx="10" fill="#2d8659"/><text x="560" y="100" text-anchor="middle" class="t">Wi-Fi (WLAN)</text><text x="560" y="128" text-anchor="middle" class="s">Decenas de m</text><text x="560" y="152" text-anchor="middle" class="s">2,4 / 5 / 6 GHz</text><text x="560" y="170" text-anchor="middle" class="s">802.11ax/be</text><text x="560" y="200" text-anchor="middle" class="s">Acceso a la red</text>
  <text x="120" y="248" text-anchor="middle" class="l">menor alcance</text><text x="560" y="248" text-anchor="middle" class="l">mayor alcance</text>
  <path d="M60 262 L640 262" stroke="#bbb" stroke-width="2" marker-end="url(#a5)"/>
  <defs><marker id="a5" markerWidth="9" markerHeight="9" refX="5" refY="4" orient="auto"><path d="M0 0 L8 4 L0 8 z" fill="#bbb"/></marker></defs>
  <text x="672" y="292" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: BT-SIG; IEEE 802.11]</text>
</svg>
```

---

## D6 · El ciclo Plug & Play

**Sección**: §2.8 — Plug & Play y gestión automática
**Propósito**: Encadenar los cinco pasos de la configuración automática.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 260" role="img" aria-label="Ciclo Plug and Play en cinco pasos: detección, identificación, asignación de recursos, carga del driver y disponibilidad">
  <style>.t{font:700 12px system-ui,sans-serif;fill:#fff}.s{font:10px system-ui,sans-serif;fill:#fff}.h{font:700 14px system-ui,sans-serif;fill:#0055a0}.n{font:700 13px system-ui,sans-serif;fill:#e89822}</style>
  <text x="340" y="28" text-anchor="middle" class="h">Al conectar el dispositivo, el sistema lo configura solo</text>
  <rect x="24" y="90" width="120" height="90" rx="8" fill="#003d73"/><text x="84" y="60" text-anchor="middle" class="n">1</text><text x="84" y="120" text-anchor="middle" class="t">Detección</text><text x="84" y="142" text-anchor="middle" class="s">El bus avisa</text><text x="84" y="158" text-anchor="middle" class="s">del nuevo HW</text>
  <rect x="164" y="90" width="120" height="90" rx="8" fill="#0055a0"/><text x="224" y="60" text-anchor="middle" class="n">2</text><text x="224" y="120" text-anchor="middle" class="t">Identificación</text><text x="224" y="142" text-anchor="middle" class="s">VID/PID</text><text x="224" y="158" text-anchor="middle" class="s">y clase</text>
  <rect x="304" y="90" width="120" height="90" rx="8" fill="#2d8659"/><text x="364" y="60" text-anchor="middle" class="n">3</text><text x="364" y="120" text-anchor="middle" class="t">Recursos</text><text x="364" y="142" text-anchor="middle" class="s">Direcciones,</text><text x="364" y="158" text-anchor="middle" class="s">interrupciones</text>
  <rect x="444" y="90" width="120" height="90" rx="8" fill="#0055a0"/><text x="504" y="60" text-anchor="middle" class="n">4</text><text x="504" y="120" text-anchor="middle" class="t">Carga driver</text><text x="504" y="142" text-anchor="middle" class="s">Local / Update /</text><text x="504" y="158" text-anchor="middle" class="s">repositorio</text>
  <rect x="584" y="90" width="72" height="90" rx="8" fill="#e89822"/><text x="620" y="60" text-anchor="middle" class="n">5</text><text x="620" y="128" text-anchor="middle" class="t">Listo</text><text x="620" y="150" text-anchor="middle" class="s">para usar</text>
  <g stroke="#888" stroke-width="2" marker-end="url(#a6)"><path d="M144 135 L162 135"/><path d="M284 135 L302 135"/><path d="M424 135 L442 135"/><path d="M564 135 L582 135"/></g>
  <defs><marker id="a6" markerWidth="8" markerHeight="8" refX="6" refY="4" orient="auto"><path d="M0 0 L8 4 L0 8 z" fill="#888"/></marker></defs>
  <text x="672" y="248" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: MS-DEVMGR]</text>
</svg>
```

---

## D7 · Tecnologías de impresión comparadas

**Sección**: §4.1 — Impresión convencional
**Propósito**: Contrastar láser, inyección, matricial y térmica.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Comparativa de tecnologías de impresión: láser con tóner y fusión, inyección con tinta líquida, matricial de impacto y térmica por calor">
  <style>.t{font:700 13px system-ui,sans-serif;fill:#fff}.s{font:10px system-ui,sans-serif;fill:#333}.h{font:700 14px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="26" text-anchor="middle" class="h">Cuatro tecnologías de impresión</text>
  <rect x="24" y="48" width="150" height="36" rx="6" fill="#0055a0"/><text x="99" y="72" text-anchor="middle" class="t">LÁSER</text>
  <rect x="188" y="48" width="150" height="36" rx="6" fill="#2d8659"/><text x="263" y="72" text-anchor="middle" class="t">INYECCIÓN</text>
  <rect x="352" y="48" width="150" height="36" rx="6" fill="#e89822"/><text x="427" y="72" text-anchor="middle" class="t">MATRICIAL</text>
  <rect x="516" y="48" width="140" height="36" rx="6" fill="#003d73"/><text x="586" y="72" text-anchor="middle" class="t">TÉRMICA</text>
  <rect x="24" y="94" width="150" height="200" rx="6" fill="#eef3f9"/><rect x="188" y="94" width="150" height="200" rx="6" fill="#eef6f0"/><rect x="352" y="94" width="150" height="200" rx="6" fill="#fbf1e2"/><rect x="516" y="94" width="140" height="200" rx="6" fill="#eaf0f6"/>
  <text x="99" y="122" text-anchor="middle" class="s">Tóner (polvo)</text><text x="99" y="146" text-anchor="middle" class="s">Fusión por calor</text><text x="99" y="176" text-anchor="middle" class="s">Muy rápida</text><text x="99" y="200" text-anchor="middle" class="s">Bajo coste/pág.</text><text x="99" y="236" text-anchor="middle" class="s">Documentos y</text><text x="99" y="254" text-anchor="middle" class="s">volúmenes altos</text>
  <text x="263" y="122" text-anchor="middle" class="s">Gotas de tinta</text><text x="263" y="146" text-anchor="middle" class="s">líquida</text><text x="263" y="176" text-anchor="middle" class="s">Gran color/foto</text><text x="263" y="200" text-anchor="middle" class="s">Equipo económico</text><text x="263" y="236" text-anchor="middle" class="s">Fotografía y</text><text x="263" y="254" text-anchor="middle" class="s">color de calidad</text>
  <text x="427" y="122" text-anchor="middle" class="s">Agujas de impacto</text><text x="427" y="146" text-anchor="middle" class="s">sobre cinta</text><text x="427" y="176" text-anchor="middle" class="s">Copia por presión</text><text x="427" y="200" text-anchor="middle" class="s">(autocopiativo)</text><text x="427" y="236" text-anchor="middle" class="s">Formularios</text><text x="427" y="254" text-anchor="middle" class="s">multicopia</text>
  <text x="586" y="122" text-anchor="middle" class="s">Calor sobre papel</text><text x="586" y="146" text-anchor="middle" class="s">termosensible</text><text x="586" y="176" text-anchor="middle" class="s">Sencilla, silenciosa</text><text x="586" y="200" text-anchor="middle" class="s">Sin tinta (directa)</text><text x="586" y="236" text-anchor="middle" class="s">Tickets y</text><text x="586" y="254" text-anchor="middle" class="s">etiquetas</text>
  <text x="672" y="312" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: HP-PRINT]</text>
</svg>
```

---

## D8 · Tipos de almacenamiento secundario

**Sección**: §5.1 — Tipos de dispositivos
**Propósito**: Agrupar los soportes por tecnología de grabación.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Tipos de almacenamiento secundario según su tecnología: magnéticos como disco duro y cinta, ópticos como CD DVD Blu-ray, y estado sólido con memoria flash NAND">
  <style>.t{font:700 13px system-ui,sans-serif;fill:#fff}.s{font:11px system-ui,sans-serif;fill:#333}.h{font:700 14px system-ui,sans-serif;fill:#0055a0}.hd{font:700 12px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="26" text-anchor="middle" class="h">Almacenamiento persistente por tecnología de grabación</text>
  <rect x="30" y="50" width="195" height="40" rx="6" fill="#0055a0"/><text x="127" y="75" text-anchor="middle" class="hd">MAGNÉTICO</text>
  <rect x="243" y="50" width="195" height="40" rx="6" fill="#2d8659"/><text x="340" y="75" text-anchor="middle" class="hd">ÓPTICO</text>
  <rect x="456" y="50" width="195" height="40" rx="6" fill="#e89822"/><text x="553" y="75" text-anchor="middle" class="hd">ESTADO SÓLIDO (SSD)</text>
  <rect x="30" y="100" width="195" height="185" rx="6" fill="#eef3f9"/><rect x="243" y="100" width="195" height="185" rx="6" fill="#eef6f0"/><rect x="456" y="100" width="195" height="185" rx="6" fill="#fbf1e2"/>
  <text x="127" y="128" text-anchor="middle" class="s">Polaridad magnética</text><text x="127" y="156" text-anchor="middle" class="s">HDD: platos + cabezal</text><text x="127" y="180" text-anchor="middle" class="s">Cinta (LTO): secuencial</text><text x="127" y="212" text-anchor="middle" class="s">Mucha capacidad</text><text x="127" y="232" text-anchor="middle" class="s">barata; más lento;</text><text x="127" y="252" text-anchor="middle" class="s">partes móviles</text><text x="127" y="274" text-anchor="middle" class="s">Cinta = archivo largo</text>
  <text x="340" y="128" text-anchor="middle" class="s">Lectura con láser</text><text x="340" y="156" text-anchor="middle" class="s">CD ~700 MB</text><text x="340" y="180" text-anchor="middle" class="s">DVD 4,7 GB</text><text x="340" y="204" text-anchor="middle" class="s">Blu-ray 25-100 GB</text><text x="340" y="236" text-anchor="middle" class="s">En retroceso frente</text><text x="340" y="256" text-anchor="middle" class="s">a red y nube</text>
  <text x="553" y="128" text-anchor="middle" class="s">Memoria flash NAND</text><text x="553" y="156" text-anchor="middle" class="s">Sin partes móviles</text><text x="553" y="180" text-anchor="middle" class="s">SATA o NVMe (PCIe)</text><text x="553" y="212" text-anchor="middle" class="s">Muy rápido,</text><text x="553" y="232" text-anchor="middle" class="s">silencioso, resistente</text><text x="553" y="252" text-anchor="middle" class="s">Más caro por GB</text><text x="553" y="274" text-anchor="middle" class="s">NVMe &gt; SATA</text>
  <text x="672" y="312" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: ISO 9660; APFS-NTFS]</text>
</svg>
```

---

## D9 · Niveles RAID más frecuentes

**Sección**: §5.6 — Sistemas de protección y redundancia
**Propósito**: Comparar RAID 0/1/5/6/10 por técnica y tolerancia.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Niveles RAID: RAID 0 striping sin tolerancia, RAID 1 espejo, RAID 5 paridad tolera un fallo, RAID 6 doble paridad tolera dos, RAID 10 espejo más banda">
  <style>.t{font:700 13px system-ui,sans-serif;fill:#fff}.s{font:11px system-ui,sans-serif;fill:#fff}.h{font:700 14px system-ui,sans-serif;fill:#0055a0}.warn{font:700 12px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="26" text-anchor="middle" class="h">Niveles RAID: rendimiento y tolerancia a fallos</text>
  <rect x="24" y="46" width="632" height="52" rx="8" fill="#d13c3c"/><text x="340" y="70" text-anchor="middle" class="t">RAID 0 · Striping (reparto)</text><text x="340" y="88" text-anchor="middle" class="s">Máximo rendimiento · SIN redundancia: si falla 1 disco, se pierde todo</text>
  <rect x="24" y="106" width="632" height="52" rx="8" fill="#0055a0"/><text x="340" y="130" text-anchor="middle" class="t">RAID 1 · Mirroring (espejo)</text><text x="340" y="148" text-anchor="middle" class="s">Copia idéntica · Tolera 1 fallo · Solo el 50 % de capacidad útil</text>
  <rect x="24" y="166" width="632" height="52" rx="8" fill="#2d8659"/><text x="340" y="190" text-anchor="middle" class="t">RAID 5 · Striping + paridad (mín. 3 discos)</text><text x="340" y="208" text-anchor="middle" class="s">Buen equilibrio capacidad/seguridad · Tolera 1 fallo</text>
  <rect x="24" y="226" width="632" height="52" rx="8" fill="#003d73"/><text x="340" y="250" text-anchor="middle" class="t">RAID 6 · Doble paridad (mín. 4 discos)</text><text x="340" y="268" text-anchor="middle" class="s">Como RAID 5 pero tolera 2 fallos simultáneos</text>
  <rect x="24" y="286" width="632" height="42" rx="8" fill="#e89822"/><text x="340" y="313" text-anchor="middle" class="t">RAID 10 (1+0) · Espejo + banda (mín. 4) · Alto rendimiento y fiabilidad</text>
  <text x="672" y="338" text-anchor="end" class="warn">RAID ≠ copia de seguridad</text>
</svg>
```

---

## D10 · La regla 3-2-1 de las copias de seguridad

**Sección**: §5.5 — Copias de seguridad
**Propósito**: Memorizar la regla 3-2-1.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 660 300" role="img" aria-label="Regla 3-2-1 de copias de seguridad: tres copias de los datos, en dos tipos de soporte distintos, con una copia fuera de las instalaciones">
  <style>.t{font:700 34px system-ui,sans-serif;fill:#fff}.tt{font:700 15px system-ui,sans-serif;fill:#fff}.s{font:12px system-ui,sans-serif;fill:#fff}.h{font:700 14px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="330" y="30" text-anchor="middle" class="h">Estrategia mínima de copias de seguridad</text>
  <rect x="40" y="60" width="180" height="180" rx="12" fill="#0055a0"/><text x="130" y="128" text-anchor="middle" class="t">3</text><text x="130" y="168" text-anchor="middle" class="tt">COPIAS</text><text x="130" y="196" text-anchor="middle" class="s">de los datos</text><text x="130" y="216" text-anchor="middle" class="s">(el original + 2)</text>
  <rect x="240" y="60" width="180" height="180" rx="12" fill="#2d8659"/><text x="330" y="128" text-anchor="middle" class="t">2</text><text x="330" y="168" text-anchor="middle" class="tt">SOPORTES</text><text x="330" y="196" text-anchor="middle" class="s">de tipo distinto</text><text x="330" y="216" text-anchor="middle" class="s">(disco + cinta/nube)</text>
  <rect x="440" y="60" width="180" height="180" rx="12" fill="#e89822"/><text x="530" y="128" text-anchor="middle" class="t">1</text><text x="530" y="168" text-anchor="middle" class="tt">FUERA</text><text x="530" y="196" text-anchor="middle" class="s">copia externa</text><text x="530" y="216" text-anchor="middle" class="s">(offsite)</text>
  <text x="330" y="270" text-anchor="middle" class="h">Y verificar periódicamente que la restauración funciona</text>
  <text x="652" y="294" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: buenas prácticas de backup]</text>
</svg>
```

---

## D11 · Modelos de color: RGB aditivo y CMYK sustractivo

**Sección**: §6.3 — Modelos de color
**Propósito**: Oponer el modelo de pantalla al de impresión.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 300" role="img" aria-label="RGB es aditivo y suma luz hasta el blanco, usado en pantallas; CMYK es sustractivo y resta luz con tintas hasta el negro, usado en impresión; CIELAB es la referencia independiente del dispositivo">
  <style>.t{font:700 14px system-ui,sans-serif;fill:#fff}.s{font:12px system-ui,sans-serif;fill:#333}.h{font:700 14px system-ui,sans-serif;fill:#0055a0}.lab{font:700 12px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="26" text-anchor="middle" class="h">Dos formas de construir el color</text>
  <rect x="30" y="46" width="300" height="180" rx="10" fill="#0e0e0e"/>
  <circle cx="130" cy="120" r="46" fill="#ff2d2d" fill-opacity="0.75"/><circle cx="180" cy="120" r="46" fill="#2dff2d" fill-opacity="0.7"/><circle cx="155" cy="160" r="46" fill="#2d6bff" fill-opacity="0.7"/>
  <text x="180" y="72" text-anchor="middle" class="t">RGB · ADITIVO</text><text x="255" y="120" text-anchor="middle" class="s" fill="#fff">Suma luz</text><text x="255" y="150" text-anchor="middle" class="s" fill="#fff">→ blanco</text><text x="180" y="212" text-anchor="middle" class="s" fill="#fff">Pantallas, cámaras, escáneres</text>
  <rect x="350" y="46" width="300" height="180" rx="10" fill="#f4f4f4" stroke="#ccc"/>
  <circle cx="450" cy="120" r="46" fill="#00b6d8" fill-opacity="0.6"/><circle cx="500" cy="120" r="46" fill="#e5008d" fill-opacity="0.55"/><circle cx="475" cy="160" r="46" fill="#ffe000" fill-opacity="0.7"/>
  <text x="500" y="72" text-anchor="middle" class="h">CMYK · SUSTRACTIVO</text><text x="575" y="120" text-anchor="middle" class="s">Resta luz</text><text x="575" y="150" text-anchor="middle" class="s">→ negro (K)</text><text x="500" y="212" text-anchor="middle" class="s">Impresión con tintas</text>
  <rect x="30" y="240" width="620" height="38" rx="8" fill="#6ea3d2"/><text x="340" y="264" text-anchor="middle" class="lab">CIELAB (L·a·b): espacio de referencia independiente del dispositivo para convertir con fidelidad entre ambos</text>
  <text x="672" y="294" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: CIE]</text>
</svg>
```

---

## D12 · Proceso de digitalización certificada (NTI)

**Sección**: §6.6 — El proceso de digitalización certificada
**Propósito**: Encadenar los pasos de la NTI hasta la copia auténtica.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 300" role="img" aria-label="Proceso de digitalización certificada según la Norma Técnica de Interoperabilidad: captura a 200 ppp, optimización y OCR, metadatos, firma o CSV e incorporación al expediente como copia auténtica">
  <style>.t{font:700 12px system-ui,sans-serif;fill:#fff}.s{font:10px system-ui,sans-serif;fill:#fff}.h{font:700 14px system-ui,sans-serif;fill:#0055a0}.n{font:700 12px system-ui,sans-serif;fill:#e89822}.res{font:700 13px system-ui,sans-serif;fill:#2d8659}</style>
  <text x="340" y="26" text-anchor="middle" class="h">De papel a copia auténtica (ENI · NTI de Digitalización)</text>
  <rect x="20" y="70" width="118" height="86" rx="8" fill="#003d73"/><text x="79" y="58" text-anchor="middle" class="n">1</text><text x="79" y="102" text-anchor="middle" class="t">Captura</text><text x="79" y="124" text-anchor="middle" class="s">Escáner</text><text x="79" y="142" text-anchor="middle" class="s">≥ 200 ppp</text>
  <rect x="150" y="70" width="118" height="86" rx="8" fill="#0055a0"/><text x="209" y="58" text-anchor="middle" class="n">2</text><text x="209" y="102" text-anchor="middle" class="t">Optimizar</text><text x="209" y="124" text-anchor="middle" class="s">Recorte, OCR</text><text x="209" y="142" text-anchor="middle" class="s">sin alterar</text>
  <rect x="280" y="70" width="118" height="86" rx="8" fill="#2d8659"/><text x="339" y="58" text-anchor="middle" class="n">3</text><text x="339" y="102" text-anchor="middle" class="t">Metadatos</text><text x="339" y="124" text-anchor="middle" class="s">Mínimos</text><text x="339" y="142" text-anchor="middle" class="s">obligatorios</text>
  <rect x="410" y="70" width="118" height="86" rx="8" fill="#e89822"/><text x="469" y="58" text-anchor="middle" class="n">4</text><text x="469" y="102" text-anchor="middle" class="t">Firma / CSV</text><text x="469" y="124" text-anchor="middle" class="s">Integridad y</text><text x="469" y="142" text-anchor="middle" class="s">autenticidad</text>
  <rect x="540" y="70" width="120" height="86" rx="8" fill="#0055a0"/><text x="600" y="58" text-anchor="middle" class="n">5</text><text x="600" y="102" text-anchor="middle" class="t">Expediente</text><text x="600" y="124" text-anchor="middle" class="s">Archivo</text><text x="600" y="142" text-anchor="middle" class="s">electrónico</text>
  <g stroke="#888" stroke-width="2" marker-end="url(#a12)"><path d="M138 113 L148 113"/><path d="M268 113 L278 113"/><path d="M398 113 L408 113"/><path d="M528 113 L538 113"/></g>
  <defs><marker id="a12" markerWidth="8" markerHeight="8" refX="6" refY="4" orient="auto"><path d="M0 0 L8 4 L0 8 z" fill="#888"/></marker></defs>
  <rect x="120" y="200" width="440" height="46" rx="8" fill="#eef6f0"/><text x="340" y="222" text-anchor="middle" class="res">Resultado: COPIA AUTÉNTICA (art. 27 Ley 39/2015)</text><text x="340" y="240" text-anchor="middle" class="s" fill="#333">con el mismo valor que el original en papel · PDF/A</text>
  <text x="672" y="292" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: RD 4/2010; NTI-DIGIT; L39-2015]</text>
</svg>
```
