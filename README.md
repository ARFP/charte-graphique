<style>
.crm-primary, .crm-secondary, .crm-rf, .crm-ofp, .crm-services, .crm-mecenat, .body-bg, .body-cl, .crm-error, .crm-warning, .crm-info, .crm-success{ display: inline-block; height: 20px; width: 20px; border:1px solid black }
.body-bg { background-color: #F5F5F5; }
.body-cl { background-color: #111111; }
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


# Charte Graphique

## Règles de base 

| Règle | Description |
| :--- | :--- |
| Éco Conception | Toujours prévoir un mode clair **et** un mode sombre |
| Mobile first | Concevoir l'interface pour les écrans mobiles en premier, puis l'adapter pour le desktop via les Media Queries CSS.  |
| Accessibilité | Conception inclusive pour les personnes en situation de handicap.<br>Respecter les critères du [Référentiel général d’amélioration de l’accessibilité](https://accessibilite.numerique.gouv.fr/){target="_blank"} |




## Couleurs principales 

Couleurs autorisées dans vos interfaces utilisateur.

- ✅ Utilisez ces couleurs comme vous le souhaitez (texte, fond, bordure...)
- ❌ Interdiction formelle d'utiliser d'autres couleurs
    - Sauf si explicitement indiqué dans les consignes du TP/projet

| Couleur | Identifiant | HEX | Description / Utilisation |
| --- | --- | --- | --- |
| <span class="body-bg"></span> | body-bg | #F5F5F5 | Clair (générique) |
| <span class="body-cl"></span> | body-cl | #111111 | Sombre (générique) |
| &nbsp; ||||
| <span class="crm-primary"></span> | crm-primary | #1b296a | Couleur primaire CRM | 
| <span class="crm-secondary"></span> | crm-secondary | #ed6840 | Couleur secondaire CRM | 
|  <span class="crm-rf"></span> | crm-rf | #cf2d4f | Rouge CRM/RF |
| <span class="crm-ofp"></span> | crm-ofp | #7db9da | Bleu CRM/OFP |
| <span class="crm-services"></span> | crm-services | #f6af2e | Jaune CRM/Services | 
| <span class="crm-mecenat"></span> | crm-mecenat | #488287 | Bleu/Vert CRM/Mecenat |

## Couleurs Actions / Évènements


Pour gérer les actions et les messages de notification, utilisez obligatoirement les couleurs suivantes : 

| Couleur | Identifiant | HEX | Description / Utilisation |
| --- | --- | --- | --- |
| <span class="crm-error"></span> | crm-error | #d32f2f | Message d'erreur<br>Bouton *Annuler*, *Supprimer*...<br>Donnée invalide, champ obligatoire vide. |
| <span class="crm-warning"></span> | crm-warning | #e67e22 | Message d'avertissement<br>Bouton *Modifier*<br>Action irréversible, mot de passe faible... |
| <span class="crm-info"></span> | crm-info | #0288d1 | Message d'information<br>Bouton *Afficher*, *Plus d'info*<br>Bulle d'aide, date de mise à jour. |
| <span class="crm-success"></span> | crm-success | #2e7d32 | Message de succès<br>Bouton *Ajouter*, *Valider*<br>Formulaire envoyé, paiement validé... |

---

## Polices

Sauf mention contraire, utilisez les polices suivantes.

| Police | Identifiant | Description / Utilisation |
| :--- | :--- | :--- |
| <span style="font-family: 'Georgia', serif;">Georgia, serif</span> | crm-txt-header | Titres, entêtes |
| <span style="font-family: 'Verdana', sans-serif;">Verdana, sans-serif</span> | crm-txt-body | Textes, corps de la page, formulaires|
| <span style="font-family: 'Arial', sans-serif;">Arial, sans-serif</span> | crm-txt-action | Boutons, notifications |
| <span style="font-family: 'Arial', sans-serif;">OpenDyslexic</span> | crm-txt-dys | Accessibilité<br>Faciliter la lecture pour les personnes dyslexiques<br>[A télécharger sur le site officiel](https://opendyslexic.org/){target="_blank"} |


## CSS de base

[CSS de base](./docs/css/crm-main.css){target="_blank"} pour le démarrage de vos projets.

```css
:root {
    /* MODE CLAIR (Par défaut) */
    --body-bg: #F5F5F5;
    --body-cl: #111111;
    --surface-bg: #FFFFFF;   /* Fond des cartes et éléments d'interface */

    /* Couleurs du thème CRM */
    --crm-primary: #1b296a;
    --crm-secondary: #ed6840;
    --crm-rf: #cf2d4f;
    --crm-ofp: #7db9da;
    --crm-services: #f6af2e;
    --crm-mecenat: #488287;

    /* Couleurs d'état / Événements */
    --crm-error: #d32f2f;
    --crm-warning: #e67e22;
    --crm-info: #0288d1;
    --crm-success: #2e7d32;

    /* Polices */
    --crm-txt-header: Georgia, serif;
    --crm-txt-body: Verdana, sans-serif;
    --crm-txt-action: Arial, sans-serif;
}

@media (prefers-color-scheme: dark) {
    :root {
        /* MODE SOMBRE (Automatique) */
        /* Structure */
        --body-bg: #121212;      /* Fond sombre (recommandé Material Design) */
        --body-cl: #E0E0E0;      /* Texte gris très clair (évite le blanc pur agressif) */
        --surface-bg: #1E1E1E;   /* Fond des cartes plus clair que le body pour le relief */

        /* Thème CRM adapté pour le mode sombre (Teintes adoucies pour l'accessibilité) */
        --crm-primary: #3f51b5;     /* Bleu légèrement plus clair pour rester visible */
        --crm-secondary: #ff7a50;   /* Orange adouci */
        
        /* Couleurs du thème CRM restent identiques mais 
           ne doivent être utilisées que sur la surface-bg ou en bordure */

        /* Événements et actions (Teintes pastel/lumineuses pour fond sombre) */
        --crm-error: #ef5350;       /* Rouge plus clair */
        --crm-warning: #ffb74d;     /* Orange/Jaune plus clair */
        --crm-info: #29b6f6;        /* Bleu plus clair */
        --crm-success: #66bb6a;     /* Vert plus clair */
    }
}

/* Exemple de base */
body {
    background-color: var(--body-bg);
    color: var(--body-cl);
    font-family: var(--crm-txt-body);
}

h1, h2, h3 {
    font-family: var(--crm-txt-header);
}

button {
    font-family: var(--crm-txt-action);
}
```

---
