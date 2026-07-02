# Tema 12 — Changelog

> **Título oficial**: Periféricos: conectividad y administración. Elementos de impresión. Elementos de almacenamiento. Elementos de visualización y digitalización.

---

## v1.0 — 2026-07-02 — Primera versión

**Estado**: pendiente de validación por María y Ana, y de revisión técnica del IAM (Jesús Cuadrado).

**Motivo**: desarrollo del Tema 12, dentro de la serie de temas técnicos generados desde cero, replicando la estructura y el formato del Tema 17 (patrón validado más limpio de la serie), e incorporando **desde el inicio** el `scope_svg` que aísla el CSS de cada diagrama para evitar el bug de colisión de estilos entre los 12 SVG.

### Alcance de la v1.0

| Entregable | Cantidad |
|---|---|
| Contenido teórico | ~11.000 palabras · 6 secciones del esqueleto oficial con ~40 epígrafes |
| Diagramas SVG inline | 12 (accesibles con `role`/`aria-label`, CSS aislado por diagrama) |
| Banco de preguntas tipo test | 60 preguntas A/B/C con explicación y referencia, balanceadas **20/20/20** |
| Casos prácticos | 3 (puesto OAC/conectividad, impresión de distrito, almacenamiento y digitalización) · 10 puntos cada uno |
| Fuentes | Tier 1 (USB-IF, HDMI, VESA, IEEE 802.11, Bluetooth SIG, ISO, CIE, SNIA…) + Tier 2 (Windows/Linux, fabricantes) + Tier 3 (ENI/NTI, Ley 39/2015, ENS, RGPD) |

### Decisiones de generación

1. **Sin material de cliente**: solo el esqueleto `Test_Prompting/temas junio/12.md`. Desarrollado desde especificaciones oficiales y normativa, todas referenciadas.
2. **Estructura fiel al esqueleto oficial**: seis secciones H2 (Tipología, Conectividad, Administración, Impresión, Almacenamiento, Visualización y digitalización). Se **corrigieron las tildes** del esqueleto de partida (Tipología, Tecnologías, electrónica, técnica…) manteniendo el orden oficial, por decisión de Joan.
3. **Bloque de digitalización con anclaje normativo real** (decisión de Joan): la «Norma técnica de interoperabilidad» del índice se desarrolla como la **NTI de Digitalización de Documentos** del **ENI** (RD 4/2010, Resolución de 19-jul-2011): resolución mínima 200 ppp, formatos del catálogo de estándares (PDF/A), metadatos mínimos, firma electrónica/CSV y **copia auténtica** (art. 27 Ley 39/2015), con ejemplo del registro municipal.
4. **Contexto Ayuntamiento de Madrid** en casos y ejemplos (puesto de Oficina de Atención a la Ciudadanía, impresión en red de distrito, archivo y digitalización de expedientes, DNI electrónico, ENS).
5. **Frontera con temas vecinos** cuidada: arquitectura/hardware al T11; ficheros y formatos al T13; sistemas operativos al T14; confidencialidad del puesto al T25; almacenamiento y backup corporativo al T26; administración del SO/drivers al T27; incidencias del puesto al T29; seguridad al T32; comunicaciones al T33/T34; ENI/ENS al T39.
6. **Referencias cruzadas validadas contra BOAM 10.032**: T11, T13, T14, T25, T26, T27, T29, T32, T33, T34, T39. Todas comprobadas.
7. **Bug de colisión de CSS de SVG resuelto de origen**: `build_t12.py` aplica `scope_svg()` a cada diagrama (clase única por SVG), evitando el desbordamiento de texto detectado en T5.

### Pendientes para QA / próxima iteración

- Validación de profundidad por María/Ana/IAM (¿alguna sección a ampliar o recortar?).
- Verificación ortográfica con corrector es_ES (cuidado con falsos positivos por términos técnicos en inglés: driver, spooler, striping, buffer, tóner, firmware…).
- Confirmación por el IAM del dato de resolución mínima (200 ppp) y formatos vigentes del catálogo de estándares de la NTI aplicables al Ayuntamiento.

### Origen

Generado el 2026-07-02 en el flujo de trabajo de eTrivium, replicando el patrón de los Temas 11, 13, 14, 15 y 17. `build_t12.py` y `_build_css.txt` persistidos en el repo.
