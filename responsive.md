# CSS et Affichage adaptatif

Le **responsive design** consiste à adapter automatiquement un site web à la taille de l’écran.

Par exemple pour un même site :

- 📱 Sur mobile → 1 colonne, gros boutons
- 📲 Sur tablette → 2 colonnes
- 💻 Sur ordinateur → plusieurs colonnes

Le contenu reste le même, **mais l’affichage change**

## Objectif

- Lire facilement sur tous les écrans  
- Naviguer sans zoom  
- Améliorer l’expérience utilisateur  

## Comment ça fonctionne ?

On utilise :

- ✅ **CSS (media queries)** → adapter selon la taille
- ✅ **Flexbox / Grid** → organiser les éléments
- ✅ **Unités fluides (%, rem)** → tailles adaptatives

## Important à comprendre

Le responsive design :

* ❌ Ce n’est pas créer plusieurs sites
* ✅ C’est **un seul site adaptable**

## À retenir

```markdown
> Un site responsive s’adapte à l’écran de l’utilisateur automatiquement.
```

## Bonnes pratiques

* Mobile-first (commencer par le mobile)
* Tester sur plusieurs tailles d’écran
* Adapter quand le design “casse”



## Les breakpoints CSS

Les breakpoints CSS sont des points de rupture utilisés en responsive design pour adapter l’affichage d’un site web en fonction de la taille de l’écran (ordinateur, tablette, mobile). Concrètement, ce sont des valeurs de largeur (en pixels, rem, etc.) à partir desquelles on change le style avec des media queries. Par exemple, on peut afficher une navigation horizontale sur grand écran et la transformer en menu burger sur mobile. Les breakpoints permettent donc de créer des interfaces flexibles, lisibles et adaptées à tous les supports, en appliquant des règles CSS différentes selon le contexte d’affichage.




## 1. Breakpoints les plus utilisés

En 2026, il n’existe **plus de standard officiel universel**  mais on retrouve des **valeurs pragmatiques basées sur les périphériques réels dans les frameworks tels que Tailwind / Bootstrap / Material**.

```css
/* Mobile first */
@media (min-width: 480px) { /* anciens mobiles */ }
@media (min-width: 640px) { /* petits tablets / grands mobiles */ }
@media (min-width: 768px) { /* tablet */ }
@media (min-width: 1024px) { /* laptop */ }
@media (min-width: 1280px) { /* desktop */ }
@media (min-width: 1600px) { /* large screens */ }
```

### Variante simplifiée utilisée en formation :

```css
@media (min-width: 768px) { }
@media (min-width: 1024px) { }
@media (min-width: 1280px) { }
@media (min-width: 1600px) { }
```

| Catégorie | Largeur | Usage | 
| ---| --- | --- |
| 📱 Mobile         | 0 – 767px | défaut (mobile) |
| 📲 Tablet         | ≥ 768px   | layout à 2 colonnes |
| 💻 Laptop         | ≥ 1024px  | layout desktop |
| 🖥️ Desktop large | ≥ 1280px  | spacing + max-width |
| 🖥️ XXL           | ≥ 1600px  | confort visuel |
| 🖨️ Imprimantes   | A4 (21cm * 29.7cm)  | Pour les impressions |

✔ Ces valeurs ciblent des **zones de confort de lecture**


## 2. Ce que disent les bonnes pratiques 

###  Mobile-first obligatoire

❌ Ancienne/Mauvaise pratique : 
```css
/* base = desktop */
.card {
  width: 50%;
}

/* adaptation sur les écrans plus petits */
@media (max-width: 1024px) {
  .card {
    width: 100%;
  }
}
```

✅ Préférez toujours le responsive design **mobile-first**:
- Plus simple à coder
- Optimisé pour les terminaux mobiles moins puissants que les PC desktop


```css
/* base = mobile */
.card {
  width: 100%;
}

/* adaptation sur les écrans plus larges */
@media (min-width: 1024px) {
  .card {
    width: 50%;
  }
}
```

### Utiliser `rem` au lieu de `px`

```css
body {
    font-size: 1rem; /* Base native du navigateur (généralement 16px) */
}

@media (min-width: 48rem) { /* 48rem * 16px = 768px */ }

```
✔ **Respect de l'accessibilité :** Si l'utilisateur zoome ou modifie la taille du texte dans les paramètres de son navigateur, les unités `rem` s'adaptent automatiquement, contrairement aux `px`.
✔ **Meilleure cohérence responsive :** L'ensemble de l'interface reste proportionnel.


