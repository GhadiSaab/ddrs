# Quick Start - Déployer en 5 minutes

## Option la plus simple: Via Vercel CLI

### 1. Installer Vercel CLI

```bash
npm install -g vercel
# Si vous n'avez pas npm, installez-le d'abord: sudo apt install npm
```

### 2. Déployer en une commande

```bash
cd /home/ghadi/Downloads/DDRS_DO2023
vercel --prod
```

C'est tout! Vercel va:
- ✅ Vous demander de vous connecter (via navigateur)
- ✅ Créer le projet automatiquement
- ✅ Déployer votre site
- ✅ Vous donner une URL (ex: https://quiz-ddrs-xxx.vercel.app)

---

## Option avec GitHub (Déploiement automatique)

### 1. Créer un repository GitHub

Allez sur https://github.com/new et créez un nouveau repository nommé `quiz-ddrs`

### 2. Pousser votre code

```bash
cd /home/ghadi/Downloads/DDRS_DO2023

# Initialiser git si pas déjà fait
git init

# Ajouter tous les fichiers
git add .

# Créer le commit
git commit -m "Initial commit: Quiz DDRS"

# Connecter à GitHub (remplacez VOTRE-USERNAME)
git remote add origin https://github.com/VOTRE-USERNAME/quiz-ddrs.git

# Pousser le code
git branch -M master
git push -u origin master
```

### 3. Connecter à Vercel

1. Allez sur https://vercel.com/new
2. Cliquez "Continue with GitHub"
3. Sélectionnez votre repository `quiz-ddrs`
4. Cliquez "Deploy"

**Terminé!** Vercel vous donnera une URL pour votre quiz.

---

## Mises à jour futures

Après le déploiement initial, pour mettre à jour:

### Si vous utilisez GitHub:
```bash
git add .
git commit -m "Update: mes modifications"
git push
# Vercel redéploie automatiquement!
```

### Si vous utilisez CLI:
```bash
vercel --prod
# Redéploie instantanément!
```

---

## Vérifier que tout est prêt

Avant de déployer, vérifiez:

```bash
cd /home/ghadi/Downloads/DDRS_DO2023
ls -la
```

Vous devriez voir:
- ✅ index.html
- ✅ quiz.json
- ✅ vercel.json
- ✅ .gitignore
- ✅ package.json

Si tout est là, vous êtes prêt à déployer! 🚀
