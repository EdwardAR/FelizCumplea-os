# Feliz Cumpleaños 🎂

Página web estática de cumpleaños con estilo glassmorphism, confeti animado y burbujas de texto flotantes.

## Estructura del proyecto

```
├── index.html                          ← Página principal (todo el HTML+CSS+JS inline)
├── assets/
│   ├── images/
│   │   ├── Barbie.ico                  ← Favicon / icono decorativo
│   │   └── fotoJhoy.png               ← Foto de la persona (fondo + miniatura)
│   └── audio/
│       └── happyBirthday.mp3           ← Música de fondo (loop)
├── vercel.json                         ← Config de deploy estático
├── AGENTS.md                           ← Instrucciones para OpenCode
└── README.md
```

## Cómo personalizar para otra persona

### 1. Reemplazar archivos multimedia

| Archivo | Descripción |
|---|---|
| `assets/images/fotoJhoy.png` | Foto que aparece al fondo y en miniatura dentro de la tarjeta |
| `assets/audio/happyBirthday.mp3` | Canción de fondo (loop, volumen 0.4) |
| `assets/images/Barbie.ico` | Favicon e icono giratorio (opcional) |

### 2. Editar `index.html`

| Buscar esta línea / sección | Cambiar por |
|---|---|
| `<title>Feliz Cumpleaños ❤️</title>` | Nombre en la pestaña del navegador |
| `.greeting` → `¡Feliz Cumpleaños!` | Saludo principal |
| `.greeting-sub` → `vistima ❤️` | Apodo o texto secundario |
| `.quote` → `Eres una gran persona y nenita dx` | Frase decorativa bajo la foto |
| `messages[]` array | Textos que aparecen en burbujas flotantes |

Ejemplo del array `messages`:

```js
const messages = [
    "Mensaje especial 1 ❤️",
    "Mensaje especial 2 🌟",
    // ...
];
```

También puedes cambiar los colores editando las variables CSS (tonos `#d63384` y derivados).

### 3. Desplegar en Vercel

```bash
npm i -g vercel
vercel --prod
```

No necesita build step — Vercel lo sirve como sitio estático.

## Desarrollo local

Abre `index.html` en cualquier navegador. No necesita servidor ni dependencias.
