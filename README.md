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
