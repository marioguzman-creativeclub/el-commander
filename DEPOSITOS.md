# Depósitos en EL COMMANDER v0.2

El tablero y su historial Git son públicos. Nada guardado aquí es privado, incluso si se elimina después. Un enlace de Drive también se vuelve público, aunque el archivo conserve sus permisos. No publicar datos personales, conversaciones, nombres de terceros, rutas de archivos privados, credenciales ni material que no haya sido aprobado para ese destino.

## Archivo

Editar `devoluciones.json` en la raíz de `marioguzman-creativeclub/el-commander`, rama `main`. No hace falta editar `index.html` o `feeds.js` para agregar una devolución. Las claves válidas de `agentes` son `coach`, `marie`, `juan`, `maca`, `peter`.

## Entrada

```json
{
  "id": "identificador-unico-estable",
  "titulo": "Título aprobado para el tablero público",
  "fecha": "2026-10-01",
  "resumen": "Resumen corto aprobado para público.",
  "estado": "publicado",
  "link": "https://enlace-verificado",
  "ejemplo": false
}
```

- `id`: obligatorio, único, estable. Una revisión modifica esa entrada, no crea un duplicado.
- `titulo`: obligatorio, hasta 160 caracteres. Preferir menos de 80.
- `fecha`: obligatoria, YYYY-MM-DD, fecha del depósito en Buenos Aires, calculada y verificada. Se muestra sin conversión UTC.
- `resumen`: obligatorio, hasta 1200 caracteres; preferir 1-3 frases y menos de 400.
- `estado`: obligatorio, texto corto. Usar `para leer`, `publicado`, `guardado` o `ejemplo`. El estado describe esa devolución, no la actividad de un proceso automático.
- `link`: opcional. Solo HTTPS, enlace observado y verificado. No inventar URLs. Puede ser repo, fuente pública o documento con permisos revisados. La URL, por sí sola, no vuelve privado el contenido ni autoriza compartirlo.
- `ejemplo`: obligatorio. `true` para muestras, `false` para contenido real autorizado para público.

## Procedimiento

1. Inspeccionar la aprobación original del usuario para publicar el titular, el resumen, la fecha y el enlace. El tablero público no es lugar para toda devolución automáticamente.
2. Si la devolución completa es privada, crearla/actualizarla en Drive privado y verificar sus permisos antes de usar su enlace. No insertar el texto privado en el JSON ni en el commit.
3. Leer el JSON actual de `main`, comprobar si el `id` ya existe y conservar las entradas de los demás agentes.
4. Agregar o actualizar el objeto en el arreglo de su agente. No cambiar `version: 1`. Máximo 100 entradas por agente. Validar la sintaxis JSON, IDs únicos y límites.
5. Guardar un commit sobre `main`. GitHub Pages vuelve a desplegar automáticamente desde `main`, raíz.
6. Verificar el éxito del despliegue, abrir el sitio, recargar y confirmar que la tarjeta está en la pestaña correcta, con texto, fecha y enlace correctos. La página lee el JSON al abrir o recargar, no por polling.
7. Reportar el enlace publicado y las limitaciones. No dar por depositado algo que solo quedó en un borrador o commit sin deploy verificado.

## Estado

Los borradores del formulario siguen siendo locales a la sesión y no son depósitos. No hay servidor, sincronización de borradores ni conexión a WhatsApp. Una carga fallida del JSON muestra un error; las pestañas y herramientas de muestra siguen disponibles. El archivo JSON no ejecuta misiones.
