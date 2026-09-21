# Xarxa Reviews 2.0 — Responsive + Backend Starter

Interfaz premium-tecnológica adaptable a escritorio, tablet, iPhone y Android. Incluye navegación responsive, resumen, centro de reseñas con búsqueda/filtros, ficha con respuesta editable (demo), Xarxa Brain, exportación CSV y sección de conexión Google.

## Estructura
- `frontend/`: sitio estático para GitHub Pages.
- `backend/`: scaffold FastAPI para desplegar por separado (Cloud Run u otro host HTTPS).

## Publicar frontend en GitHub Pages
1. Sube el contenido de `frontend/` a la raíz del repositorio (index.html, manifest.webmanifest, sw.js).
2. En GitHub: Settings → Pages → Deploy from a branch → `main` → `/(root)` → Save.
3. Cuando Pages publique, abrirá una URL con formato `https://TU-USUARIO.github.io/xarxa-reviews/`.

## Ejecutar backend local (opcional)
Desde la carpeta `backend`:
```bash
pip install -r requirements.txt
uvicorn main:app --reload
```
Health check: `http://localhost:8000/api/health`

## Estado real / limitaciones
- El frontend usa una muestra de reseñas públicas; no es feed en vivo ni garantiza orden por más recientes.
- Los indicadores de rating, volumen, sentimiento y temas están marcados como demostrativos.
- Aprobar una respuesta solo actualiza el estado local; no la publica en Google.
- El backend incluido es un starter explícito: los endpoints de OAuth/sync/reply están pendientes y devuelven errores controlados. No está listo para producción.
- Para conectar Google Business Profile hacen falta acceso aprobado a sus APIs, OAuth 2.0, HTTPS, implementación completa del flujo y almacenamiento seguro de tokens. No expongas secretos en frontend ni en GitHub.
- GitHub Pages solo sirve archivos estáticos; no ejecuta FastAPI.

## Seguridad
No subas archivos `.env` reales, secretos, tokens OAuth ni credenciales. Usa variables de entorno/Secret Manager en el hosting del backend.
