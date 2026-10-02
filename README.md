# Checkpoint API REST

API REST avec Node.js, Express et Mongoose, connectée à MongoDB Atlas. Elle permet de gérer des utilisateurs (ajouter, lister, modifier, supprimer).

## Prérequis

- [Node.js](https://nodejs.org) installé
- Un cluster MongoDB Atlas (offre gratuite M0)
- [Postman](https://www.postman.com) pour tester les routes

## Installation

```bash
git clone https://github.com/ranim-khemiri/Rest-API.git
cd Rest-API
npm install
```

Créer le fichier `config/.env` :

```
MONGO_URI=mongodb+srv://UTILISATEUR:MOTDEPASSE@cluster0.xxxxx.mongodb.net/checkpoint?retryWrites=true&w=majority
PORT=3000
```

Le fichier `.env` n'est pas envoyé sur GitHub (il est dans `.gitignore`).

## Lancement

```bash
node server.js
```

Le terminal doit afficher :

```
Serveur démarré sur http://localhost:3000
Connecté à MongoDB Atlas
```

## Modèle User

| Champ | Type | Remarque |
|---|---|---|
| `name` | String | obligatoire |
| `email` | String | obligatoire, unique |
| `age` | Number | facultatif |

## Routes de l'API

| Méthode | Route | Description |
|---|---|---|
| GET | `/users` | Retourne tous les utilisateurs |
| POST | `/users` | Ajoute un nouvel utilisateur |
| PUT | `/users/:id` | Modifie un utilisateur par son id |
| DELETE | `/users/:id` | Supprime un utilisateur par son id |

## Exemples de tests (Postman)

Pour POST et PUT : onglet **Body → raw → JSON**.

**POST** `http://127.0.0.1:3000/users`

```json
{ "name": "Alice", "email": "alice@mail.com", "age": 25 }
```

**GET** `http://127.0.0.1:3000/users`

**PUT** `http://127.0.0.1:3000/users/ID`

```json
{ "age": 30 }
```

**DELETE** `http://127.0.0.1:3000/users/ID`

Remplacer `ID` par le `_id` renvoyé par le POST.

## Structure du projet

```
rest-api/
├── config/
│   └── .env          (non envoyé sur GitHub)
├── models/
│   └── User.js
├── server.js
├── .gitignore
└── package.json
```

## Technologies utilisées

- Node.js
- Express
- Mongoose
- MongoDB Atlas
- dotenv

## Auteur

Ranim Khemiri
