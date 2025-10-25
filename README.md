# Kuorashi Blog - HackTheBox Inspired Theme

Ce site Jekyll utilise un thème personnalisé inspiré du design de HackTheBox.

## 🎨 Caractéristiques du thème

- **Double thème (Clair/Sombre)** : Basculez entre les thèmes avec un bouton animé
- **Palette de couleurs HackTheBox** : Fond sombre (#141d2f) avec accent vert néon (#9fef00)
- **Design moderne** : Cartes avec effets de hover, bordures arrondies, et ombres
- **Responsive** : Optimisé pour mobile, tablette et desktop
- **Typographie tech** : Police moderne avec lettres espacées pour un look cybersécurité
- **Animations** : Effets de glow et transitions fluides
- **Sauvegarde de préférence** : Le thème choisi est sauvegardé dans le navigateur

## 🚀 Installation

```bash
# Installer les dépendances
bundle install

# Lancer le serveur de développement
bundle exec jekyll serve --livereload

# Le site sera accessible sur http://localhost:4000
```

## 📁 Structure

```
.
├── _includes/          # Composants réutilisables (header, footer, social)
├── _layouts/           # Templates de page (default, home, post, page, htb)
├── assets/
│   └── css/
│       └── style.scss  # CSS personnalisé HackTheBox
├── _config.yml         # Configuration Jekyll
└── Gemfile            # Dépendances Ruby
```

## 🎨 Personnalisation

### Couleurs

Les couleurs sont définies dans `/assets/css/style.scss` avec des variables CSS :

```css
:root {
  --htb-green: #9fef00;        /* Vert néon principal */
  --htb-dark-bg: #141d2f;      /* Fond principal */
  --htb-darker-bg: #0f1419;    /* Fond plus sombre */
  --htb-card-bg: #1e2d3d;      /* Fond des cartes */
  --htb-border: #2e3e4e;       /* Bordures */
  --htb-text: #e0e0e0;         /* Texte principal */
  --htb-text-muted: #8b949e;   /* Texte secondaire */
}
```

### Navigation

Modifiez le fichier `_includes/header.html` pour ajouter ou retirer des liens de navigation.

### Thème Clair/Sombre

Le site dispose d'un système de thème avec basculement :

- **Bouton toggle** : Situé dans la barre de navigation (icône 🌙/☀️)
- **Sauvegarde automatique** : La préférence est stockée dans `localStorage`
- **Thème par défaut** : Sombre (HackTheBox style)
- **Personnalisation** : Modifiez les variables CSS dans `:root` et `[data-theme="light"]`

## 📝 Collections

Le site utilise plusieurs collections Jekyll :

- **Posts** : Articles de blog standard
- **Machines** : Write-ups de machines HTB
- **Challenges** : Solutions de challenges HTB
- **Prolabs** : Documentation des Pro Labs HTB
- **About** : Pages À propos
- **CV** : Pages CV

## 🔧 Plugins utilisés

- `jekyll-feed` : Génération de flux RSS
- `jekyll-seo-tag` : Optimisation SEO

## 📱 Responsive Design

Le thème est entièrement responsive avec des breakpoints à 768px pour les appareils mobiles.

## 🎯 Fonctionnalités

- ✅ **Thème clair/sombre** avec bouton toggle animé
- ✅ Thème sombre inspiré de HackTheBox
- ✅ Navigation moderne et responsive
- ✅ Cartes avec filtres pour les machines/challenges HTB
- ✅ Effets de hover et animations
- ✅ Scrollbar personnalisée
- ✅ Badges de difficulté (Easy, Medium, Hard)
- ✅ Code syntax highlighting ready
- ✅ SEO optimisé
- ✅ Icônes sociales SVG (GitHub, LinkedIn)
- ✅ Sauvegarde des préférences utilisateur

## 📄 Licence

Ce thème est libre d'utilisation pour vos projets personnels.

---

**Développé avec ❤️ par kuorashi**