### Focus Culture Web : `L'astuce des 62.5%`

En parcourant des tutoriels ou du code, vous croiserez souvent cette technique :

```css
html { 
    font-size: 62.5%; /* Base à 10px au lieu de 16px (16 * 0.625 = 10) */
} 

body { 
    font-size: 1.6rem; /* 1.6 * 10px = 16px. Retour à la taille normale */
}

h1 {
    font-size: 2.4rem; /* Équivaut à 24px. Calcul mental simplifié! */
}
```

#### Pourquoi l'utilisait-on ?

Dans la grande majorité des navigateurs web, la taille de texte par défaut est `16px`.
1rem est donc, par défautégal à 16px. Le ratio `rem` / `px` est **1.6/10**.

L'astuce des 62.5% ramène ce ratio `rem` / `px` à **1/10**. Cela permettait aux développeurs de calculer de tête instantanément ($1.4\text{rem} = 14\text{px}$, $3\text{rem} = 30\text{px}$).

#### Pourquoi est-ce déconseillé aujourd'hui ?

1. **Risque pour l'accessibilité :** Cette méthode peut écraser ou fausser les paramètres des outils d'aide à la lecture (extensions, liseuses pour malvoyants) qui forcent une taille de police minimale.
2. **Incompatibilité avec le marché :** Les frameworks modernes (comme Tailwind CSS) et les bibliothèques de composants se basent tous sur le standard natif ($1\text{rem} = 16\text{px}$). Utiliser les 62.5% rendrait ces outils inutilisables sur votre projet.

#### Règle : Conserver la base native du navigateur (`1rem = 16px`)

Pour vos calculs, voici quelques repères de base : 

| rem      | px   | |
|----------|------| --- |
| 0.5rem   | 8px  | Taille de texte minimum recommandée |
| 0.625rem | 10px |  |
| 0.75rem  | 12px |  |
| 1rem     | 16px | Taille de texte par défaut dans les navigateurs web |
| 1.25rem  | 20px |  |
| 1.5rem   | 24px |  |
| 1.75rem  | 28px |  |
| 2rem     | 32px | Taille de texte maximum recommandée  |



## 3. Les tendances futures

Les media queries “classiques” vont perdre en importance.

### Les container queries (déjà en production)

Le futur réel du responsive

```css
.card-container {
  container-type: inline-size;
}

@container (min-width: 400px) {
  .card {
    display: flex;
  }
}
```

✅ Avantages :

* responsive par composant
* indépendant du viewport
* parfait pour composants réutilisables

### Design fluide (moins de breakpoints)

👉 On remplace les paliers par des valeurs dynamiques :

```css
h1 {
  font-size: clamp(1.5rem, 2vw, 3rem);
}
```

✅ Résultat :

* adaptation continue
* moins de media queries


### Layouts adaptatifs modernes

### Grid auto-adaptatif :

```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}
```

Plus besoin de breakpoints dans beaucoup de cas


### Media queries avancées

Exemples modernes :

```css
@media (hover: hover) { }
@media (pointer: coarse) { }
@media (prefers-reduced-motion: reduce) { }
@media (prefers-color-scheme: dark) { }
```

Le responsive ne concerne plus seulement la taille  mais aussi **les capacités et préférences utilisateur**.


## Recommandation DWWM / CDA

### À maitriser en priorité

1. Mobile-first
2. Breakpoints simples :
   * 768 / 1024 / 1280
3. Flexbox + Grid auto-adaptatif
4. `clamp()` pour typographie
5. Les container queries



## À dé-prioriser / éviter

❌ Ciblage iPhone / Android spécifique  
❌ Multiplication de breakpoints  
❌ Design rigide basé sur pixels fixes

***

## 5. Résumé

* Breakpoints courants :
  - **768 / 1024 / 1280 / 1600**
* Approche :
  - **mobile-first + content-driven**
* Évolution :
  - **moins de media queries, plus de fluidité**

Dans le futur :

✅ Container queries  
✅ Layouts auto-adaptatifs  
✅ Typographie fluide  
✅ Responsive basé sur les composants


> “On ne design plus pour des écrans, mais pour des contenus.”

