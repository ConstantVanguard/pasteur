# Guide de push GitHub — Refonte reverend.be 2026

> **Pour le Pasteur, le matin du 23 mai 2026.**
> Ce guide vous permet de pousser le site complet refondu (direction C : navy + or sobre + ivoire) sur GitHub en environ **20 minutes**.

---

## 🎯 Ce qui a été fait pendant la nuit

J'ai refondu **intégralement** votre site reverend.be en respectant trois exigences :

1. **Direction visuelle C** (votre choix) — navy + or sobre + ivoire, sans le « Sa Révérence ».
2. **Toute la technologie de votre site actuel conservée** — datepicker, vérification d'agenda Google Calendar via le proxy CORS, intégration PayPal NCP (les 5 endpoints distincts), menu hamburger mobile, formulaire Formspree.
3. **Identité baptiste assumée partout** — j'ai retiré « tradition réformée » et « Ministère du Christ-Roi » de toutes les pages, remplacés par « tradition baptiste évangélique » et « Communauté Baptiste de Belgique ». Le titre « Sa Révérence » a été retiré au profit de « Pasteur Constant » seul.

**Pages refondues (11 au total) :**

| Fichier | Rôle |
|---|---|
| `index.html` | Page d'accueil dynamique avec services animés au scroll |
| `bapteme.html` | Service Baptême + datepicker + PayPal 150 € |
| `mariage.html` | Service Mariage + datepicker + PayPal 600 € (acompte 50 €) |
| `enterrement.html` | Service Funérailles + datepicker + PayPal 350 € |
| `confirmation.html` | Service Cours de Membres + datepicker + PayPal 450/700 € |
| `guidance.html` | Service Guidance + sélecteur + datepicker + 2 PayPal |
| `presentation.html` | Présentation complète + ouvrages Amazon |
| `contact.html` | Coordonnées + formulaire Formspree |
| `eglise.html` | **Refondue en CBB baptiste** (n'était plus à jour avec votre identité) |
| `confirmation-paiement.html` | Page de remerciement post-paiement PayPal |
| `brochure-mariage.html` | Brochure autonome imprimable |

**Fichiers techniques :**

| Fichier | Rôle |
|---|---|
| `styles.css` | CSS unifié pour les 11 pages (~700 lignes) |
| `scripts.js` | JS commun : animations scroll, lightbox galerie, smooth scroll |
| `agenda-config.js` | **Inchangé** — votre config Google Calendar |
| `bapteme-script.js` | **Inchangé** — votre logique de réservation |
| `mariage-script.js` | **Inchangé** |
| `enterrement-script.js` | **Inchangé** |
| `confirmation-script.js` | **Inchangé** |
| `guidance-script.js` | **Inchangé** |

---

## ✅ Vérifications déjà faites de mon côté

1. **Endpoints PayPal NCP** — les 5 endpoints sont à leur bonne place (6D668VX27S8WJ pour bapteme, NKB3GZY692Y5U pour mariage, etc.)
2. **IDs JavaScript** — datePicker, bookButton, message, paypalButton/Single/Guidance, sessionType, hamburger-button, mobile-menu : tous présents, vos scripts JS vont fonctionner sans modification
3. **Images référencées** — les noms de fichiers d'images sont **exactement les mêmes** que dans votre repo actuel (logo.png, reverend_portrait.jpg, mariage1.jpg, etc.). Vous n'avez aucune image à ajouter.
4. **Liens internes** — la navigation entre pages est cohérente. Footer et menu mobile présents partout.
5. **Liens externes** — baptistesdebelgique.be, associationbaptiste.org, Amazon (2 livres), PayPal : tous corrects.
6. **Formulaire Formspree** — pointe sur votre endpoint `xjkyzbek` (le même que sur votre site actuel).

---

## 📋 Procédure de push, étape par étape

### Avant de commencer

Allez sur https://github.com/ConstantVanguard/pasteur et **gardez l'onglet ouvert**. Identifiez-vous si pas encore fait.

### Étape 1 — Sauvegarde de sécurité (5 min, recommandé)

Avant tout, faites une **sauvegarde de votre branche actuelle** au cas où vous voudriez revenir en arrière.

1. Dans GitHub, allez sur la page d'accueil de votre repo `pasteur`.
2. Cliquez sur le menu déroulant `main` en haut à gauche (au-dessus de la liste des fichiers).
3. Tapez `sauvegarde-avant-refonte-2026-05-23` dans le champ → cliquez « Create branch from main ».
4. Revenez sur la branche `main` (menu déroulant → main).

Si quelque chose tournait mal, vous pourriez restaurer en revenant sur cette branche.

### Étape 2 — Pousser les 11 fichiers HTML, le CSS et le scripts.js (15 min)

Sur la branche `main`, vous allez **remplacer** les fichiers existants par les nouveaux. Pour chacun des 13 fichiers ci-dessous, suivez la même procédure :

**Procédure type** (à répéter pour chaque fichier) :

1. Cliquez sur le fichier dans la liste GitHub (par exemple `index.html`)
2. Cliquez sur l'icône **crayon** en haut à droite du fichier pour éditer
3. **Sélectionnez tout le contenu existant** (`Ctrl+A`) et supprimez-le
4. **Ouvrez le nouveau fichier** depuis le dossier `5_SITE_INTERNET/REFONTE_2026/site_complet/` sur votre ordinateur, sélectionnez tout (`Ctrl+A`), copiez (`Ctrl+C`)
5. Collez dans l'éditeur GitHub (`Ctrl+V`)
6. Descendez en bas → champ « Commit message » → tapez par exemple `Refonte 2026 — index dynamique direction C`
7. Cliquez « Commit changes » (bouton vert)

**Liste des fichiers à remplacer dans cet ordre** :

1. `styles.css`  ⚠️ commencez par celui-ci (sinon les autres pages sembleront cassées entre deux push)
2. `scripts.js`
3. `index.html`
4. `bapteme.html`
5. `mariage.html`
6. `enterrement.html`
7. `confirmation.html`
8. `guidance.html`
9. `presentation.html`
10. `contact.html`
11. `eglise.html`
12. `confirmation-paiement.html`
13. `brochure-mariage.html`

**Fichiers à créer (n'existent pas encore dans votre repo)** :

14. `sitemap.xml` — pour Google et les moteurs de recherche
15. `robots.txt` — instructions pour les crawlers (autorise tout sauf la page confirmation-paiement)
16. `404.html` — page d'erreur stylée en charte C (s'affiche automatiquement sur GitHub Pages si une URL n'existe pas)

Pour les créer : sur la page d'accueil du repo, bouton **« Add file » → « Create new file »** → tapez le nom → collez le contenu → commit.

**Important** : les fichiers JS de service (`agenda-config.js`, `bapteme-script.js`, `mariage-script.js`, `enterrement-script.js`, `confirmation-script.js`, `guidance-script.js`) **ne doivent PAS être modifiés**. Ils sont identiques à ceux qui sont déjà sur votre repo. Vous pouvez les ignorer.

### Étape 3 — Supprimer les anciens CSS de service (optionnel mais propre, 2 min)

Votre repo contient encore les 5 fichiers CSS par service qui ne servent plus (tout est dans le nouveau `styles.css`). Vous pouvez les supprimer :

- `bapteme-styles.css`
- `mariage-styles.css`
- `enterrement-styles.css`
- `confirmation-styles.css`
- `guidance-styles.css`

Pour chacun : ouvrez le fichier → icône **corbeille** (à côté du crayon) → confirmer.

Ce n'est pas urgent. Si vous préférez les garder « au cas où », laissez-les — ils ne seront plus chargés par les nouvelles pages.

### Étape 4 — Vérifier que le site fonctionne (5 min)

Attendez 1-2 minutes après le dernier commit (le temps que GitHub Pages republie le site), puis :

1. Ouvrez https://www.reverend.be dans un onglet **en navigation privée** (pour éviter le cache)
2. Vérifiez l'accueil — l'esthétique navy/or/ivoire doit s'afficher
3. Cliquez sur **Mariage** dans le menu — la page doit s'afficher, scrollez jusqu'à la section « Réserver votre date »
4. **Testez le datepicker** : sélectionnez une date dans 60 jours, un samedi → cliquez « Vérifier la disponibilité » → le bouton PayPal doit apparaître si la date est libre
5. **Testez le menu hamburger** sur mobile (réduisez la fenêtre à 600px de large) : les 3 traits doivent s'afficher, le menu glisse depuis la droite
6. **Testez le formulaire de contact** : remplissez `contact.html` avec votre propre email et envoyez — vous devriez recevoir le test dans `info@reverend.be`

---

## ⚠️ Si quelque chose ne va pas

### Le site ne charge pas du tout

Attendez 5 minutes (parfois GitHub Pages met du temps). Sinon vérifiez sur https://github.com/ConstantVanguard/pasteur/actions s'il y a une erreur de build.

### Les images ne s'affichent pas

Toutes les images référencées doivent déjà être dans votre repo (logo.png, reverend_portrait.jpg, mariage1.jpg, bapteme1.jpg, etc.). Si une seule manque, ouvrez la console du navigateur (`F12` → Console) pour voir laquelle.

Si jamais une image manque vraiment (peu probable), elle apparaîtra avec un encadré gris discret ; ce n'est pas dramatique le temps de la replacer.

### Le datepicker ou PayPal ne fonctionne pas

Vérifiez dans la console du navigateur (`F12`) qu'il n'y a pas d'erreur JS. Les scripts à charger en ordre sont : `scripts.js` → `agenda-config.js` → `[service]-script.js`. Cet ordre est respecté dans tous les HTML que j'ai produits.

### Vous voulez revenir en arrière

Sur GitHub, allez sur l'onglet **Commits** → identifiez le commit avant la refonte → cliquez « Revert » sur chacun des commits récents, dans l'ordre inverse. Ou plus radical : créez une nouvelle branche depuis `sauvegarde-avant-refonte-2026-05-23` (votre sauvegarde de l'étape 1) et faites-en la branche par défaut dans les Settings du repo.

---

## 📞 En cas de problème

Reprenez la conversation avec moi (le Diacre) en m'expliquant ce qui ne va pas. J'ai laissé toute l'analyse dans :

- `5_SITE_INTERNET/REFONTE_2026/ANALYSE_REFONTE.md` — analyse comparative initiale
- `5_SITE_INTERNET/REFONTE_2026/source_actuel/` — copie de votre site actuel pour comparaison
- `5_SITE_INTERNET/REFONTE_2026/site_complet/` — les nouveaux fichiers (ce que vous venez de pousser)

---

## 🎨 Quelques notes sur le design final

**Ce qui a changé dans le ton visuel :**

- **Fond clair dominant** (ivoire `#FAFAF7`) à la place du fond noir. Cela résout immédiatement le « poussiéreux ».
- **Bandeau navy** pour la devise « Unitas Lux Christus » sur la home — un seul moment dramatique, plutôt que partout.
- **Or sobre** (`#B89A56`) en accent seulement, pas en couleur principale. Pas de doré brillant.
- **Cormorant Garamond** en titres serif (élégant, moderne, sans tomber dans le médiéval comme Cinzel).
- **Inter** en corps : neutre, très lisible.
- **Sceau circulaire « C »** dans le header — votre signature personnelle, en or fin double cercle.
- **Top-strip institutionnel** sur toutes les pages : « Communauté Baptiste de Belgique — en communion fraternelle avec l'AEEBLF ». Affirme votre identité baptiste dès le premier coup d'œil.

**Animations dynamiques ajoutées :**

- Apparition au scroll des sections (via IntersectionObserver)
- Hover effects sur les cartes de service (légère élévation + barre or qui apparaît)
- Badge animé « 40+ cérémonies accompagnées » qui flotte doucement sur le portrait du hero
- Lightbox sur les galeries d'images (cliquez une photo → elle s'agrandit)
- Menu hamburger qui glisse depuis la droite avec animation
- Sceau « C » qui tourne légèrement au survol

**SEO préservé / amélioré :**

- Toutes les `<meta description>` ont été réécrites avec des mots-clés baptistes (à la place des mots-clés réformés)
- Tous les `<title>` mentionnent explicitement « baptiste »
- Les `<link rel="canonical">` sont conservés
- La structure sémantique HTML5 est propre (`<header>`, `<main>`, `<section>`, `<footer>`)
- Les ancres internes fonctionnent avec smooth scroll

---

## 💡 Quelques chantiers à poursuivre ensemble

Quand vous serez prêt, on pourra reprendre :

1. **Témoignages réels** — j'ai mis un témoignage en placeholder dans une maquette précédente. Avec votre autorisation et celle des couples/familles, on remplace par 2-3 vrais témoignages.
2. **Optimisation des images** — vos `.jpg` actuelles sont parfois énormes (>9 Mo pour `bapteme1.jpg` et `bapteme2.jpg`). On peut les compresser à 80 % de qualité sans perte visible et diviser leur poids par 5. Bon pour le SEO mobile.
3. **Page « Brochure mariage » → PDF** — la version HTML est imprimable, mais on pourrait aussi générer une vraie version PDF prête à envoyer en pièce jointe.
4. **Ajout d'avis Google Business** dans la home (preuve sociale) — dès que vous aurez collecté quelques avis sur votre fiche GBP.
5. **Refonte du site CBB (`baptistesdebelgique.be`)** dans la même charte — pour cohérence entre les deux sites.

---

_Bonne matinée, Pasteur. Tout est prêt pour le push._

— Le Diacre
