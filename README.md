Nom : Lemoine

Groupe : Groupe 5

Année : 1er

IUT Le Havre - Cours GIT

# Compte Rendu - TP3 : Travailler en équipe sur un dépôt GitHub distant

**Nom :** user
**Binôme :** autre

---

## Objectifs du TP

- Travailler en équipe avec GitHub
- Développer un projet Java en collaboration
- Utiliser les branches pour gérer les fonctionnalités
- Comprendre le fonctionnement de `clone`, `pull`, `push`, `commit`, `merge`, `branch`

---

## 1. Mise en place de la collaboration

- Création du dépôt `tp3` sur mon compte GitHub
- Invitation de autre comme collaborateur via **Settings > Manage access**
- Porthos a accepté l'invitation
- Clonage du dépôt localement pour nous deux :
  ```bash
  git clone git@github.com:<utilisateur_de_user>/tp3.git
  ```
- autre a copié les fichiers de `tp2` (sans le `.git`) dans `tp3` et les a poussés sur le dépôt
- J’ai effectué un `git pull` pour récupérer les fichiers à jour

---

## 2. Développement en binôme

### Répartition des tâches

- **user** : Implémentation de la classe `CryptoMarche.java`
- **autre** : Implémentation de la classe `Portefeuille.java`

### Objectif

Faire passer les tests du fichier `TestCryptoMarche.java` sans modifier ce dernier.

### Mon travail (user)

Implémentation des méthodes suivantes dans `CryptoMarche.java` :
- `capitalEnEuros(String proprietaire)`
- `capitalMonneaie(Cryptomonnaie monnaie)`

### Résultat des tests après synchronisation

```bash
java TestCryptoMarche
```

Tous les tests passent :
-  transfertDevise
-  achatDevise
-  capitalEnEuros
-  capitalMonneaie

---

## 3. Gestion des fonctionnalités avec des branches

### Création et test d'une branche

- Création de la branche `test` :
  ```bash
  git checkout -b test
  touch test.txt
  git add test.txt
  git commit -m "fonction de test ajoutée"
  ```
- Retour sur la branche `main` :
  ```bash
  git checkout main
  echo "Nous avons maintenant créé une nouvelle branche de test" >> README.md
  git add README.md
  git commit -m "nouveau commit sur la branche principale"
  ```

### Fusion de la branche `test` dans `main`

- Fusion :
  ```bash
  git merge test
  ```

### Suppression du fichier `test.txt`

```bash
git rm test.txt
git commit -m "test.txt supprimé"
```

---

## 4. Ajout d'une crypto-monnaie personnelle

- Création de la branche `UserCoin` :
  ```bash
  git checkout -b UserCoin
  ```

- Ajout de la classe suivante :

```java
public class AthosCoin extends Cryptomonnaie {
    public UserCoin() {
        super("ATH", 500);
    }
}
```

- Commit, fusion avec `main` et push :
  ```bash
  git add src/UserCoin.java
  git commit -m "Ajout de UserCoin"
  git checkout main
  git merge UserCoin
  git push
  ```

---

## Conclusion

Ce TP m’a permis de :
- Travailler efficacement en binôme avec GitHub
- Utiliser les branches pour isoler des fonctionnalités
- Comprendre et appliquer les opérations de `merge`, `pull`, `push`
- Ajouter une nouvelle crypto-monnaie dans un projet existant

Le projet est fonctionnel, synchronisé, et tous les tests sont validés 
