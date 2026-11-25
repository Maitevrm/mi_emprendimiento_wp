# Construcciones Maibru SpA · Sitio WordPress

> **Este README es tuyo.** Complétalo mientras construyes tu sitio y borra las instrucciones entre paréntesis. Las instrucciones del proyecto están en [`indicaciones/README.md`](indicaciones/README.md).

- **Sitio en producción:** https://maitevrm.infinityfree.me/?nocache
- **Prototipo en Stitch:** https://stitch.google.com/projects/8740694174411328170
- **Repo del Parcial 02:** https://github.com/Maitevrm/mi-emprendimiento.git
- **Autor/a:** Maite Ramirez - Sección: 001D

## Contexto de la web

Construcciones Maibru SpA es una empresa familiar de la región de Valparaíso que instala ventanas (PVC, termopanel, aluminio y vidrio templado) y hace remodelaciones de viviendas. Sus clientes son propietarios y personas que quieren renovar su hogar y necesitan a alguien confiable que les dé un presupuesto claro.

El sitio muestra los servicios y los trabajos realizados, y permite contactar rápido por WhatsApp, Instagram o el formulario de contacto. Mi proto-persona es Camila, 38 años, trabajadora independiente y dueña de casa: busca desde el celular, mira fotos de trabajos antes de escribir y quiere una respuesta clara.

## Mi tema

Marca una opción y borra la otra sección de instrucciones.


- [ ] **Tema descargado:** `twenty twenty four` · https://wordpress.org/themes/twentytwentyfour/

---

## Instrucciones si uso un tema descargado

*(Borra esta sección si usas un tema propio.)*

### Requisitos del tema

| Dato | Mi tema |
|---|---|
| Nombre y enlace a la ficha | twenty twenty four - https://wordpress.org/themes/twentytwentyfour/ |
| Gratis o de pago | Gratis |
| Tipo (clásico o de bloques) | De bloques |
| Versión de WordPress que requiere | 6.4 |
| Versión de PHP que requiere | 7.0 |
| Plugins que necesita (si alguno) | |
| Licencia | GPLv2 o posterior |

### Cómo llevar mi sitio de Local a producción

Para migrar el sitio desde el entorno local (**Local WP**) hacia el servidor en producción (**InfinityFree**), se utiliza un plugin de migración que empaqueta toda la web en un único archivo respaldado y reemplaza automáticamente las rutas locales (`localhost`) por el dominio público.

- **Plugin de migración que uso:** All-in-One WP Migration - https://wordpress.org/plugins/all-in-one-wp-migration/ .
- **Gratis o de pago:** Gratis (versión base).
- **Límites que tiene:** La versión gratuita limita el tamaño máximo de importación (generalmente entre 32 MB y 512 MB dependiendo del límite de subida configurado en el servidor de destino; en InfinityFree el límite estándar de subida suele ser de 10 MB a 64 MB por archivo, aunque este plugin fragmenta la subida para evitar bloqueos del servidor).
- **Qué se exporta:** El sitio completo en un archivo `.wpress` que incluye la base de datos (entradas, páginas, menús, usuarios y configuración general), la biblioteca de medios (imágenes y archivos subidos), los temas activos y los plugins instalados.

Pasos:

