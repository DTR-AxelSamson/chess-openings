---
name: exo
description: Transforme l'étape d'implémentation en cours en exercice de code à trous qu'Axel complète lui-même, au lieu d'écrire le code à sa place. À utiliser quand Axel tape /exo, dit « fais-m'en un exercice », « laisse-moi l'écrire », ou quand il demande un indice / annonce qu'il a fini un exercice précédent. Couvre la génération de l'exercice, les indices progressifs et la relecture de sa réponse.
---

# /exo — fabriquer un exercice à trous

Objectif : Axel écrit le code qui compte. Je fournis tout ce qui l'entoure, et rien de plus.

Sujet = l'argument passé à `/exo` s'il y en a un, sinon l'étape d'implémentation en cours.

## Avant de générer

Vérifier trois points, et poser la question si l'un manque :

1. **La notion a déjà été expliquée.** Un trou sur un `useState` jamais vu n'est pas un
   exercice, c'est une devinette. Si la notion est neuve : l'expliquer d'abord, l'exercice
   ensuite.
2. **L'exercice porte sur une seule notion.** Si l'étape en demande deux (par ex. un hook
   *et* une mise à jour immuable d'arbre), la découper en deux exercices.
3. **Taille visée : 15 à 30 minutes.** Au-delà, découper.

## Où l'exercice est écrit

**Mode par défaut — dans le vrai fichier du projet.** Créer ou modifier le fichier source
réel (`src/...`) avec les trous dedans. Le code qu'Axel complète *est* l'application :
rien n'est jeté, et il vérifie son travail en rechargeant le navigateur.

**Mode bac à sable — `exercises/NN-sujet.ts`.** Réservé à l'entraînement sur une notion
pure pas encore rattachée à une fonctionnalité (destructuration, promesses, `reduce`).
Fichier isolé, exécutable en une commande — le runner sera mis en place à la première
utilisation de ce mode.

Ne jamais livrer l'exercice sous forme de bloc de code dans le chat : Axel travaille dans
son éditeur, pas dans un terminal.

## Ce qu'on donne, ce qu'on retire

**Donné**, parce que le taper n'apprend rien : imports, types et interfaces, coquille du
composant, classes Tailwind, câblage des props, et tout ce qui a déjà fait l'objet d'un
exercice précédent.

**Retiré**, parce que c'est là qu'est la réflexion : le corps de la fonction, la logique de
mise à jour de l'état, l'appel de hook et son tableau de dépendances, le corps du
gestionnaire d'événement, l'algorithme de parcours ou d'insertion dans l'arbre.

**Granularité** : un trou substantiel vaut mieux que dix minuscules. Dix trous d'un token
chacun font un exercice de dactylographie. Viser 1 à 3 trous.

## Forme d'un trou

Un numéro, un contrat en une phrase (le *quoi*, jamais le *comment*), les types
entrée/sortie, et les contraintes non négociables :

```ts
// TODO 1 — Insérer `move` comme enfant du nœud d'id `parentId`.
//   Si un enfant portant déjà ce SAN existe, renvoyer l'arbre inchangé.
//   (tree: MoveNode[], parentId: string, move: string) => MoveNode[]
//   Contrainte : ne pas muter `tree`.
```

Pas de squelette de solution en commentaire, pas de noms de variables intermédiaires
suggérés — ils donnent la réponse.

## Ce qui accompagne l'exercice (dans le chat, brièvement)

1. **Notions requises** — les idiomes JS/React nécessaires, avec le lien de doc
   (MDN, react.dev). Si l'un n'a jamais servi, l'expliquer en trois ou quatre lignes avant.
2. **Critère de réussite observable** — comment Axel sait *tout seul* que c'est bon.
   Toujours concret : « en jouant 1.e4 puis 1...e5, deux nœuds apparaissent dans la colonne
   de droite », ou « `npx tsc --noEmit` passe ». Jamais « ça devrait marcher ».
3. **Un piège classique**, s'il y en a un, formulé en avertissement et non en réponse
   (« attention : `push` mute le tableau »).

Aucun indice dans le fichier. Les indices se demandent.

## Quand Axel demande un indice

Trois niveaux, **un seul à la fois**, dans l'ordre :

1. Reformuler le problème autrement, ou poser la question qui débloque.
2. Nommer l'outil (« regarde `Array.prototype.map` », « il te faut la forme fonctionnelle
   de `setState` »).
3. Donner *une* ligne de la solution — pas la solution.

Solution complète : seulement s'il la demande explicitement après avoir tenté, ou après
deux essais infructueux. Toujours accompagnée du *pourquoi de cette forme-là*.

## Quand Axel dit avoir fini

Lire son code, répondre dans cet ordre :

1. **Ce qui est juste**, en une ligne — en particulier s'il a trouvé une forme différente
   de celle attendue mais correcte. Ne pas réécrire du code qui marche pour le mettre à
   mon goût.
2. **Ce qui casse** : le symptôme et la ligne. Le laisser corriger (cf. règle 5 du
   CLAUDE.md).
3. **Ce qui est idiomatique, ou ne l'est pas.** C'est le vrai contenu de l'apprentissage
   ici : Axel sait programmer, ce qu'il découvre c'est la manière dont JS et React veulent
   qu'on écrive les choses. Une boucle `for` correcte là où un `map` est attendu mérite
   d'être signalée — en expliquant pourquoi, sans corriger à sa place.

Ne pas noter. Ne pas féliciter mécaniquement.
