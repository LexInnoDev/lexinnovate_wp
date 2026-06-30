# Deploy en Vercel

El proyecto está preparado como un sitio Astro estático.

## Versiones fijadas

- Node.js: `24.x`
- npm: `11.18.0`
- Astro: `7.0.4`

Vercel toma Node 24 desde `package.json`. Los archivos `.nvmrc` y
`.node-version` mantienen la misma versión en entornos locales compatibles.

## Configuración de Vercel

`vercel.json` define explícitamente:

- Framework: Astro
- Instalación reproducible: `npx --yes npm@11.18.0 ci`
- Build: `npm run build`
- Directorio publicado: `dist`
- Caché inmutable para assets generados en `/_astro/`
- Cabeceras HTTP básicas de seguridad

No se instala `@astrojs/vercel`: la página usa `output: "static"` y no necesita
funciones, SSR ni un adaptador.

## Variables de entorno

La página puede desplegarse sin variables obligatorias. Para habilitar
integraciones opcionales, crea las variables necesarias de `.env.example` en:

`Vercel → Project Settings → Environment Variables`

Configúralas para Production y Preview según corresponda:

- `PUBLIC_GA_MEASUREMENT_ID`
- `PUBLIC_GOOGLE_SITE_VERIFICATION`
- `PUBLIC_BING_SITE_VERIFICATION`
- `PUBLIC_X_HANDLE`
- `PUBLIC_LINKEDIN_URL`
- `PUBLIC_FACEBOOK_URL`
- `PUBLIC_INSTAGRAM_URL`

Las variables `PUBLIC_*` se incorporan durante el build. Después de cambiarlas,
es necesario generar un nuevo deployment.

## Deploy

### Desde Git

1. Importa el repositorio en Vercel.
2. No sobrescribas Framework Preset, Build Command ni Output Directory.
3. Añade las variables opcionales.
4. Ejecuta el deployment.

### Desde CLI

```bash
npx vercel
npx vercel --prod
```

## Verificación local limpia

Con Node 24 activo:

```bash
npx --yes npm@11.18.0 ci
npm run build
```
