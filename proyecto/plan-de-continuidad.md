# Plan de continuidad — Construcciones Maibru

- **Sitio web:** https://maitevrm.infinityfree.me/?nocache

## 1. Cómo está el sitio hoy
Actualmente la página funciona como una primera versión operativa en el hosting gratuito de **InfinityFree**, usando WordPress y el tema **Twenty Twenty-Four**. Tiene las secciones principales listas (Inicio, Servicios, Proyectos, Nosotros y Contacto) y el formulario con **Forminator** y **WP Mail SMTP** ya envía correos sin problemas. 

Las principales limitaciones actuales son que, al ser un servidor gratuito, el dominio no es propio (`infinityfree.me`), la carga a veces es lenta, hay restricciones de espacio para subir archivos pesados y en ocasiones el enlace principal tarda en reflejar las actualizaciones recientes o en cargar debido a la caché y estabilidad del hosting gratuito.

## 2. Qué se mejoraría a futuro
- **Corto plazo:** Comprar un dominio propio (`.cl`) y pasar el sitio a un hosting de pago básico para que cargue más rápido, tenga certificado SSL sin problemas y no dependa de límites gratuitos. También optimizar el peso de las fotos de las obras para que abran rápido en el celular.
- **Mediano plazo:** Agregar más fotos reales de trabajos terminados (idealmente con un antes y después) y mejorar el SEO básico con algún plugin gratuito para que la empresa aparezca cuando alguien busque servicios de construcción en la zona.
- **Largo plazo:** Sumar un botón directo de WhatsApp para cotizaciones rápidas y ampliar el formulario de contacto para que el cliente pueda elegir qué tipo de trabajo necesita (remodelación, ampliación, etc.).

## 3. Recursos y presupuesto estimado (etapa real)
Para esta entrega no se gastó nada ($0), pero si el negocio quisiera dejar la página funcionando de forma profesional, necesitaría: 

| Recurso | Para qué sirve | Costo aproximado |
|---|---|---|
| **Dominio `.com` (V2Networks)** | Tener la dirección propia `construccionesmaibru.com` | ~$38.000 al año |
| **Hosting básico WordPress** | Alojar la web con buena velocidad y correo corporativo | ~$35.000 - $50.000 al año |
| **Plugins y tema** | Twenty Twenty-Four, Forminator y WP Mail SMTP (versiones gratis) | $0 |

## 4. Mantenimiento y respaldos
- **Respaldos:** Sacar una copia de seguridad una vez al mes usando **All-in-One WP Migration** y guardar el archivo en Google Drive por si ocurre algún error.
- **Actualizaciones:** Revisar cada cierto tiempo que WordPress, el tema y los plugins estén actualizados.
- **Revisión del formulario:** Probar de vez en cuando el formulario de contacto para asegurarse de que los correos sigan llegando bien.
