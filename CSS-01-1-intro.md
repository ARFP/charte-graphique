# Introduction au CSS : Donner du style à vos pages web

**Objectif :** Comprendre comment fonctionne le CSS pour modifier l'apparence d'un site web.


## 1. CSS: Kesako ?

Le mot **CSS** signifie ***C**ascading **S**tyle **S**heets* (Feuilles de style en cascade).

Pour comprendre le lien entre le HTML et le CSS, on utilise souvent l'image d'une maison :

* **Le HTML** définit la structure (les murs, les portes, les fenêtres).
* **Le CSS** s'occupe de la décoration (la couleur de la peinture, la taille des fenêtres, la disposition des meubles).

## 2. La syntaxe CSS

Pour donner un ordre en CSS, on écrit une **règle de style**.
Une règle de style est toujours composée de 3 éléments indispensables :

```css
sélecteur {
    propriété: valeur;
}
```

| Élément | Rôle | Exemple |
| --- | --- | --- |
| **Le Sélecteur** | **Qui** est modifié ? (La cible dans le HTML) | `h1` (tous les titres principaux) |
| **La Propriété** | **Quoi** est modifié ? (La caractéristique) | `color` (la couleur du texte) |
| **La Valeur** | **Comment** est-ce modifié ? (Le résultat souhaité) | `#1b296a` (bleu) |

Traduction en CSS de l'exemple ci-dessus : 

```css
h1 {
    color: #1b296a;
}

```

Le code précédent signifie : *"Tous les titres `<h1>` doivent être colorés en bleu."*


## 3. Où écrit-on le code CSS ?

La bonne pratique professionnelle est d'écrire le code CSS dans un fichier séparé.

1. Le nom d'un fichier CSS se termine par l'extension `.css` (exemple: `style.css`).
2. Dans un document HTML, vous reliez le CSS en ajoutant une balise `<link>` à l'intérieur de la zone `<head>` :

```html
<head>
    [...]
    <link rel="stylesheet" href="style.css">
</head>
```

Cette ligne sert à **relier** un fichier HTML (le contenu) avec un fichier CSS (la décoration). Elle se place toujours dans la zone `<head>` du fichier HTML.

### Anatomie de la balise `<link>`

| Élément | Nom | Rôle |
| --- | --- | --- |
| **`link`** | Nom de la balise | Indique au navigateur qu'il doit lier un fichier externe à la page. |
| **`rel="stylesheet"`** | Attribut de relation | Explique le type de fichier lié. Ici, c'est une "feuille de style" (du CSS). |
| **`href="style.css"`** | Attribut d'adresse | Indique le chemin et le nom du fichier CSS à charger (ici : `style.css`). |

### Deux règles importantes pour éviter les erreurs :

1. **L'emplacement :** Cette ligne doit être écrite **avant** la fermeture de la balise `</head>`.
2. **Le nom du fichier :** Le nom écrit dans le `href` doit être exactement le même que le nom de votre fichier (attention aux majuscules et à l'extension `.css`).

---

## Exercice Pratique Flash

**Consigne :**

1. Créer un fichier `css-1er-essai.html`
2. Y mettre le code suivant : 

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exercice - Introduction CSS</title>

</head>
<body>
    <h1>Mon premier titre stylisé</h1>
    <p>Ce paragraphe doit changer de couleur grâce à votre code CSS.</p>
    <p>Ce deuxième paragraphe doit lui aussi changer de couleur.</p>
</body>
</html>
```

3. Crée un fichier `style.css`.
4. Lier le fichier CSS à la page HTML en ajoutant la balise `<link>` après la balise `<title>` 
5. Écrire la règle CSS pour que le titre `<h1>` de la page s'affiche avec la taille de texte `3.125rem` (50 pixels).
6. Écrire la règle CSS pour que tous les paragraphes `<p>` de la page s'affichent avec la couleur de texte `#0000CC` (bleu).

--- 

## Ressources

- [Introduction au langage CSS sur MDN](https://developer.mozilla.org/fr/docs/Learn/CSS/First_steps)
- [Tutoriaux HTML/CSS sur MDN](https://developer.mozilla.org/fr/docs/MDN/Tutorials)

## Entrainez-vous

- [Exercice d'introduction aux règles CSS](https://arfp.github.io/tp/web/bases/04-css)
- [Mise en forme d'une page, pas à pas](https://arfp.github.io/tp/web/html-css/00-introduction)