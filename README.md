# Futbol Manager · Packs de contenido

Catálogo de packs para **Futbol Manager**. Un pack sustituye los nombres
ficticios que trae la app por los reales y le añade imágenes: escudos de
clubes, caras de jugadores y trofeos.

La app lee el fichero [`index.json`](index.json) de este repositorio y muestra
el catálogo en **Ajustes → Contenido**. Desde ahí se descargan e instalan en el
móvil con un toque.

## Cómo hacer un pack

Un pack es un **ZIP** con un `manifest.json` en la raíz y las imágenes en
carpetas:

```
mi-pack.zip
├── manifest.json
├── logos/
│   ├── rma.png
│   └── fcb.png
├── faces/
│   └── 1001.png
└── trophies/
    └── liga.png
```

### manifest.json

```json
{
  "id": "esp",
  "name": "España",
  "version": 1,
  "author": "tu-usuario",
  "clubs": {
    "Madrid Blanco": {
      "name": "Real Madrid",
      "logo": "logos/rma.png"
    },
    "Cataluña Blaugrana": {
      "name": "FC Barcelona",
      "logo": "logos/fcb.png"
    }
  },
  "players": {
    "Álvaro Segura": "faces/1001.png"
  },
  "trophies": {
    "Primera División": "trophies/liga.png"
  }
}
```

**Las claves son los nombres ficticios que trae la app.** Puedes verlos todos
exportando la plantilla desde **Ajustes → Data Packs → Exportar**: copia el
JSON, y ya tienes la lista de clubes y jugadores de tu liga lista para
rellenar.

| Campo | Para qué sirve |
|---|---|
| `id` | Identificador único. Instalar otro pack con el mismo `id` lo reemplaza. |
| `version` | Súbela al publicar cambios: la app ofrecerá actualizar. |
| `clubs` | Renombra el club y le pone escudo. También vale `"Ficticio": "Real"` si solo quieres renombrar. |
| `players` | Cara del jugador, por su nombre ficticio. |
| `trophies` | Imagen del trofeo, por el nombre de la competición. |

### Imágenes

- **PNG con transparencia**, cuadradas.
- Escudos: 256×256 va sobrado. Caras: 256×256. Trofeos: 512×512.
- Cuanto más ligero, mejor: la app las descarga por red.
- Si falta una imagen, la app usa su escudo monocromo de tres letras. No pasa
  nada por hacer un pack parcial.

## Publicar en el catálogo

1. Sube el ZIP como *release asset* de este repositorio (o a cualquier URL
   pública estable).
2. Añade una entrada a `index.json`:

```json
{
  "id": "esp",
  "name": "España",
  "country": "ESP",
  "author": "tu-usuario",
  "version": 1,
  "size": 4194304,
  "description": "20 escudos de Primera División.",
  "url": "https://github.com/ruben-qa/Futbol-Manager-Packs/releases/download/esp-v1/esp.zip"
}
```

3. Abre un *pull request*. En cuanto se fusione, el pack aparece en la app sin
   necesidad de actualizarla.

## Aviso legal

Los nombres y escudos de clubes y competiciones son marcas de sus titulares, y
la imagen de un jugador le pertenece a él. **La app no distribuye ninguno de
esos materiales**: viene con nombres ficticios y sin imágenes.

Un pack es contenido que una persona prepara y comparte bajo su
responsabilidad. Sube solo material que tengas derecho a distribuir.
