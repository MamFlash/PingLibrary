[README.md](https://github.com/user-attachments/files/26125870/README.md)
# 🏓 PingLib — Bibliothèque vidéo pour coachs de ping-pong

PingLib est une application web gratuite qui permet à chaque coach de ping-pong de constituer et consulter sa propre bibliothèque de vidéos YouTube. Les vidéos sont organisées par tags personnalisables (niveau, technique, type d'exercice...) et accessibles depuis n'importe quel appareil.

---

## ✨ Fonctionnalités

- **Bibliothèque personnelle** — chaque utilisateur a ses propres vidéos, séparées de celles des autres
- **Ajout de vidéos YouTube** — colle une URL et le titre se remplit automatiquement
- **Tags personnalisables** — crée tes propres catégories et tags pour organiser ta bibliothèque
- **Filtres et recherche** — retrouve une vidéo rapidement par mot-clé ou par tag
- **Lecture intégrée** — regarde les vidéos directement dans l'app sans quitter la page
- **Modification et suppression** — édite ou supprime une vidéo à tout moment
- **Synchronisation multi-appareils** — tes vidéos sont disponibles sur mobile, tablette et desktop
- **Interface claire et lisible** — conçue pour être confortable en plein jour sur mobile

---

## 🚀 Utiliser l'application

L'app est accessible directement en ligne, aucune installation n'est nécessaire.

### Créer un compte

1. Ouvre l'application dans ton navigateur
2. Clique sur l'onglet **Inscription**
3. Renseigne ton adresse e-mail et choisis un mot de passe (minimum 6 caractères)
4. Confirme ton mot de passe et clique sur **S'inscrire**

### Se connecter

1. Ouvre l'application
2. Entre ton e-mail et ton mot de passe
3. Clique sur **Se connecter** — tu retrouves ta bibliothèque sur tous tes appareils

### Ajouter une vidéo

1. Clique sur **+ Ajouter** dans la barre de navigation
2. Colle l'URL d'une vidéo YouTube — le titre se remplit automatiquement
3. Ajoute des notes si tu le souhaites
4. Sélectionne les tags correspondants
5. Clique sur **Ajouter la vidéo**

### Organiser avec des tags

1. Clique sur **⚙ Tags** dans la barre de navigation
2. Crée tes propres catégories (ex : Âge, Matériel, Pays...)
3. Ajoute des tags dans chaque catégorie
4. Les tags sont ensuite disponibles à l'ajout et à la modification de chaque vidéo

---

## 🛠 Stack technique

L'application est un fichier HTML unique, sans framework, sans serveur à gérer.

| Composant | Technologie |
|---|---|
| Interface | HTML, CSS, JavaScript vanilla |
| Authentification | Firebase Authentication |
| Base de données | Firebase Firestore |
| Hébergement | GitHub Pages |
| Polices | Google Fonts (Syne + DM Sans) |

Les données de chaque utilisateur sont stockées de façon isolée dans Firestore — un utilisateur ne peut accéder qu'à ses propres vidéos.

---

## 🔧 Déployer sa propre instance

Tu veux héberger ta propre version de PingLib ? Voici comment faire :

### 1. Créer un projet Firebase

- Va sur [firebase.google.com](https://firebase.google.com) et crée un compte
- Crée un nouveau projet
- Active **Authentication** → **Email/Password**
- Crée une base **Firestore Database** en mode production
- Dans les règles Firestore, colle ceci :

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

### 2. Récupérer les clés Firebase

- Dans les paramètres du projet, enregistre une application Web
- Copie le bloc `firebaseConfig` généré

### 3. Configurer le fichier

- Ouvre `index.html`
- Remplace le bloc `firebaseConfig` existant par le tien

### 4. Déployer sur GitHub Pages

- Crée un dépôt GitHub public
- Dépose le fichier `index.html`
- Active GitHub Pages dans les paramètres du dépôt (Settings → Pages → Branch: main)

---

## 📄 Licence

Projet libre — utilise, modifie et partage librement.
