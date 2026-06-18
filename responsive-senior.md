# CSS Responsive avancé

Pendant plus d'une décennie, le responsive s'est résumé à une seule chose : surveiller la largeur de la fenêtre du navigateur (*Viewport*) via les Media Queries. Aujourd'hui, cette approche ne suffit plus. L'ère du "Component-Driven Design" (conception par composants autonomes) a donné naissance à des outils CSS natifs ultra-puissants.


## 1. Les Media Queries Modernes (Nouvelle Syntaxe)

Avant d'attaquer les nouveautés architecturales, la syntaxe des Media Queries classiques a été grandement simplifiée. Fini les confusions entre `min-width` et `max-width`.

### L'ancienne syntaxe (Verbeuse)

```css
/* Écrans entre 768px et 1024px */
@media (min-width: 768px) and (max-width: 1024px) {
    /* Code... */
}
```

### La syntaxe moderne (Opérateurs mathématiques)

Le CSS supporte désormais les opérateurs de comparaison (`<`, `>`, `<=`, `>=`). C'est beaucoup plus proche des langages de programmation classiques et instantané à lire.

```css
/* Écrans supérieurs ou égaux à 768px */
@media (width >= 768px) { ... }

/* Écrans strictement inférieurs à 1024px */
@media (width < 1024px) { ... }

/* Écrans compris entre 768px et 1024px (Syntaxe d'intervalle) */
@media (768px <= width <= 1024px) { ... }

```

## 2. La Typographie Fluide avec `clamp()`

 La fonction **[clamp()](https://developer.mozilla.org/fr/docs/Web/CSS/clamp)** fait partie des fonctions de comparaison mathématique du CSS (avec `min()` et `max()`). Elle permet de définir une valeur qui évolue de manière fluide entre une limite basse et une limite haute.

### Syntaxe

$$clamp(\text{Minimum}, \text{Valeur Idéale / Dynamique}, \text{Maximum})$$

### Le Cas d'usage parfait : Le titre `<h1>` voyageur

Avant, pour qu'un titre soit gros sur desktop et petit sur mobile, il fallait écrire 3 ou 4 Media Queries. Avec `clamp()`, on règle cela en une seule ligne de code sans aucune Media Query.

```css
h1 {
    /* Min: 2rem (32px) | Idéal: 5vw (5% de la largeur écran) | Max: 4rem (64px) */
    font-size: clamp(2rem, 5vw, 4rem);
}

```

* **Sur Mobile (petit écran) :** `5vw` représente une petite valeur. Dès qu'elle descend en dessous de `2rem`, le CSS bloque le titre à `2rem`. Il ne sera jamais minuscule.
* **En mouvement :** Entre les deux, la police grandit de manière totalement fluide au pixel près selon la taille de l'écran.
* **Sur Desktop (grand écran) :** `5vw` devient immense. Dès qu'elle dépasse `4rem`, le CSS bloque le titre à `4rem`. Il ne sera jamais disproportionné.

> [!TIP] 
>
> La fonction `clamp()` ne s'applique pas qu'aux polices ! C'est magique pour les `padding`, les `margin` ou la largeur (`width`) d'un élément pour créer des espacements proportionnels.


## 3. Les Container Queries

C'est le changement le plus attendu par les développeurs depuis la découverte du feu il y a 500000 ans.

* **Le problème historique :** Une Media Query surveille la taille de **l'écran**. Si un composant "Carte produit" est placé dans une barre latérale étroite (300px) ou au centre de la page (800px), l'écran, lui, fait toujours la même taille (ex: 1440px). La carte ne sait pas qu'elle est à l'étroit.
* **La solution :** Les *Container Queries* permettent à un élément d'écouter la taille de **son parent direct**, peu importe la taille de l'écran global.

### Comment ça marche en CSS ?

#### Étape 1 : Déclarer le parent comme "contenant"

On doit dire au CSS quel élément doit être surveillé.

```css
.sidebar, .main-grid__item {
    /* On indique que ce parent sert de contexte de taille (inline-size = largeur) */
    container-type: inline-size;
    container-name: card-container; /* Optionnel : pour cibler un conteneur précis */
}

```

#### Étape 2 : Coder le composant responsive en fonction de son parent

On utilise `@container` au lieu de `@media`.

```css
/* Par défaut : la carte a un affichage vertical (mode mobile/étroit) */
.product-card {
    display: flex;
    flex-direction: column;
}

/* Si le PARENT de la carte fait plus de 500px de large, on passe en horizontal */
@container (width >= 500px) {
    .product-card {
        flex-direction: row;
        gap: 2rem;
    }
}

```

Cette approche permet de créer des **composants 100% autonomes**. On code une carte produit une seule fois. Qu'elle soit injectée dans un layout en 3 colonnes, dans un slider mobile, ou tout en haut en mode "vedette", elle adaptera son design toute seule en fonction de l'espace que le layout lui accorde.


## En résumé : La boîte à outils du développeur frontend

| Outil | Ce qu'il écoute | Meilleur cas d'usage |
| --- | --- | --- |
| **Media Queries `(width >= 768px)`** | La fenêtre du navigateur (*Viewport*) | L'architecture globale de la page (Header, Footer, passage d'une grille de 1 à 4 colonnes). |
| **Fonction `clamp()`** | Une unité dynamique (ex: `vw`, `%`) | La typographie fluide et les espacements élastiques sans générer de lignes de code superflues. |
| **Container Queries `@container`** | Le parent direct du composant | Le design interne des composants réutilisables (cartes, formulaires, menus, widgets). |
