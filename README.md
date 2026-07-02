<style>
.crm-primary, .crm-secondary, .crm-rf, .crm-ofp, .crm-services, .crm-mecenat, .body-bg, .body-cl, .crm-error, .crm-warning, .crm-info, .crm-success, .surface-bg { display: inline-block; height: 20px; width: 20px; border:1px solid black }
.body-bg { background-color: #F5F5F5; }
.body-cl { background-color: #111111; }
.surface-bg { background-color: #FFFFFF; }
.crm-primary { background-color: #1b296a; }
.crm-secondary { background-color: #ed6840;} 
.crm-rf { background-color: #cf2d4f;} 
.crm-ofp { background-color: #7db9da;} 
.crm-services{ background-color: #f6af2e;} 
.crm-mecenat { background-color: #488287;} 
.crm-error { background-color: #d32f2f;} 
.crm-warning { background-color: #e67e22;} 
.crm-info { background-color: #0288d1;} 
.crm-success { background-color: #2e7d32;} 
.logo { width: 240px; margin:auto; }
</style>

![CRM Logo](./docs/logo/crm-logo.png){class="logo"} 


# Charte Graphique TP DWWM/CDA

Sauf mention contraire dans les consignes du TP, vous devez respecter les règles suivantes dans vos interfaces utilisateur.

## Règles de base 

| Règle | Description |
| :--- | :--- |
| **Éco Conception** | Toujours prévoir un mode clair **et** un mode sombre et un mécanisme (bouton ou interrupteur) permettant de basculer entre les 2 modes<br>Les images doivent être optimisées en taille et en poids.<br>Une page web: < 2 Mo (html, css, js, images etc...). |
| **Mobile first**| Concevoir l'interface pour les écrans mobiles en premier, puis l'adapter pour le desktop via les Media Queries CSS. ([Breakpoints](#affichage-adaptatif))   |
| **Accessibilité UI** | Conception inclusive pour les personnes en situation de handicap (contrastes suffisants, polices inclusives).<br>Obligation d'utiliser `rem` pour les tailles de polices (interdiction d'utiliser `px`).<br>Respecter les critères du [Référentiel général d’amélioration de l’accessibilité](https://accessibilite.numerique.gouv.fr/){target="_blank"} |
| **Accessibilité DYS** | L'interface doit proposer un mécanisme (bouton ou interrupteur) permettant de basculer l'ensemble des textes en police OpenDyslexic pour les utilisateurs concernés. |
| **Loi de Fitts** | Tous les éléments cliquables (liens, boutons, icônes) doivent avoir une taille cible minimale de 44px * 44px sur mobile (via du padding si nécessaire) |
| **Defensive Design** | L'interface ne doit JAMAIS casser si un titre, un texte ou une image est plus long que prévu |




## Couleurs principales 

Couleurs autorisées dans vos interfaces utilisateur.

- ✅ Utilisez ces couleurs comme vous le souhaitez (texte, fond, bordure...)
- ❌ Interdiction formelle d'utiliser d'autres couleurs
    - Sauf si explicitement indiqué dans les consignes du TP/projet

| Couleur | Identifiant | HEX | Description / Utilisation | Couleur Texte si utilisée en background |
| --- | --- | --- | --- | --- |
| <span class="body-bg"></span> | body-bg | `#F5F5F5` | Clair (générique) | Sombre
| <span class="body-cl"></span> | body-cl | `#111111` | Sombre (générique) | Clair
| <span class="surface-bg"></span> | surface-bg | `#FFFFFF` | Fond des cartes et éléments d'interface | Sombre
| <span class="crm-primary"></span> | crm-primary | `#1b296a` | Couleur primaire CRM | Clair
| <span class="crm-secondary"></span> | crm-secondary | `#ed6840` | Couleur secondaire CRM | Clair
|  <span class="crm-rf"></span> | crm-rf | `#cf2d4f` | Rouge CRM/RF | Clair
| <span class="crm-ofp"></span> | crm-ofp | `#7db9da` | Bleu CRM/OFP | Sombre
| <span class="crm-services"></span> | crm-services | `#f6af2e` | Jaune CRM/Services | Sombre
| <span class="crm-mecenat"></span> | crm-mecenat | `#488287` | Bleu/Vert CRM/Mecenat | Clair

## Couleurs Actions / Évènements


Pour gérer les actions et les messages de notification, utilisez obligatoirement les couleurs suivantes : 

| Couleur | Identifiant | HEX | Description / Utilisation |
| --- | --- | --- | --- |
| <span class="crm-error"></span> | crm-error | #d32f2f | Message d'erreur |
| <span class="crm-warning"></span> | crm-warning | #e67e22 | Message d'avertissement |
| <span class="crm-info"></span> | crm-info | #0288d1 | Message d'information |
| <span class="crm-success"></span> | crm-success | #2e7d32 | Message de succès/validation |

---

## Polices

Sauf mention contraire, utilisez les polices suivantes.  
Pour le corps de la page `crm-txt-body`, choisissez Verdana **OU** Arial.

| Police | Identifiant | Description / Utilisation |
| :--- | :--- | :--- |
| <span style="font-family: 'Georgia', serif;">Georgia, serif</span> | crm-txt-header | Titres, entêtes |
| <span style="font-family: 'Verdana', sans-serif;">Verdana, sans-serif</span> | crm-txt-body | Textes, corps de la page, formulaires |
| <span style="font-family: 'Arial', sans-serif;">OpenDyslexic</span> | crm-txt-dys | Accessibilité<br>Faciliter la lecture pour les personnes dyslexiques<br>[A télécharger sur le site officiel](https://opendyslexic.org/){target="_blank"} |

## Affichage adaptatif

Sauf mention contraire, utilisez les points de rupture suivants :


| Catégorie | Largeur | Usage | 
| ---| --- | --- |
| 📱 Mobile         | 0 – 767px | - |
| 📲 Tablet         | ≥ 768px   | `@media (min-width: 768px) { }` |
| 💻 Laptop         | ≥ 1024px  | `@media (min-width: 1024px) { }` |
| 🖥️ Desktop large | ≥ 1280px  | `@media (min-width: 1280px) { }` |
| 🖥️ XXL           | ≥ 1600px  | `@media (min-width: 1600px) { }` |
| 🖨️ Imprimantes   | A4 (21cm * 29.7cm)  | `@media print { }` |


## CSS de base

[CSS de base](./docs/css/crm-main.css){target="_blank"} pour le démarrage de vos projets.

```css
:root {
    
}

@media (prefers-color-scheme: dark) {
    :root {
        
    }
}

body {
    
}

h1, h2, h3, h4, h5, h6 {
    
}


@media (min-width: 768px) { }
@media (min-width: 1024px) { }
@media (min-width: 1280px) { }
@media (min-width: 1600px) { }
@media print { }
```

---
