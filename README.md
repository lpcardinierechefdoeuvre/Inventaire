# Inventaire Magasin — Vercel + GitHub + Firebase

## Architecture
- **GitHub** : dépôt des fichiers source.
- **Vercel** : hébergement du site statique.
- **Firebase Firestore** : base de données des articles avec **synchronisation temps réel**.
- Le navigateur conserve aussi une copie locale pour éviter de perdre le travail si Firebase n'est pas encore configuré.

## Mise en ligne
1. Créez un projet Firebase.
2. Activez **Firestore Database**.
3. Dans Firebase > Project settings > Your apps, créez une application Web et récupérez la configuration Firebase.
4. Ouvrez `index.html` et remplacez les valeurs `VOTRE_...` dans `FIREBASE_CONFIG`.
5. Créez un dépôt GitHub et poussez `index.html`, `README.md`, `firebase.rules` et `vercel.json`.
6. Dans Vercel, importez le dépôt GitHub puis déployez.
7. Dans Firebase, publiez les règles présentes dans `firebase.rules`.

## Exports
- CSV
- Excel `.xlsx`
- JSON
- PDF
- Impression navigateur

## Données
La collection Firestore utilisée est `inventaire`. Chaque article utilise son `id` comme identifiant de document.

## Important
La configuration Firebase côté navigateur n'est pas un secret. La sécurité des données doit être assurée par les règles Firestore et, si nécessaire, par Firebase Authentication.

## Synchronisation en direct

L'application utilise le listener Firestore `onSnapshot`. Tous les navigateurs ouverts sur l'application reçoivent automatiquement :
- les nouveaux articles ;
- les modifications ;
- les suppressions ;
- les changements de quantité et de prix.

Il n'est donc pas nécessaire de recharger la page pour voir les changements effectués par un autre utilisateur.


Projet Firebase configuré : `inventaire215`.
