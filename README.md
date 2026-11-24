# Alabanza Preview

Vista previa de la aplicación Android en desarrollo. Publicación automática desde `joshuagg86/alabanza`, rama `feature/android-blue-app`.

Actualización: interfaz azul de alto contraste y primer módulo de letras descargadas localmente.

La web de producción (`main` de `alabanza`) no se modifica.

Entrega de prueba: descargas individuales de pads y pistas de ensayo, lector de letras offline y ajustes visuales. Verificar en teléfono antes de uso en servicio.

## Ajustes Android — navegación, pads y lector
- Menú superior duplicado oculto en móvil; Servicios con selector Domingo/Miércoles/Rol.
- Pantalla dedicada de Pads con reproducción y descarga por tono.
- Descargas: botón Ver abre el lector completo.
- Mejor contraste azul y controles del lector.
- Audio cloud Android: la función Supabase requiere autorizar origen https://localhost y redeplegarla.

## QA 2026-11-23
La nueva compilación incluye mejoras del visor de canciones y mensajes descriptivos cuando el servicio de audio privado no permite el origen Android. Pendiente: desplegar el ajuste de Supabase para https://localhost.

## Corrección visual nueva
- Selector de tema integrado junto al logo del encabezado, aviso de sincronización oculto en móvil.
- Contrastes de tema claro corregidos y azules sustituyen a morados legados.
- Logo claro automático cuando exista logo_claro.png en la rama feature/android-blue-app.

## Validación logo y Supabase — 23 noviembre 2026
- Se verificó que `logo_claro.png` y `logo.png` están en `feature/android-blue-app`.
- La compilación Android copia ambos recursos desde la rama de desarrollo.
- Supabase: el usuario confirmó que configuró `ALABANZA_ALLOWED_ORIGINS`; validar acceso desde `https://localhost` al probar una canción publicada en la APK.

## QA audio — 23 noviembre de 2026
- Sólo tema oscuro, sin botón de selección de tema.
- Pads: caché de dos tonos decodificados, pre-carga al seleccionar.
- Mezclador: preparación automática de pistas guardadas, transporte Play/Pausa con iconos.
- Descargar pistas: confirma que ya están descargadas y deshabilita descarga redundante.
- Reproducir después de preparación; la primera decodificación aún puede tardar según RAM y duración.

Ajuste final de audio: precarga de pads bajo demanda, sin decodificar un tono innecesario al iniciar la aplicación.

## Pruebas offline y app icon — 23 nov 2026
- Mensajes Sin conexión para pads y audio privado.
- Catálogo offline filtrado por letras descargadas explícitamente, no sólo caché Firestore.
- Mezclador en popup grande y control de cierre sin pausar el audio.
- Iconos Android generados desde icono-512.png del proyecto.

### Ajuste final del catálogo offline
La pantalla de Inicio también filtra títulos por letras descargadas en modo avión; revisión final incluida en la compilación.

## Ajuste de noviembre 24: letras automáticas y descargas solo audio
- Descargas ya no tiene botones ni listas para letras.
- El repertorio se restaura del archivo privado Android al abrir la app, y se sincroniza al recuperar las canciones Firestore online.
- Actualizado ícono adaptive Android con fondo azul ICEGH (no blanco).
- Modal de Ensayar portado al body para evitar superposición del blur, cierre sin detener el sonido.
- Android: @capacitor/filesystem 8.1.5 registrado para almacenar la biblioteca de letras.

QA: restauración al reiniciar corregida para no sustituir la biblioteca interna por una caché parcial de Firestore.

## Revisión posterior a QA completa — 24 noviembre 2026
- Se confirma que el usuario probó correctamente seis funciones Android: icono, descargas sólo audio, letras persistentes con reinicio, lector offline, mezclador popup y reproducción al cerrar.
- Descargas muestra número de archivos y tamaño total del audio almacenado.
- Se pide confirmación antes de eliminar pads o mezclas descargados.
- Pads y mezclador actualizan automáticamente el indicador descargado al modificar la biblioteca.
- Se mantienen sin cambios la web publicada y el motor de audio estable.

## Diseño móvil compacto — 24 de noviembre 2026
- El lector de canciones en teléfono usa una cabecera compacta y un menú Más para acordes, tamaño de texto, audio rack, edición, velocidad y distribución.
- El título conserva ancho para evitar una letra por línea.
- Ensayo a pantalla completa y mezclador de ensayo se ocultan en smartphones (<768px); tablet y PC conservan esos controles.
- El flujo previo de audio offline y letras persistentes no se modifica.

## 24 noviembre — lector móvil v2
- Todos los controles en una sola fila: tono, canción anterior/siguiente, secciones, autoavance y ajustes.
- El botón de ajustes ahora es un ícono de deslizadores sin texto; panel desplegable flotante a nivel body para evitar recortes y conflictos de z-index.
- La navegación por secciones se superpone a la letra en vez de reducir el ancho de lectura.
- Tablet/PC mantienen diseño original y mezclador. Revisión funcional pendiente en Vivo.

## Interfaz musical fija — 24 noviembre 2026
- Nueva barra fija en el lector de celular: Pads / Metrónomo / Ensayar.
- Pads y Metrónomo tienen paneles individuales, sus controles y volumen horizontal, sin cortar los deslizadores.
- Ensayar restaura el mezclador multipista; el modo de ensayo a pantalla completa continúa deshabilitado solo en teléfono.
- Menú de ajustes superior: Editar canción, Mostrar acordes, Tamaño de letra, Velocidad de lectura.
- Eliminada la fila Distribución y el acceso largo al Audio Rack.
- Pistas de pads no descargadas se consultan desde GitHub Pages cuando Android tiene conexión.
- Reutiliza motor WebAudio y reproducción anterior sin modificar datos ni descargas existentes.
