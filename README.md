# Atelier Docker – Les bases

Cet atelier sert à mettre en place votre environnement de travail (**GitHub Codespaces**) et à lancer votre premier conteneur **Docker**.

**Objectif final :** publier un petit serveur web (Apache httpd) qui affiche **« It works! »** et partager son URL publique.

---

## Prérequis

- Un navigateur web récent (Chrome, Firefox, Edge…)
- Une adresse e-mail valide pour créer un compte GitHub

Vous n'avez **rien à installer** sur votre machine : Codespaces fournit un environnement Linux en ligne, avec Docker déjà installé.

---

## Étape 1 – Créer un compte GitHub

1. Rendez-vous sur [https://github.com](https://github.com).
2. Cliquez sur **Sign up** et suivez les instructions.
3. Validez votre adresse e-mail.

> Si vous avez déjà un compte GitHub, passez directement à l'étape 2.

---

## Étape 2 – Forker le repository de l'atelier

Un *fork* est une copie d'un repository dans votre propre compte GitHub. Vous pourrez y travailler librement, sans modifier le repository d'origine.

1. Une fois connecté, rendez-vous sur le repository de l'atelier : [https://github.com/bstocker/Atelier_Docker_Bases](https://github.com/bstocker/Atelier_Docker_Bases).
2. Cliquez sur le bouton **Fork** (en haut à droite).
3. Laissez votre compte comme **Owner** et le nom du repository inchangé.
4. Cliquez sur **Create fork**.

Vous êtes maintenant sur **votre copie** du repository (l'adresse est de la forme `https://github.com/<votre-pseudo>/Atelier_Docker_Bases`).

> ⚠️ Pour la suite de l'atelier, travaillez toujours depuis **votre fork**, et non depuis le repository d'origine.

---

## Étape 3 – Lancer un Codespace

1. Sur la page de **votre fork**, cliquez sur le bouton vert **Code**.
2. Sélectionnez l'onglet **Codespaces**.
3. Cliquez sur **Create codespace on main**.

Patientez quelques instants : un éditeur VS Code s'ouvre dans votre navigateur.

---

## Étape 4 – Ouvrir le terminal

Le terminal se trouve normalement en bas de l'écran. S'il n'est pas visible :

- Menu **☰** → **Terminal** → **New Terminal**
- ou raccourci clavier : `Ctrl` + `` ` ``

Vérifiez que Docker est bien disponible :

```bash
docker --version
```

---

## Étape 5 – Lancer votre premier conteneur Docker

Dans le terminal, tapez la commande suivante :

```bash
docker run -d -p 80:80 quay.io/ocp-edge-qe/httpd
```

Explication de la commande :

| Élément                       | Signification                                                                 |
|-------------------------------|-------------------------------------------------------------------------------|
| `docker run`                  | Crée et démarre un nouveau conteneur                                          |
| `-d`                          | Mode *détaché* : le conteneur tourne en arrière-plan                          |
| `-p 80:80`                    | Redirige le port 80 du Codespace vers le port 80 du conteneur                 |
| `quay.io/ocp-edge-qe/httpd`   | L'image à utiliser (un serveur web Apache), téléchargée depuis le registre Quay |

Vérifiez que le conteneur tourne :

```bash
docker ps
```

Vous devez voir une ligne avec l'image `quay.io/ocp-edge-qe/httpd` et le statut `Up`.

---

## Étape 6 – Rendre votre site web public

1. Ouvrez l'onglet **PORTS** (à côté de l'onglet **TERMINAL**).
2. Repérez la ligne correspondant au port **80**.
3. Faites un **clic droit** sur la ligne → **Port Visibility** → **Public**.
4. Cliquez sur l'URL (colonne **Forwarded Address**) pour ouvrir votre site.

Vous devez voir la page **« It works! »**.

---

## ✅ Travail demandé

Copiez l'URL de votre site web (celle qui affiche **« It works! »**) et collez-la dans le salon **#général** du Discord.

---

> ⚠️ Pensez à **arrêter votre Codespace** quand vous avez terminé (bouton vert **Code** → onglet **Codespaces** → **…** → **Stop codespace**) afin de ne pas consommer inutilement votre quota d'heures gratuites.
