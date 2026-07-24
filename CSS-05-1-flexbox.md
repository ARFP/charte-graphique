# Flexbox – L'alignement sur un axe unique

**Objectif :** Apprendre à aligner facilement plusieurs boîtes les unes à côté des autres ou les unes sous les autres.


## 1. Concept de base : Parent et Enfants

Pour utiliser Flexbox, on travaille toujours sur deux niveaux :

1. **Le container (Le Parent)** : La boîte qui va contenir les éléments. On lui donne la règle `display: flex;`.
2. **Les items (Les Enfants)** : Les boîtes situées directement à l'intérieur du parent. Elles obéissent automatiquement aux ordres du parent flexbox.

```css
.parent-container {
    display: flex; /* Active le mode Flexbox */
}
```

## 2. Le choix du sens : `flex-direction`

Flexbox fonctionne sur **un seul axe à la fois**. Vous devez choisir si vous alignez vos éléments en ligne ou en colonne grâce à la propriété `flex-direction` :

| Valeur | Résultat visuel | Comportement des enfants |
| --- | --- | --- |
| **`flex-direction: row;`**<br><br>*(Par défaut)* | **En ligne (Horizontal)** | Les enfants se placent les uns à côté des autres, de la gauche vers la droite. |
| **`flex-direction: row-reverse;`**<br><br>*(Par défaut)* | **En ligne (Horizontal)** | Les enfants se placent les uns à côté des autres, de la droite vers la gauche. |
| **`flex-direction: column;`** | **En colonne (Vertical)** | Les enfants se placent les uns en dessous des autres, du haut vers le bas. |
| **`flex-direction: column-reverse;`** | **En colonne (Vertical)** | Les enfants se placent les uns en dessous des autres, du bas vers le haut. |

---

## 3. L'alignement des éléments

Une fois l'axe choisi, vous pouvez ranger et espacer vos éléments à l'intérieur du parent.

### A. Aligner sur l'axe principal : `justify-content`

Cette propriété gère l'alignement et l'espacement sur l'axe de votre `flex-direction`.

| Valeur | Effet visuel |
| --- | --- |
| **`flex-start`** *(Par défaut)* | Colle tous les éléments au **début** de la ligne. |
| **`center`** | Place tous les éléments au **centre**. |
| **`flex-end`** | Colle tous les éléments à la **fin** de la ligne. |
| **`space-between`** | Crée un **espace égal entre** les éléments (le premier colle à gauche, le dernier colle à droite). |
| **`space-around`** | Crée un **espace égal tout autour** de chaque élément. |

### B. Aligner sur l'axe secondaire : `align-items`

Cette propriété gère l'alignement dans l'autre sens (par exemple, la hauteur de la ligne).

| Valeur | Effet visuel |
| --- | --- |
| **`stretch`** *(Par défaut)* | Étire les enfants pour qu'ils prennent toute la hauteur du parent. |
| **`center`** | Aligne les enfants pile au **milieu** de la hauteur. |
| **`flex-start`** | Aligne les enfants vers le **haut**. |
| **`flex-end`** | Aligne les enfants vers le **bas**. |

---

> [!TIP] Focus Culture Web : Le texte de droite à gauche (RTL)
>
> Certaines langues comme l'arabe, le farsi, l'ourdou ou l'hébreu, s'écrivent de droite à gauche. On appelle cela le mode **RTL** (*Right-to-Left*).
>
>Si votre site doit être traduit dans l'une de ces langues, l'utilisation de Flexbox est magique. Sans changer votre code, le navigateur inverse automatiquement l'ordre d'affichage : le début de la ligne (`flex-start`) passe tout à droite, et la fin de la ligne (`flex-end`) passe tout à gauche. Votre mise en page s'adapte ainsi naturellement à la langue de l'utilisateur.

## Exercice Pratique : La barre de navigation CRM

**Consigne :** Créez une barre de menu (`<nav>`) contenant un logo et 3 liens.

```html
<nav>
    <img src="./docs/logo/crm-logo.png" alt="logo">
    <ul>
        <li><a href="#">Lien 1</a></li>
        <li><a href="#">Lien 2</a></li>
        <li><a href="#">Lien 3</a></li>
    </ul>
</nav>
```

1. Donnez la règle `display: flex;` au parent `<nav>`.
2. Utilisez `justify-content` pour placer le logo tout à gauche et les liens tout à droite.
3. Utilisez `align-items` pour centrer verticalement le texte et le logo au milieu de la barre.
