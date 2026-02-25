# 🍔 FRAY — APK Android

## Méthode RAPIDE → GitHub Actions (0 install)

### Étape 1 — Mettre le projet sur GitHub
1. Va sur **github.com** → "New repository" → nom: `fray-app`
2. Upload tous ces fichiers (drag & drop)
3. Le build démarre automatiquement !

### Étape 2 — Ajouter les secrets GitHub
Dans ton repo GitHub : **Settings → Secrets → Actions → New secret**
- `KEYSTORE_PASSWORD` = `fray2026`
- `KEY_PASSWORD` = `fray2026`

### Étape 3 — Télécharger l'APK
Onglet **Actions** → dernier build → **Artifacts** → télécharge `FRAY-release.apk`

---

## Méthode locale → Android Studio

1. Installe **Android Studio** (gratuit) depuis developer.android.com
2. Ouvre ce dossier dans Android Studio
3. **Build → Generate Signed Bundle/APK → APK**
4. Utilise le keystore : `keystore/fray-release.keystore`
   - Store password: `fray2026`
   - Key alias: `fray`
   - Key password: `fray2026`

---

## Fichier OBLIGATOIRE à uploader sur le serveur

Uploade `assetlinks.json` dans ce dossier exact sur LWS :
```
/fray/.well-known/assetlinks.json
```
Accessible à : `https://app.kaana-bi.com/.well-known/assetlinks.json`

Ce fichier prouve que ton app Android est liée au site web → l'app s'ouvre SANS barre d'adresse Chrome (vraie app native).

---

## Distribuer l'APK directement (avant Play Store)

Tu peux envoyer l'APK par WhatsApp, email, ou le mettre en téléchargement sur ton site. Les utilisateurs activent "Sources inconnues" dans les paramètres Android pour installer.

---

## Le mois prochain → Play Store

1. Crée un compte **Google Play Console** ($25 une seule fois) : play.google.com/console
2. Uploade l'APK
3. Remplis la fiche (description, captures d'écran, icône 512x512 → voir `ic_launcher_store.png`)
4. Soumets pour review (2-3 jours)

---

## Structure du projet
```
fray-apk/
├── app/
│   ├── build.gradle
│   └── src/main/
│       ├── AndroidManifest.xml      ← Configuration app
│       └── res/
│           ├── mipmap-*/            ← Icônes toutes tailles
│           ├── drawable/splash.png  ← Écran de démarrage
│           └── values/              ← Couleurs, textes
├── keystore/
│   └── fray-release.keystore        ← Clé de signature (GARDE PRÉCIEUSEMENT)
├── assetlinks.json                  ← À uploader sur app.kaana-bi.com/.well-known/
├── ic_launcher_store.png            ← Icône 512x512 pour Play Store
└── .github/workflows/build-apk.yml ← Build automatique GitHub
```
