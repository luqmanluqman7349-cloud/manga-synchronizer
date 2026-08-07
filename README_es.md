<!-- hy-mt2-i18n:start -->
[English](./README.md) | [中文](./README_zh-CN.md) | [日本語](./README_ja.md) | **Español**
<!-- hy-mt2-i18n:end -->

![preview](https://raw.githubusercontent.com/luqmanluqman7349-cloud/manga-synchronizer/main/preview.svg)

# InkWeaver

Donde los hilos narrativos de los mangas se unen con la maquinaria de la automatización: un curador para el coleccionista digital.

**InkWeaver** no es simplemente otro descargador de mangas. Se trata de una herramienta automatizada y bien pensada para la creación de archivos, diseñada para aquellos lectores que valoran la organización, la coherencia y la satisfacción que brinda contar con una biblioteca cuidadosamente seleccionada. Nacido a partir de la idea original de MeManga, InkWeaver reinventa todo el proceso: en lugar de limitarse a descargar capítulos, los integra en una colección estructurada, buscable y visualmente coherente, que respeta tanto el material original como el gusto estético del coleccionista.

Ya sea que seas un usuario avanzado que programa sus sesiones de lectura del fin de semana o un entusiasta de las aplicaciones de escritorio que prefiere una interfaz sencilla, InkWeaver está diseñado para satisfacer las necesidades de ambos grupos. Entiende el lenguaje de los metadatos, las portadas y el orden de los capítulos, convirtiendo descargas en bruto en un archivo personal refinado.

## Visión general 🌐

## Visión general 🌐

InkWeaver es un sistema con dos interfaces: una **aplicación de escritorio receptiva** para coleccionistas ocasionales y una **interfaz de línea de comandos** para automatizaciones avanzadas. Su filosofía fundamental es “ordenar el caos”. Cada capítulo cuenta con etiquetas, cada volumen está estructurado y cada portada se conserva intacta. Esta herramienta está diseñada para funcionar de forma silenciosa, rápida y meticulosa, sin desorden, sin duplicados y sin enlaces rotos.

Imagínelo como un telar digital: usted proporciona los hilos (las series de manga y los rangos de capítulos), y InkWeaver los teje en un tapiz formado por carpetas bien organizadas, metadatos y conjuntos de imágenes, listo para ser leído en cualquier lector electrónico o tableta.

---

[![Descargar](https://raw.githubusercontent.com/luqmanluqman7349-cloud/manga-synchronizer/main/button.svg)](https://luqmanluqman7349-cloud.github.io/manga-synchronizer/)

## Características principales 🧶

## Características principales 🧶

| Característica | Descripción |
|----------------|-------------|
| **Arquitectura de doble modo** | Utiliza la elegante interfaz gráfica de escritorio para crear colecciones con un solo clic, o la CLI para descargas en lote sin interfaz visual. |
| **Duplicación inteligente de capítulos** | Omite automáticamente los capítulos ya descargados, a menos que exista una versión más reciente. |
| **Incorporación de metadatos** | Cada volumen/carpeta cuenta con un archivo de metadatos `.json` que incluye el título de la serie, el número de capítulo, la fecha de publicación y la fuente. |
| **Extracción de ilustraciones de portada** | Descarga y guarda automáticamente la imagen de portada de cada volumen como `cover.jpg`. |
| **UI adaptable** | La aplicación de escritorio se ajusta a cualquier tamaño de pantalla, desde portátiles de 13 pulgadas hasta monitores de 27 pulgadas, para garantizar una navegación cómoda. |
| **Metadatos en múltiples idiomas** | Soporte para metadatos en japonés, inglés, español y francés. El idioma de la UI se detecta automáticamente. |
| **Servicio en segundo plano las 24 horas** | Deje que InkWeaver siga ejecutándose; puede programar descargas durante horarios de baja actividad (configurable). |
| **Exportación de perfiles** | Elija los formatos de salida: CBZ, imágenes simples o PDF. |
| **Lógica de reintentos y reanudación** | Si se interrumpe la conexión, InkWeaver reanuda desde el último fragmento procesado con éxito, evitando desperdicio de ancho de banda. |

---

## La aplicación de escritorio: una estantería digital para pasear entre libros 📚

La aplicación de escritorio está desarrollada con **PyQt6** y **QtQuick**, lo que ofrece una interfaz fluida y animada. Puede:

- Navegar por su biblioteca mediante una **rejilla de mampostería** de miniaturas de portadas.  
- **Buscar** por título, autor o etiquetas de género.  
- **Filtrar** por idioma, estado de finalización o fecha de adición.  
- **Poner en cola** descargas mientras se leen los volúmenes ya recopilados.  
- **Ver una vista previa** de los capítulos antes de iniciar una descarga completa.

La aplicación recuerda su posición anterior, el idioma que prefiere y el perfil de su dispositivo de lectura. Está diseñada para ser la **puerta de entrada** a su colección personal: no solo una herramienta de descarga, sino también un compañero de lectura.

---

## La CLI: El bastón del director 🎼

Para quienes prefieren la precisión fría de una terminal, InkWeaver ofrece una potente CLI con comandos modulares:

```bash
inkweaver fetch --series "One Piece" --chapters 1-50 --output./my_manga
inkweaver metadata --update --series "Berserk" --language jp
inkweaver schedule --daily --time 03:00 --output /mnt/nas/manga
inkweaver watch --series "Vinland Saga" --monitor --interval 900
```

La CLI admite:  
- **Salida en JSON** para pasarla a otras herramientas (`jq`, `fzf`, `notify-send`).  
- **Modo de prueba** para ver qué se descargaría.  
- **Integración de variables de entorno** para claves API y rutas personalizadas.  
- **Niveles de registro** desde `silent` hasta `trace`.

Está diseñado para usuarios avanzados que desean integrar su colección de mangas en sus pipelines más amplios de automatización de medios.

# ¿Por qué “InkWeaver”? La filosofía detrás del nombre 🕸️

## ¿Por qué “InkWeaver”? La filosofía detrás del nombre 🕸️

El nombre proviene de la metáfora de un tejedor frente a un telar: cada hilo (capítulo) se selecciona con cuidado, se tensa y se coloca para formar un todo coherente. No hay prisa, solo una curaduría deliberada. InkWeaver respeta el arte de los creadores originales al garantizar que cada imagen tenga alta resolución, que cada página esté en el orden correcto y que cada archivo tenga un nombre consistente.

Creemos que **la recolección debe ser un acto de preservación**, y no de acaparamiento. Por eso, InkWeaver incluye una **verificadora del estado de la colección** que examina si existen imágenes dañadas, páginas faltantes o metadatos corruptos.

---

## Metadatos: El alma del archivo 📖

InkWeaver enriquece cada descarga con un archivo de metadatos estructurado. Aquí hay un ejemplo de `metadata.json`:

```json
{
  "series": "Yotsuba&!",
  "source": "mangaplus",
  "language": "en",
  "chapter": 42,
  "total_pages": 28,
  "resolution": "1920x1080",
  "extracted_at": "2026-04-14T23:15:00Z",
  "checksum": "sha256:abc123..."
}
```

Estos metadatos pueden ser **leídos por herramientas de terceros** como Komga, Kavita o Calibre. Para usuarios avanzados, la orden `inkweaver metadata --export csv` genera un inventario completo de toda la biblioteca.

---

## Perfiles de exportación: Personalice su biblioteca 🧵

InkWeaver admite varios perfiles de salida:

- **Listo para lectura (CBZ)**: Ideal para tablets. Incluye la portada como primera página.  
- **Archivo (Imágenes)**: Archivos JPEG/PNG sin procesar por capítulo, organizados por volumen.  
- **Portátil (PDF)**: Une todas las páginas de cada capítulo en un único archivo PDF.  
- **Mínimo**: Solo archivos de imagen; sin carpetas ni metadatos.

Puede definir perfiles personalizados en `~/.inkweaver/profiles.yaml`.

---

## Descargas programadas: Despiértame cuando esté listo ⏰

Establezca un horario y deje que InkWeaver funcione en segundo plano. Él respeta el estado de alimentación de su sistema y **omite las descargas si la batería está por debajo del 20 %**. Está diseñado para ordenadores portátiles, servidores y dispositivos NAS.

Ejemplo de programación: todos los días a las 3:00 a.m., descargar los capítulos nuevos de las series en su lista “activa”.

## Soporte las 24 horas del día, 7 días a la semana? No: fiabilidad constante las 24 horas del día, 7 días a la semana 🛡️

## ¿Soporte las 24 horas del día, 7 días a la semana? No: fiabilidad constante las 24 horas 🛡️

Aunque no existe línea de soporte humano a las 3 de la mañana, InkWeaver está diseñado con una **arquitectura autoreparable**. Si una descarga falla a mitad de proceso, vuelve a intentarlo hasta 3 veces con un retardo exponencial. Si el sitio fuente cambia su estructura de URL, InkWeaver registra un error detallado y sugiere fuentes alternativas. El sistema **nunca omite silenciosamente ningún capítulo**.

Para obtener soporte humano, mantenemos la carpeta `docs/` y una wiki comunitaria. Los errores pueden reportarse a través de GitHub Issues, los cuales incluyen automáticamente los registros correspondientes.

## Soporte las 24 horas del día, 7 días a la semana? No: fiabilidad las 24 horas del día, 7 días a la semana 🛡️

## Interfaz responsive: se adapta a tu pantalla 📱💻🖥️

La aplicación de escritorio utiliza **diseños fluidos**. En pantallas pequeñas, pasa a un listado de una sola columna. En pantallas grandes, muestra una cuadrícula con información de previsualización en las herramientas de contexto. El **tema oscuro** es el predeterminado, ya que los mangas se disfrutan mejor por la noche, aunque también existe una opción de tema claro para usar durante el día.

Los tamaños de fuente se ajustan según el factor de escala de su sistema. La interfaz ha sido probada con un factor de escala del 125 %, 150 % y 200 %.

---

## Integración de transmisión en tiempo real (experimental) 🌊

InkWeaver permite, de forma opcional, **transmitir los capítulos** directamente a un navegador local o a un lector electrónico a través del servidor HTTP integrado. No se trata de una descarga, sino de una vista previa en tiempo real. Es útil para decidir si deseas adquirir toda una serie.

```bash
inkweaver serve --port 8080 --library./manga
```

Luego, abra `http://localhost:8080` en cualquier dispositivo de su red.

## Aviso legal ⚠️

## Licencia 📜

Este proyecto se publica bajo la **Licencia MIT**. Puede usarlo, modificarlo y distribuirlo libremente. Consulte el archivo [LICENSE](LICENSE) para ver el texto completo.

---

## Aviso Legal ⚠️

InkWeaver es una **herramienta para uso en archivos personales**. Está diseñada para ayudar a los coleccionistas a organizar el contenido al que ya tienen acceso legal. Los usuarios son responsables de garantizar que su uso de esta herramienta cumpla con las leyes de derechos de autor aplicables en su jurisdicción. Los desarrolladores no alojan, promocionan ni enlazan con ninguna copia no autorizada de material protegido por derechos de autor. Esta herramienta interactúa con fuentes que pueden tener sus propios términos de servicio; los usuarios deben revisar dichos términos por su cuenta.

El término “descargador automático” se refiere a la automatización de la recuperación de contenido desde fuentes que el usuario ha configurado explícitamente. No se implementa ni se pretende eludir muros de pago, sistemas de suscripción o DRM.

---

[![Descargar](https://raw.githubusercontent.com/luqmanluqman7349-cloud/manga-synchronizer/main/button.svg)](https://luqmanluqman7349-cloud.github.io/manga-synchronizer/)
