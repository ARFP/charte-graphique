Il est fortement conseillé d'en faire **un cours à part**, placé immédiatement après l'introduction et juste avant le modèle de boîte.

**Pourquoi ?** Les sélecteurs et la préséance (la spécificité) forment un gros morceau logique. L'intégrer dans l'introduction créerait une surcharge cognitive et briserait l'effet "Flash" (simple et rapide) de votre premier module. En revanche, le détacher permet de poser des règles claires pour la suite, évitant aux apprenants de se demander plus tard pourquoi leur code CSS "ne marche pas" à cause d'un conflit de priorités.

Voici le support dédié conçu selon la méthode **FALC**.

---

# M1.2 : Les Sélecteurs CSS et la Priorité

**Objectif :** Apprendre à cibler précisément un élément HTML et comprendre qui gagne en cas de conflit.

---

## 1. Les 3 Sélecteurs de Base

Pour appliquer un style, vous devez choisir la bonne cible. Il existe 3 manières principales de sélectionner un élément :

| Type de sélecteur | Syntaxe en CSS | Cible dans le HTML | Usage recommandé |
| --- | --- | --- | --- |
| **De Balise** | `h1 { }` | `<h1 >...</h1>` | Appliquer un style général à toutes les balises du même nom. |
| **De Classe** | `.mon-bouton { }` <br><br>*(avec un point)* | `<a class="mon-bouton">` | **Le plus utilisé.** Pour appliquer un style à plusieurs éléments précis. |
| **D'Identifiant** | `#mon-titre { }` <br><br>*(avec un hashtag)* | `<h1 id="mon-titre">` | À utiliser de manière exceptionnelle (1 seule fois par page pour un élément unique). |

---

## 2. La Préséance : Qui gagne en cas de conflit ?

Quand plusieurs règles CSS visent le même élément HTML, le navigateur utilise un système de points appelé **la spécificité**. Le sélecteur qui a le plus de points gagne et applique son style.

### Le barème des points (du plus fort au plus faible) :

1. 🥇 **L'Identifiant (`#id`)** = **100 points** (Très fort).
2. 🥈 **La Classe (`.classe`)** = **10 points** (Moyen).
3. 🥉 **La Balise** = **1 point** (Faible).

### Exemple de conflit :

Regardez ce code HTML :

```html
<p class="texte-charte" id="alerte">Quel est mon style ?</p>

```

Et ce code CSS :

```css
p { color: blue; }            /* 1 point (balise) */
.texte-charte { color: green; } /* 10 points (classe) */
#alerte { color: red; }        /* 100 points (identifiant) */

```

* **Résultat :** Le texte s'affichera en **rouge**, car l'identifiant (`#alerte`) est beaucoup plus fort (100 points) que la classe et la balise.

> [!IMPORTANT]
> **Règle d'égalité :** Si deux sélecteurs ont exactement le même nombre de points, c'est **le dernier écrit** tout en bas du fichier CSS qui gagne.

---

## 🎯 Exercice Pratique : Le jeu des priorités

**Consigne :** 1. Créez un titre `<h1>` dans votre HTML avec la classe `titre-principal`.
2. Dans votre CSS, écrivez une règle pour la balise `h1` avec la couleur secondaire de la charte (`#ed6840`).
3. En dessous, écrivez une règle pour la classe `.titre-principal` avec la couleur primaire (`#1b296a`).
4. Vérifiez la couleur finale du titre à l'écran et expliquez pourquoi.