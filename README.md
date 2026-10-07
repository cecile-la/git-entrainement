# git-entrainement
Dépôt d'entraînement Git : branches, merge, conflits, rebase sur des fichiers texte.
<!-- Je modifie le readme avant de sauvegarder-->

# Mémo — commandes de la mise en place de git-entrainement

Terminal : Git Bash (MINGW64). Chemins au format `/c/...`.

## Vérifier la configuration de Git

| Commande | Ce qu'elle fait |
|---|---|
| `git config --global user.name` | Affiche le nom qui signera mes commits. `--global` : réglage valable pour tous mes dépôts sur cet ordinateur. |
| `git config --global user.email` | Affiche l'email associé à mes commits. J'utilise l'adresse `noreply` de GitHub pour ne pas exposer ma vraie adresse dans des dépôts publics. |

## Se déplacer et créer des dossiers

| Commande | Ce qu'elle fait |
|---|---|
| `cd /c/Env/Workspace` | Change le dossier courant (*change directory*). |
| `cd git-entrainement` | Entre dans un sous-dossier du dossier courant. |
| `mkdir Exercices-A` | Crée un dossier (*make directory*). |
| `ls` | Liste le contenu du dossier courant. Rien ne s'affiche si le dossier est vide. |

## Récupérer le dépôt et l'ouvrir

| Commande | Ce qu'elle fait |
|---|---|
| `git clone <URL>` | Copie le dépôt GitHub sur mon disque : fichiers + historique complet. Crée un dossier du nom du dépôt et enregistre l'adresse du dépôt distant sous le nom `origin`. |
| `code .` | Ouvre VS Code sur le dossier courant (`.` = « ici »). |

## Vérifier l'état du dépôt

| Commande | Ce qu'elle fait |
|---|---|
| `git status` | Indique la branche courante, si je suis à jour avec `origin`, et les fichiers modifiés ou non suivis. |
| `git remote -v` | Liste les dépôts distants connus et leurs adresses (`-v` : *verbose*, affiche les URL). Deux lignes `origin` : une pour récupérer (*fetch*), une pour envoyer (*push*). |
| `git diff` | Montre les modifications pas encore ajoutées avec `git add` : lignes en `-` supprimées, lignes en `+` ajoutées, lignes sans préfixe inchangées. Si l'affichage s'arrête sur `:`, appuyer sur `q` pour quitter. |

**Lire l'en-tête d'un diff** : `@@ -1,2 +1,42 @@`
- `-1,2` : dans l'ancienne version, le bloc commence ligne 1 et fait 2 lignes.
- `+1,42` : dans la nouvelle version, le bloc commence ligne 1 et fait 42 lignes.
- Ici : 40 lignes ajoutées, aucune supprimée.

## Repère dans l'invite

- `(main)` en fin de ligne : je suis dans un dépôt Git, sur la branche `main`.
- Pas de `(...)` : je ne suis dans aucun dépôt.
- Règle : ne jamais créer ni cloner un dépôt à l'intérieur d'un autre.

