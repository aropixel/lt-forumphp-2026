# La boîte à outils qu'on ne réinvente plus

Lightning talk (5 minutes) pour le **Forum PHP 2026** — la suite de bundles Symfony
d'Aropixel : une toolbox éprouvée, utilisée sur tous nos projets, et prête pour les
agents IA. Propulsé par [Slidev](https://sli.dev), avec le thème « Terminal » de la
conférence AFUP du même jour (`afup-conf-2026`, « La lucidité comme architecture »), pour
que les deux présentations aient le même habillage.

Pour lancer le diaporama :

```bash
npm install
npm run dev
```

Puis ouvrir <http://localhost:3030>. Le mode présentateur (avec les notes orateur) est
sur <http://localhost:3030/presenter/>.

Pour exporter en PDF :

```bash
npm run export
```

## Structure

- `slides.md` — tout le contenu. Les notes orateur sont entre `<!-- -->` sous chaque
  slide.
- `terminal/` — thème Terminal repris de `afup-conf-2026` : canvas 1920×1080,
  JetBrains Mono, barre `[aropixel] <section>` en haut (frontmatter `section:` et
  `speakers: [joel]` sur chaque slide). Layouts `cover`, `default`, `statement`
  (`dark: true` pour le fond noir), classes `tight` (slides à image) et `compact`
  (titre réduit). Les styles propres au LT (blocs de code, `.cards`, `.ask`, `.files`)
  sont à la fin de `terminal/styles/layout.css`.
- `assets/` — captures réelles de l'AdminBundle (catalogue de composants, color picker,
  édition de collection), réutilisées depuis `doc/assets/` du dépôt `admin-bundle`.
- `public/logo-aropixel.svg` — logo, extrait du header d'aropixel.com.

## Timing

9 slides pour 5 minutes chrono — environ 30 à 35 secondes par slide en moyenne.
