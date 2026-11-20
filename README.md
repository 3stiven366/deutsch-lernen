# Deutsch lernen

Material interactivo para estudiar alemán (nivel B1). Cada capítulo de mi libro de clase está convertido en una página web de estudio: gramática explicada en español, ejercicios que se corrigen solos, vocabulario con traducción oculta y tarjetas de repaso.

**Página publicada:** https://3stiven366.github.io/deutsch-lernen/

## Estructura

```
.
├── index.html                                   ← Home: índice de capítulos
├── README.md
└── kapitel/
    ├── kapitel-05-umwelt-wetter.html
    └── kapitel-06-zukunft-ndeklination.html
```

Cada página de capítulo es **un único archivo HTML autocontenido**: lleva dentro su CSS, su JavaScript y todo el vocabulario. No hay build, no hay dependencias que instalar. Se puede descargar y abrir con doble clic sin conexión.

Lo único que se carga desde fuera son las tipografías de Google Fonts; sin internet la página se ve con las fuentes del sistema y todo lo demás sigue funcionando.

## Añadir un capítulo nuevo

1. Copia el archivo del capítulo en `kapitel/`, siguiendo el patrón `kapitel-NN-tema.html` (dos dígitos, minúsculas, sin acentos ni espacios).
2. Abre `index.html` y añade un bloque al principio del array `CHAPTERS`:

```js
{
  num: 7,
  file: "kapitel/kapitel-07-tema.html",
  title: "Título en alemán",
  sub: "Subtítulo con los textos del capítulo",
  topics: ["Tema 1", "Tema 2", "Tema 3"]
},
```

3. Commit y push. GitHub Pages lo publica en un minuto.

El orden de las tarjetas y el contador de capítulos se calculan solos a partir del array, así que no hay que tocar nada más.

## Por qué la lista no se genera automáticamente

Se podría hacer con una GitHub Action que lea la carpeta `kapitel/` y reescriba el índice. No está hecho así por dos razones: los títulos y los temas de cada capítulo no se pueden deducir del nombre del archivo, y una lista cargada desde un `.json` externo rompería la página al abrirla localmente con doble clic, porque el navegador bloquea `fetch()` sobre `file://`.

Con una línea por capítulo, el array inline sale más barato que mantener el automatismo.

## Convenciones de nombres

- Archivos: `kapitel-NN-tema-corto.html`, todo en minúsculas y con guiones.
- `NN` es el número de capítulo del libro, con cero delante para que ordenen bien.
- El tema corto va en alemán o en la forma en que aparece en el libro, sin artículos.

## Licencia y contenido

Proyecto de estudio personal. Las explicaciones, los ejercicios añadidos y las listas de vocabulario son una reelaboración propia a partir del material de clase, no una reproducción del libro.
