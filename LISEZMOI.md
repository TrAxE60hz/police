# Casse l'Œuf Géant — appli Android (Noobzik)

Le jeu tourne entièrement hors ligne dans l'appli : joystick pour bouger, planning travail/pause,
basket, café, pointeuse, 6 œufs, 31 pets, boosts, rebirth, roue de la chance.
La progression est sauvegardée sur le téléphone.

## Ce qu'il te faut (une seule fois, sur ton PC Windows)

1. **Node.js** (version LTS) : https://nodejs.org
2. **Android Studio** : https://developer.android.com/studio
   (au premier lancement, laisse-le installer le SDK Android)

## Fabriquer l'APK

Dans ce dossier, ouvre un terminal (clic droit > « Ouvrir dans le terminal ») et tape :

```
npm install
npx cap sync android
npx cap open android
```

Android Studio s'ouvre sur le projet. Attends la fin de « Gradle sync » (barre en bas), puis :

- **Tester sur ton téléphone** : branche-le en USB (options développeur + débogage USB activés),
  choisis-le en haut et clique sur ▶ Run.
- **Fichier APK à installer** : menu **Build > Build App Bundle(s) / APK(s) > Build APK(s)**.
  L'APK se trouve ensuite dans `android/app/build/outputs/apk/debug/app-debug.apk`.

## Publier sur le Play Store

1. Crée un compte développeur Google Play (25 $ une seule fois) : https://play.google.com/console
2. Dans Android Studio : **Build > Generate Signed App Bundle / APK** > Android App Bundle,
   crée une clé de signature (garde-la précieusement, elle sert pour toutes les mises à jour).
3. Envoie le fichier `.aab` dans la Play Console, remplis la fiche (captures, description,
   classification du contenu, public cible : jeu pour enfants = règles « Famille » de Google).

## Modifier le jeu

Tout le jeu est dans `www/index.html`. Après une modification, relance `npx cap sync android`.

- Durée du service / de la pause : `WORK_TIME` et `BREAK_TIME` en haut du script
- Outils, boosts, pets, œufs : tableaux `TOOLS`, `UPGRADES`, `PETS`, `EGGS`
- Nom et identifiant de l'appli : `capacitor.config.json` (`appName`, `appId`)
- Icône : dans Android Studio, clic droit sur `app` > New > Image Asset
