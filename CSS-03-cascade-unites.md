# Héritage et Unités en CSS

**Objectif :** Comprendre comment les styles se transmettent entre les éléments et apprendre à utiliser des tailles fluides pour respecter l'accessibilité.


## 1. Le principe de l’Héritage

En CSS, le mot "Cascade" signifie que certaines règles de style s'appliquent à un élément et **se transmettent automatiquement** à ses enfants, ses petits-enfants, etc...

* **Les propriétés héritées (généralement liées au texte) :** `color`, `font-family`, `font-size`.
* **Les propriétés non héritées (liées à la structure) :** `border`, `padding`, `margin`, `width`.

**Exemple :**

Si vous écrivez ce code CSS :

```css
body {
    color: #0000CC; /* bleu */
    font-family: Verdana, sans-serif;
}

```

* **Résultat :** Tous les paragraphes `<p>`, les titres `<h1> <h2>...` et les listes `<ul>` à l'intérieur du `<body>` vont automatiquement s'afficher en **Verdana** et en **bleu**, sans avoir besoin de leur appliquer la règle individuellement.


## Exception : les éléments de formulaire

Certains éléments HTML refusent d'hériter des règles de style de leurs parents. Les navigateurs appliquent leur propre style interne par défaut (souvent la police système standard). C'est le cas des **boutons** et des **champs de saisie** :

* `<button>`
* `<input>`
* `<textarea>`
* `<select>`

### Le Problème :

Si vous écrivez `body { font-family: Verdana; }`, vos paragraphes seront en Verdana, mais vos boutons resteront avec la police par défaut du navigateur (souvent Arial ou Times New Roman).

### La Solution (`inherit`) :

Pour forcer ces éléments à obéir à l'héritage de vos règles CSS, on utilise la valeur **`inherit`** (qui signifie "hérite de ton parent").

**Exemple :**

```css
button, input, textarea, select {
    font-family: inherit;
    font-size: inherit;
    color: inherit;
}

```

Grâce à ces trois lignes, les éléments des formulaires adopteront automatiquement les polices et les couleurs sans aucun effort.

---


## 2. Les Unités : Absolues vs Relatives

Pour donner une taille à un texte ou à une boîte, vous devez choisir une unité de mesure.

### A. L'unité absolue : Le Pixel (`px`)

Le pixel reste fixe. Il ne s'adapte jamais aux changements.

* ❌ **Interdiction pour le texte :** Si un utilisateur malvoyant augmente la taille du texte dans les paramètres de son navigateur, le texte ne grandit pas avec l'UI, ce qui brise l'accessibilité.

### B. L'unité relative universelle : Le `rem`

Le `rem` signifie *Root EM*. Cette unité est calculée par rapport à la taille de police par défaut du navigateur (la racine `html`).

* Par défaut, dans 99% des navigateurs : **`1rem = 16px`**.
* ✅ **Obligation pour le texte :** Le `rem` respecte le zoom de l'utilisateur. Si l'utilisateur double la taille par défaut de son navigateur, `1rem` devient égal à `32px` automatiquement.

### C. Les unités de structure fluides

Pour les boîtes (largeur, hauteur), on utilise d'autres unités relatives :

* **`%` (Pourcentage) :** Calcule la taille par rapport à la taille du parent direct.
* **`vw` (*Viewport Width*) :** Calcule la taille selon la largeur totale de l'écran ($1\text{vw} = 1\%$ de la largeur).
* **`vh` (*Viewport Height*) :** Calcule la taille selon la hauteur totale de l'écran ($1\text{vh} = 1\%$ de la hauteur).

---

## 3. Les repères de conversion `rem` / `px`

Pour vos calculs, conservez toujours la base native du navigateur (`1rem = 16px`).

| Valeur en `rem` | Équivalent en `px` | Usage recommandé |
| --- | --- | --- |
| **`0.5rem`** | `8px` | Taille de texte minimale absolue. |
| **`1rem`** | `16px` | Taille par défaut du texte de lecture. |
| **`1.25rem`** | `20px` | Sous-titres ou texte mis en avant. |
| **`1.5rem`** | `24px` | Titres intermédiaires. |
| **`2rem`** | `32px` | Grands titres. |

---

## Exercice Pratique : Passage au 100% accessible

**Consigne :** 
1. Dans un fichier HTML, créez une boîte `<div>` qui contient :
    - un titre `<h2>` ""
    - un paragraphe `<p>` contenant un exte d'au moins 200 caractères.
    - un bouton `<button>Cliquez ici</button>`.
3. Dans votre CSS, appliquez la police `Georgia, serif` uniquement sur le parent `<div>`. 
4. Vérifiez que le titre et le paragraphe héritent bien de cette police.
5. Constatez la différence de police entre le texte et le bouton.
6. Donnez une taille de `2rem` au titre `<h2>` et une taille de `1rem` au paragraphe `<p>`.
7. Appliquez le code correctif `font-family: inherit;` sur le bouton et observez le résultat.
8. Changez les paramètres de zoom de votre navigateur (Ctrl + la molette de la souris) pour vérifier que votre texte s'adapte parfaitement.
