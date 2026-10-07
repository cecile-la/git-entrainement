# git-entrainement

Dépôt d'entraînement Git : branches, merge, conflits, sur des fichiers texte.

## Objectif

Pratiquer le workflow Git d'un projet réel (`main`, `develop`, branches de fonctionnalité) et apprendre à lire l'historique, sur un exemple volontairement simple : un fichier `hello.txt`.

**Notions** : commit, push, branches, `HEAD`, merge *fast-forward*, commit de merge, conflit et résolution, lecture du graphe.


## Lancer

```bash
git clone https://github.com/cecile-la/git-entrainement.git
cd git-entrainement
git log --oneline --graph --all
```

Terminal utilisé : Git Bash (Windows).

## Les 7 étapes

### 1. Commiter et pousser une modification
```bash
git add README.md
git commit -m "docs: …"
git push
```
Pourquoi : enregistrer une modification dans l'historique, puis l'envoyer sur GitHub. Simple `git push` : `main` est déjà reliée à `origin/main` depuis le clone.

### 2. Ajouter un nouveau fichier
```bash
git status
git add hello.txt
git commit -m "feat: ajout de hello.txt pour l'exercice des branches"
git push
```
Pourquoi : voir la différence entre un fichier non suivi (*untracked*) et un fichier modifié (*modified*).

### 3. Créer la branche develop
```bash
git switch -c develop
git push --set-upstream origin develop
```
Pourquoi : `-c` crée la branche et bascule dessus. `--set-upstream` sert au premier push d'une branche que GitHub ne connaît pas encore.

### 4. Créer une branche de fonctionnalité
```bash
git switch -c feature/bonjour
git add hello.txt
git commit -m "feat: ajout de la ligne Bonjour dans hello.txt"
git push --set-upstream origin feature/bonjour
```
Pourquoi : une branche par fonctionnalité, partie de `develop`, comme dans un vrai projet.

### 5. Merger dans develop, puis dans main
```bash
git switch develop
git pull
git merge feature/bonjour
git push
git switch main
git pull
git merge develop
git push
```
Pourquoi : on se place sur la branche qui reçoit, puis on merge. Résultat *Fast-forward* : la branche qui reçoit n'avait aucun commit propre, Git a seulement avancé son étiquette.

### 6. Provoquer un conflit
```bash
git switch develop
git switch -c feature/hola     # ligne 1 → Hola mundo, puis add + commit
git switch develop
git switch -c feature/hallo    # ligne 1 → Hallo Welt, puis add + commit
git switch develop
git merge feature/hola
git merge feature/hallo        # CONFLICT
git status
cat hello.txt
```
Pourquoi : deux branches modifient la même ligne depuis un ancêtre commun. Git ne sait pas choisir et marque le conflit dans le fichier (`<<<<<<<`, `=======`, `>>>>>>>`).

### 7. Résoudre le conflit
```bash
# résolution à la main dans hello.txt : on garde les deux lignes, on retire les marqueurs
git add hello.txt
git commit -m "Merge branch 'feature/hallo' into develop, conflit résolu sur hello.txt"