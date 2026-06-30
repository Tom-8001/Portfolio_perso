# Portfolio Tom Muller

> Site portfolio statique — hébergeable sur GitHub + Vercel
> Thème sombre violet, HTML/CSS/JavaScript vanilla, aucune dépendance externe.

---

## Déploiement rapide

### Vercel (recommandé)
1. Pusher ce dossier sur un dépôt GitHub.
2. Aller sur [vercel.com](https://vercel.com) → New Project → importer le dépôt.
3. Framework preset : **Other** (site statique, pas de build step).
4. Cliquer Deploy.

### GitHub Pages
1. Dans les paramètres du dépôt → Pages → Source : `main` branch, dossier `/root`.
2. Le site est accessible sur `https://VOTRE_USERNAME.github.io/NOM_DU_REPO`.

---

## Structure des fichiers

```
portfolio/
├── index.html                  # Page d'accueil avec hero, stats, projets phares, CTA
├── about.html                  # À propos : bio, skills, timeline, centres d'intérêt
├── projects.html               # Grille filtrée de tous les projets
├── project.html                # Page template détaillée (1 seule page, contenu dynamique via ?id=N)
├── contact.html                # Formulaire Formspree + liens sociaux
│
├── css/
│   ├── main.css                # Variables CSS, reset, typographie, layout, tags, placeholders
│   ├── components.css          # Navbar, boutons, cards projets, filtres, skills, timeline, stats, formulaire, footer, page détail
│   └── animations.css          # Keyframes, reveal au scroll, effets hero, particules, gradient animé
│
├── js/
│   ├── projects.js             # Données centralisées de tous les projets (source unique de vérité)
│   ├── main.js                 # Navbar scroll, active link, burger menu, reveal observer, smooth scroll
│   └── animations.js           # Canvas particules, compteurs animés au scroll
│
└── assets/
    └── images/
        ├── hero/
        │   └── placeholder.svg     # Remplacer par votre photo de profil
        ├── about/
        │   └── placeholder.svg     # Remplacer par votre photo / bannière about
        └── projects/
            ├── project-1.svg       # EQD2/BED RayStation
            ├── project-2.svg       # IA Influenceur Luna
            ├── project-3.svg       # Générateur Shorts YouTube
            ├── project-4.svg       # Bot Trading Crypto
            ├── project-5.svg       # Game Hub WebL3Game
            ├── project-6.svg       # Dungeon Ascension
            ├── project-7.svg       # Tower Defense Procédural
            ├── project-8.svg       # Idle Defense
            ├── project-9.svg       # 7 Wonders Java
            ├── project-10.svg      # ComfyUI + Trellis2 3D
            ├── project-11.svg      # Multi-Agents IA
            ├── project-12.svg      # Dungeon Roguelike Prototype
            └── project-13.svg      # Pipeline Vidéos Courtes IA
```

---

## Personnalisation rapide

### 1. Ajouter vos photos
Remplacer les fichiers `.svg` placeholder par des images réelles :
- `assets/images/hero/placeholder.svg` → votre photo de profil (format carré recommandé)
- `assets/images/about/placeholder.svg` → votre photo / bannière (format 3:4 recommandé)
| `assets/images/projects/project-N.png` → capture d'écran ou visuel de chaque projet

### 2. Mettre à jour vos liens
Rechercher et remplacer dans **tous les fichiers HTML** :
- `VOTRE_USERNAME` → votre username GitHub (ex: `tommuller`)
- `VOTRE_PROFIL` → votre URL LinkedIn (ex: `tom-muller-paris`)
- `votre.email@exemple.com` → votre email réel
- `VOTRE_ID_FORMSPREE` → votre ID Formspree (voir section Formspree ci-dessous)

### 3. Modifier les données projets
Toutes les données des projets sont centralisées dans **`js/projects.js`**.
Pour modifier un projet, éditer l'objet correspondant dans le tableau `PROJECTS`.
Pour ajouter un projet, copier un objet existant et modifier les valeurs.

**Champs disponibles par projet :**
```js
{
  id: 14,                           // ID unique (incrémenter)
  slug: "mon-nouveau-projet",       // URL-friendly (non utilisé actuellement mais prévu)
  title: "Mon Nouveau Projet",
  category: "Catégorie affichée",
  categoryKey: "ia",                // Clé de filtre (ia | jeu | automatisation | medical | java)
  status: "done",                   // done | wip | active
  statusLabel: "Terminé",
  year: "2026",
  context: "Contexte / entreprise",
  image: "assets/images/projects/project-14.svg",
  shortDesc: "Description courte (1-2 phrases)",
  fullDesc: "Description longue pour la page détail",
  features: ["Feature 1", "Feature 2"],
  tags: ["Python", "IA", "..."],
  links: { github: "https://...", demo: "https://..." }
}
```

### 4. Configurer Formspree
1. Aller sur [formspree.io](https://formspree.io) → créer un compte gratuit.
2. New Form → copier l'ID (format `xyzabcde`).
3. Dans `contact.html`, remplacer `VOTRE_ID_FORMSPREE` par cet ID.
4. L'email de destination est configuré dans votre dashboard Formspree.

### 5. Changer les couleurs
Toutes les couleurs sont des variables CSS dans `css/main.css` (section `:root`).
```css
:root {
  --purple-main:   #7c3aed;   /* Violet principal */
  --purple-bright: #a855f7;   /* Violet vif */
  --purple-light:  #c084fc;   /* Violet clair */
  --bg-primary:    #08080e;   /* Fond principal */
}
```

---

## Fonctionnalités

| Fonctionnalité | Implémentation |
|---|---|
| Thème sombre violet | Variables CSS + background grid + orbs |
| Navigation responsive | Navbar fixe + burger menu mobile |
| Filtres projets | JavaScript vanilla, filtrage par catégorie |
| Page détail projet | Template unique `project.html?id=N` |
| Animations au scroll | IntersectionObserver, classes `.reveal` |
| Particules de fond | Canvas 2D animé |
| Compteurs animés | IntersectionObserver + setInterval |
| Compétences avec jauges | CSS transition déclenchée au scroll |
| Timeline parcours | CSS pur + hover effects |
| Formulaire de contact | Formspree (aucun backend requis) |
| Placeholders images | SVG inline indiquant où placer les images |
| Navigation projet prev/next | Calculée depuis le tableau PROJECTS |

---

## Technologies utilisées

- **HTML5** — structure sémantique
- **CSS3** — variables, flexbox, grid, animations, backdrop-filter
- **JavaScript ES6+** — vanilla, modules non nécessaires (simple script tags)
- **Google Fonts** — Inter + JetBrains Mono (via CDN)
- **Formspree** — formulaire de contact sans backend
- **Vercel / GitHub Pages** — hébergement statique gratuit

---

## Navigateurs supportés

Chrome 90+, Firefox 90+, Edge 90+, Safari 14+. Aucun polyfill requis.

---

## Auteur

Tom Muller — Étudiant L3 MIAGE — Nice/Carros 2026
