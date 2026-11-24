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
