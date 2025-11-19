# Déploiement du Quiz DDRS sur Vercel

Ce guide vous explique comment déployer votre quiz en ligne gratuitement avec Vercel.

## Prérequis

- Un compte GitHub (gratuit)
- Un compte Vercel (gratuit) - https://vercel.com

## Méthode 1: Déploiement via GitHub (Recommandé)

### Étape 1: Initialiser Git et pousser sur GitHub

```bash
# 1. Initialiser le dépôt Git (si pas déjà fait)
git init

# 2. Ajouter tous les fichiers
git add .

# 3. Créer le premier commit
git commit -m "Initial commit: Quiz DDRS website"

# 4. Créer un nouveau repository sur GitHub
# Allez sur https://github.com/new
# Nommez-le "quiz-ddrs" ou un nom de votre choix
# Ne cochez PAS "Initialize with README"

# 5. Connecter votre dépôt local à GitHub
git remote add origin https://github.com/VOTRE-USERNAME/quiz-ddrs.git

# 6. Pousser le code
git branch -M master
git push -u origin master
```

### Étape 2: Déployer sur Vercel

1. **Créer un compte Vercel**
   - Allez sur https://vercel.com
   - Cliquez sur "Sign Up"
   - Choisissez "Continue with GitHub"
   - Autorisez Vercel à accéder à votre GitHub

2. **Importer votre projet**
   - Cliquez sur "Add New..." puis "Project"
   - Sélectionnez votre repository "quiz-ddrs"
   - Cliquez sur "Import"

3. **Configurer le projet**
   - **Project Name**: quiz-ddrs (ou votre choix)
   - **Framework Preset**: Other
   - **Root Directory**: ./
   - Laissez les autres paramètres par défaut
   - Cliquez sur "Deploy"

4. **Attendre le déploiement**
   - Vercel va construire et déployer votre site (environ 1-2 minutes)
   - Une fois terminé, vous obtiendrez une URL comme: `https://quiz-ddrs.vercel.app`

## Méthode 2: Déploiement Direct via CLI

### Installation de Vercel CLI

```bash
# Installer Vercel CLI globalement
npm install -g vercel

# Ou avec yarn
yarn global add vercel
```

### Déploiement

```bash
# 1. Se connecter à Vercel
vercel login

# 2. Déployer depuis le dossier du projet
cd /home/ghadi/Downloads/DDRS_DO2023
vercel

# Suivez les instructions:
# - Set up and deploy? Yes
# - Which scope? Votre compte
# - Link to existing project? No
# - Project name? quiz-ddrs
# - In which directory is your code located? ./
# - Want to override settings? No

# 3. Déployer en production
vercel --prod
```

## Méthode 3: Déploiement via l'interface Web

1. **Créer une archive ZIP**
```bash
cd /home/ghadi/Downloads/DDRS_DO2023
zip -r quiz-ddrs.zip index.html quiz.json quiz2.json vercel.json .gitignore
```

2. **Uploader sur Vercel**
   - Allez sur https://vercel.com/new
   - Cliquez sur "Browse" et sélectionnez votre fichier ZIP
   - Ou glissez-déposez le fichier ZIP
   - Cliquez sur "Deploy"

## Structure des fichiers nécessaires

Assurez-vous que ces fichiers sont présents:

```
DDRS_DO2023/
├── index.html          # Page principale du quiz
├── quiz.json           # Données des questions
├── quiz2.json          # Données additionnelles
├── vercel.json         # Configuration Vercel
└── .gitignore          # Fichiers à ignorer
```

## Mises à jour automatiques

Avec la Méthode 1 (GitHub), chaque fois que vous poussez du code:

```bash
# Modifier vos fichiers
git add .
git commit -m "Update: description des changements"
git push

# Vercel déploiera automatiquement les changements!
```

## Domaine personnalisé (Optionnel)

1. Allez sur votre projet Vercel
2. Cliquez sur "Settings" > "Domains"
3. Ajoutez votre domaine personnalisé
4. Suivez les instructions pour configurer les DNS

## Variables d'environnement (Si nécessaire plus tard)

Si vous ajoutez des fonctionnalités nécessitant des variables:

1. Projet Vercel > "Settings" > "Environment Variables"
2. Ajoutez vos variables
3. Redéployez le projet

## Dépannage

### Erreur: "quiz.json not found"
- Vérifiez que `quiz.json` est bien dans le même dossier que `index.html`
- Vérifiez qu'il n'est pas dans `.gitignore`

### Le site ne se charge pas
- Vérifiez les logs dans Vercel Dashboard
- Assurez-vous que `index.html` est à la racine du projet

### Changements non visibles
- Videz le cache du navigateur (Ctrl+Shift+R ou Cmd+Shift+R)
- Attendez quelques minutes pour la propagation CDN

## URLs importantes

- **Dashboard Vercel**: https://vercel.com/dashboard
- **Documentation**: https://vercel.com/docs
- **Support**: https://vercel.com/support

## Notes

- Vercel offre un plan gratuit généreux pour les projets personnels
- Les déploiements sont automatiques depuis GitHub
- HTTPS est activé automatiquement
- CDN global pour des performances optimales
- Aucune limite de bande passante sur le plan gratuit