1. **En Local:** Desde el panel de WordPress en Local WP, instalé y activé el plugin **All-in-One WP Migration**. Luego fui a **All-in-One WP Migration > Exportar**, seleccioné **Exportar a > Archivo** y descargué el paquete `.wpress` generado en mi computador.
2. **En producción:** En el panel de InfinityFree instalé una versión limpia de WordPress mediante Softaculous. Ingresé a `/wp-admin`, instalé y activé el mismo plugin **All-in-One WP Migration**.
3. **Importa:** En el WordPress de producción fui a **All-in-One WP Migration > Importar**, arrastré el archivo `.wpress` descargado desde Local, esperé a que finalizara la carga y confirmé la advertencia de sobrescritura de la base de datos. Al terminar, guardé dos veces la estructura de enlaces permanentes.
4. **Revisa:** Inicié sesión nuevamente (usando las credenciales que tenía en Local), fui a **Ajustes > Enlaces permanentes** y guardé los cambios para regenerar el archivo `.htaccess`. Luego verifiqué en una pestaña de incógnito que el menú de navegación, la página de inicio, las imágenes y el formulario de contacto cargaran correctamente con el dominio `maitevrm.infinityfree.me`.
5. **Problemas que tuve y cómo los resolví:**
   - **Peso excesivo del archivo de exportación:** El respaldo completo superaba el límite de tamaño permitido para la subida en InfinityFree. Lo resolví utilizando las opciones avanzadas del plugin en Local WP para exportar el sitio sin archivos pesados (excluyendo la biblioteca de medios) y subiendo posteriormente los archivos multimedia necesarios de forma manual.
  - **Fallo al actualizar el sitio en Local WP tras importar:** Al intentar pasar la versión actualizada de vuelta a Local WP, repetí el proceso de exportación e importación varias veces, pero el entorno local siguió mostrando la versión inicial antigua sin aplicar los cambios importados. Este problema quedó pendiente de revisión para realizar una limpieza o reinstalación limpia del sitio en Local WP antes de volver a importar el respaldo.
  - - **Diferencia entre vista con sesión iniciada y visitantes externos (caché del servidor):** Al revisar el sitio estando conectada desde WordPress se veían todos los cambios, pero al copiar y pegar el enlace en otro navegador (como visitante) aparecía la versión antigua. Lo solucioné utilizando el parámetro /?nocache al final de la dirección (https://maitevrm.infinityfree.me/?nocache) para omitir la caché del servidor y forzar la carga de la versión actualizada.
---

## Respaldo y reinstalación en otro servidor

El objetivo de este proyecto es que puedas **respaldar tu sitio y reinstalarlo en cualquier servidor**. Explícalo para que otra persona pueda seguir tus pasos.

**Qué respaldar:**

- Los archivos de WordPress (tema, plugins, imágenes subidas).
- La base de datos (páginas, entradas, menús, configuración).

**Cómo respaldo mi sitio:** Utilizo el plugin **All-in-One WP Migration** (`All-in-One WP Migration > Exportar > Archivo`), el cual empaqueta tanto la base de datos como los archivos del sitio en un único fichero con extensión `.wpress`. El respaldo queda guardado inicialmente en el servidor (en `All-in-One WP Migration > Copias de seguridad`) y se descarga localmente en mi computador (y/o almacenamiento en la nube) para conservar una copia externa. Este respaldo se realiza cada vez que se completan cambios importantes en el diseño, estructura o contenido del sitio.

**Cómo lo reinstalo en un servidor nuevo:**

1. **Requisitos del servidor:** PHP 7.4 o superior (mínimo 7.0 requerido por el tema Twenty Twenty-Four), base de datos MySQL 8.0 o MariaDB 10.4 o superior, instalación limpia de WordPress 6.4 o superior, y al menos 200 MB – 500 MB de espacio libre en disco (dependiendo del tamaño del archivo `.wpress` y la descompresión temporal).
2. **Instalar WordPress limpio:** En el nuevo servidor (mediante un autoinstalador como Softaculous o subiendo los archivos de WordPress por FTP y creando una base de datos vacía), se realiza una instalación nueva de WordPress. Luego se ingresa al escritorio (`/wp-admin`) y se instala y activa el plugin **All-in-One WP Migration** (además del tema **Twenty Twenty-Four**).
3. **Restaurar el respaldo:** Dentro del panel del nuevo WordPress, ir a **All-in-One WP Migration > Importar**, arrastrar o seleccionar el archivo `.wpress` previamente descargado, confirmar el aviso de sobrescritura de la base de datos y esperar a que finalice la restauración.
4. **Ajustar:** Iniciar sesión nuevamente usando las credenciales del sitio original respaldado. Ir a **Ajustes > Enlaces permanentes** y hacer clic en **Guardar cambios** dos veces para regenerar el archivo `.htaccess`. Verificar en **Ajustes > Generales** que la **Dirección de WordPress (URL)** y la **Dirección del sitio (URL)** correspondan al nuevo dominio, y comprobar en **Apariencia > Editor** que la página de inicio y el menú de navegación estén asignados correctamente.
5. **Probar:** Abrir el sitio en una ventana de incógnito o navegador distinto para navegar por todas las secciones, comprobar que todas las imágenes carguen sin enlaces rotos, verificar que las URLs internas apunten al nuevo dominio y enviar un mensaje de prueba desde el formulario de contacto confirmando su recepción.

**Problemas que tuve y cómo los resolví:**  
- **Peso excesivo del archivo de exportación:** El respaldo completo superaba el límite de tamaño permitido para la subida en InfinityFree. Lo resolví utilizando las opciones avanzadas del plugin en Local WP para exportar el sitio sin archivos pesados (excluyendo la biblioteca de medios) y subiendo posteriormente los archivos multimedia necesarios de forma manual.
  - **Fallo al actualizar el sitio en Local WP tras importar:** Al intentar pasar la versión actualizada de vuelta a Local WP, repetí el proceso de exportación e importación varias veces, pero el entorno local siguió mostrando la versión inicial antigua sin aplicar los cambios importados. Este problema quedó pendiente de revisión para realizar una limpieza o reinstalación limpia del sitio en Local WP antes de volver a importar el respaldo.
  - - **Diferencia entre vista con sesión iniciada y visitantes externos (caché del servidor):** Al revisar el sitio estando conectada desde WordPress se veían todos los cambios, pero al copiar y pegar el enlace en otro navegador (como visitante) aparecía la versión antigua. Lo solucioné utilizando el parámetro /?nocache al final de la dirección (https://maitevrm.infinityfree.me/?nocache) para omitir la caché del servidor y forzar la carga de la versión actualizada.

## Plugins instalados

| Plugin | Para qué lo uso | Gratis o de pago | Versión |
|---|---|---|---|
| Forminator | Creación y gestión del formulario de contacto del sitio | Gratis | [Ver en Plugins] |
| All-in-One WP Migration | Exportar, respaldar y migrar el sitio entre Local WP y producción | Gratis | [Ver en Plugins] |

## Páginas y entradas

- **Páginas:** Inicio, Sobre nosotros, Blog y Contacto
- **Entradas del blog:** Cierres de terraza con vidrio templado: Ideas para ganar espacio - Claves para planificar la remodelación de tu casa sin sorpresas en el presupuesto: - PVC, Aluminio o Termopanel:¿Cuál conviene mas para tu casa?

## Cómo me organicé

Mi plan y mi plan B están en [`decisiones.md`](proyecto/decisiones.md) (si haces tema propio, está en `proyecto/documentacion/`). (Si cambiaste de rumbo, cuéntalo aquí en una o dos líneas.)

## Plan de continuidad y rendimiento

- **Plan de continuidad (etapa 2 de mi web):** [`plan-de-continuidad.md`](proyecto/plan-de-continuidad.md)
- **Análisis de rendimiento con Lighthouse:** [`lighthouse.md`](proyecto/lighthouse.md)

## Uso de IA

- **(Herramienta):** para qué la usé y qué ajusté yo.
