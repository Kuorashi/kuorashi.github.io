# Configuration de votre profil

## 📸 Ajouter votre photo de profil

1. **Préparez votre photo** :
   - Format recommandé : JPG ou PNG
   - Dimensions : 300x300px minimum (carré de préférence)
   - Poids : < 500KB pour un chargement rapide

2. **Placez votre photo** :
   ```bash
   # Copiez votre photo dans le dossier assets/images/
   cp /chemin/vers/votre/photo.jpg assets/images/profile.jpg
   ```

3. **Ou modifiez le chemin dans _config.yml** :
   ```yaml
   author:
     avatar: /assets/images/votre-nom-de-photo.jpg
   ```

## ✏️ Personnaliser vos informations

Éditez le fichier `_config.yml` et modifiez la section `author` :

```yaml
# Profile Information
author:
  name: kuorashi                              # Votre pseudo
  avatar: /assets/images/profile.jpg          # Chemin vers votre photo
  bio: Cybersecurity Enthusiast | Pentester   # Votre bio courte
  location: France                            # Votre localisation
  education: École d'Ingénieur en Cybersécurité  # Votre formation
  work: Pentester & Red Team Operator         # Votre travail
  interests: "HackTheBox | CTF | Red Team"    # Vos centres d'intérêt
```

## 🎨 Personnalisation avancée

### Modifier les icônes

Les icônes sont des SVG dans `_layouts/home.html`. Vous pouvez :
- Changer les icônes (cherchez "profile-icon")
- Ajouter de nouveaux champs
- Modifier l'ordre des informations

### Modifier le style

Le CSS se trouve dans `assets/css/style.scss` :
- `.profile-section` : Carte principale
- `.profile-avatar` : Photo de profil
- `.profile-name` : Nom/pseudo
- `.profile-bio` : Biographie
- `.profile-item` : Badges d'information

### Exemples de modifications

**Changer la taille de la photo** :
```scss
.profile-avatar {
  width: 200px;  // Au lieu de 150px
  height: 200px;
}
```

**Changer la couleur de la bordure** :
```scss
.profile-avatar {
  border: 4px solid #ff0055;  // Rouge au lieu de vert
}
```

## 🚀 Après les modifications

1. Sauvegardez vos fichiers
2. Le site se régénère automatiquement avec LiveReload
3. Rafraîchissez votre navigateur si nécessaire

## 📝 Note importante

Si vous modifiez `_config.yml`, vous devez **redémarrer le serveur Jekyll** :

```bash
# Arrêter le serveur (Ctrl+C)
# Puis relancer
bundle exec jekyll serve --livereload
```

---

**Besoin d'aide ?** Consultez la documentation Jekyll : https://jekyllrb.com/docs/
