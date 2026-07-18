# Director Studio — Orquestador de Producción de Video

Herramienta gratuita, de un solo archivo, que corre 100% en el navegador. Analiza un guion,
lo divide en escenas y shots, sincroniza los tiempos con un archivo de audio real, y genera los
prompts de imagen (Nano Banana 2) y video (Kling 2.5) listos para pegar en Magnific.

**No necesita instalación, cuenta, ni servidor.** Es un solo archivo `index.html` — se abre y
funciona.

## Qué hace

1. **Guion** → lo analiza y lo divide en escenas y personajes.
2. **Audio** → subes tu narración grabada, mide la duración real y propone shots (A-roll/B-roll)
   sincronizados exactamente con esos segundos — no con una estimación.
3. **Personajes** → ficha de cada uno (físico, vestuario, voz, personalidad) con imagen de
   referencia o ID de asset de Magnific para mantener consistencia.
4. **Shots** → genera el prompt de imagen inicial, imagen final y video de cada shot.
5. **Edición** → línea de tiempo del corte completo.
6. **Exportar** → CSV/Excel para tu hoja de producción, guion limpio para ElevenLabs, o JSON
   completo del proyecto.

Todo el proyecto se guarda automáticamente en tu navegador (no se pierde al cerrar la pestaña).

## Cómo usarlo

1. Abre `index.html` (doble clic, o el link publicado si está en GitHub Pages).
2. Click en **"Configura tu API key de Anthropic"** (arriba) y pega tu propia llave.
   - ¿No tienes una? Consíguela gratis en [console.anthropic.com/settings/keys](https://console.anthropic.com/settings/keys).
   - Tu llave se guarda **solo en tu navegador** (localStorage). Nunca se envía a ningún
     servidor — esta herramienta no tiene backend, todo corre en tu equipo. Las llamadas van
     directo de tu navegador a la API de Anthropic.
   - Anthropic cobra por uso de API (no es lo mismo que una suscripción a Claude.ai). Revisa sus
     precios antes de usarlo a fondo.
3. Pega tu guion en la pestaña **Guion** y dale "Analizar guion".
4. Sube tu audio en la pestaña **Audio** para sincronizar tiempos reales (opcional, pero
   recomendado).
5. Revisa personajes y shots, genera los prompts, y exporta.

## Sobre la generación de imágenes ("Generar img")

El botón de generar imagen dentro de cada shot usa el conector MCP de Magnific a través de la
API de Anthropic. Para que funcione, tu cuenta/llave de Anthropic necesita tener acceso a ese
conector. Si no te funciona, puedes copiar el prompt generado (botón "Copiar") y pegarlo
manualmente en Magnific — el resto de la herramienta (guion, shots, sincronía de audio, export)
funciona igual sin depender de esto.

## Publicar en GitHub Pages (para compartirlo con un link)

1. Sube este archivo a un repositorio en GitHub.
2. Ve a **Settings → Pages** del repo.
3. En "Source", elige la rama (`main`) y la carpeta raíz (`/`).
4. Guarda. En 1-2 minutos tu herramienta queda publicada en
   `https://tu-usuario.github.io/nombre-del-repo/`.

Cualquiera que abra ese link puede usarla con su propia API key — nunca consume créditos ni
tokens tuyos.

## Notas técnicas

- Un solo archivo HTML, sin paso de compilación (React + Babel + Tailwind vía CDN).
- Sin backend, sin base de datos — todo el estado vive en `localStorage` del navegador de cada
  usuario.
- La transcripción automática de audio usa la Web Speech API del navegador (funciona mejor en
  Chrome/Edge); si no está disponible, puedes pegar la transcripción a mano.
