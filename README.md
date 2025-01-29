# **L'accessibilité numérique**

## **Sommaire**
1. [Présentation](#présentation)
  - [Qu’est-ce que l’accessibilité numérique ?](#qu’est-ce-que-l’accessibilité-numérique-)
  - [Types de handicap impactant le numérique](#types-de-handicap-impactant-le-numérique-)
  - [Exemples de besoins spécifiques](#exemples-de-besoins-spécifiques-)
  - [Les niveaux d’accessibilité du WCAG](#les-niveaux-d’accessibilité-du-wcag-)
  - [Pourquoi c’est important ?](#pourquoi-c’est-important-)
2. [Les principales règles d’accessibilité](#les-principales-règles-d’accessibilité)
  - [Images](#1-images-principe--perceptible)
  - [Couleurs](#2-couleurs-principe--perceptible)
  - [Navigation au clavier](#3-navigation-au-clavier-principe--utilisable)
  - [Cadres (iframes)](#4-cadres-iframes-principe--robuste)
  - [Formulaires](#5-formulaires-principe--Compréhensible)
  - [Éléments interactifs](#6-éléments-interactifs-principe--utilisable)
  - [Structure et titres](#7-structure-et-titres-principe--Compréhensible)
  - [Multimédia](#8-multimédia-principe--perceptible)
  - [Temps et animations](#9-temps-et-animations-principe--utilisable)
  - [Tableaux](#10-tableaux-principe--perceptible)
  - [Liens](#11-liens-principe--perceptible)
  - [Scripts](#12-scripts-principe--compréhensible)
  - [Éléments obligatoires & structures](#13-éléments-obligatoires--structures-principe--compréhensible--perceptible)
  - [Présentation de l’information](#14-présentation-de-l’information-principe--perceptible)
  - [Formulaires](#15-formulaires-principe--perceptible--compréhensible)
  - [Navigation](#16-navigation-principe--perceptible)

## **Présentation**
### **Qu’est-ce que l’accessibilité numérique ?**  
L’accessibilité numérique vise à rendre les contenus utilisables par tous.  
 les organismes et normes : **WAI (Web Accessibility Initiative) & universalité du W3C**

---

### **Types de handicap impactant le numérique :**  
- **Déficiences motrices**
- **Déficiences visuelles**
- **Déficiences auditives**
- **Déficiences mentales ou intellectuelles**
- **Déficiences cognitives**
- **Déficiences psychiques**
- **Maladies invalidantes**

---

### **Exemples de besoins spécifiques :**  
- **Navigation au clavier** : Utilisation de la touche Tab, Entrée, Espace ou flèches.  
- **Lecteurs d’écran** : Transcription vocale des contenus.  
- **Personnalisation** : Adaptation des couleurs, polices, tailles.  
- **Commandes vocales** : Interaction par la voix.  

---

### **Les niveaux d’accessibilité du WCAG :**  
1. **Niveau A (minimum)** : Lève les principales barrières d’accès.  
   *Exemple : Texte alternatif pour les images.*  
2. **Niveau AA (recommandé)** : Évite des discriminations pour une meilleure accessibilité.  
   *Exemple : Contrastes de couleur suffisants.*  
3. **Niveau AAA (optimal)** : Confort maximal, mais non obligatoire.  
   *Exemple : Sous-titres détaillés pour toutes les vidéos.*  

---

### **Pourquoi c’est important ?**  
- **Chiffres clés** :  
  - 9 millions de personnes en situation de handicap en France.  
  - 1 site sur 7 seulement est accessible.  
  - 80% des handicaps sont invisibles.  
- **Contexte légal** :  
  - En France, la loi du 11 février 2005 impose l’accessibilité des sites publics et entreprises.  

---

L’accessibilité numérique est une démarche inclusive qui répond à des enjeux d’égalité et de respect des droits fondamentaux. Elle concerne tous les contenus : sites, applications, logiciels et supports numériques.

---

## Les principales règles d’accessibilité

Voici un résumé des critères d'accessibilité numérique et des recommandations techniques à appliquer au niveau du code :

---

### 1. **Images** (Principe : perceptible)
- **Image porteuse d'information ou lien** : Ajouter un attribut `alt` décrivant le contenu ou un attribut aria-label.  
  *Exemple : `<img alt="Description de l'image" src="image.jpg">`*  
  *Exemple : `d'information<svg role="img" aria-label="[texte alternatif]">`*
 - **Image décorative** : Utiliser un `alt=""` vide ou `aria-hidden="true"`.  
  *Exemple : `<img alt="" src="image.jpg">`*
- **Image complexe (graphique, infographie)** : Ajouter une description détaillée à proximité. 
  *Exemple : 
    ``` html
    <figure role="figure" aria-label="[Légende de l'image]">
      <img src="…" alt="Peinture" />
      <figcaption>
        [Légende de l'image]
      </figcaption>
    </figure>
    ```
  *Exemple : Texte descriptif sous le graphique.*
- **Icône** : Inclure une description dans un `span` pour lecteurs d’écran.  
  *Exemple : `<i aria-hidden="true"><span class="sr-only">Description</span></i>`*

---

### 2. **Couleurs** (Principe : perceptible)
- **Contrastes suffisants** : Respecter les ratios WCAG (4.5:1 pour les textes normaux, 3:1 pour les grands textes).  
  *Outil : [Contrast Finder](https://app.contrast-finder.org/)*  
- **Information par couleur** : Toujours associer la couleur à une forme ou un texte.  
  *Exemple : `<span style="color:red;" aria-hidden="true">Erreur</span>` accompagné d'un symbole.*

---

### 3. **Navigation au clavier** (Principe : utilisable)
- **Focus visible** : Toujours rendre visible l’élément ayant le focus.  
  - Ne pas utiliser `outline: none`.  
  *Exemple : `:focus { outline: 2px solid blue; }`*  
- **Ordre du focus** : Organiser les éléments selon une logique naturelle avec `tabindex`.  
  *Exemple : `<div tabindex="1">` pour prioriser.*  
- **Alternatives pour gestes complexes** : Prévoir des gestes simples ou des alternatives claviers.  
- **Zones interactives** : Taille minimale de 24x24px et espacées d’au moins 24px.  

---

### 4. **Cadres (iframes)** (Principe : robuste)
- **Titre pertinent** : Ajouter un attribut `title` pour décrire le contenu.  
  *Exemple : `<iframe title="Vidéo explicative" src="video.html"></iframe>`*

---

### 5. **Formulaires** (Principe : Compréhensible)
- **Label explicite** : Associer chaque champ à un label via `for` et `id`.  
  *Exemple : `<label for="email">Email</label><input id="email" type="email">`*  
- **Erreur accessible** : Utiliser des messages clairs et associés au champ avec `aria-describedby`.  
  *Exemple : `<span id="error-email">Email invalide</span><input aria-describedby="error-email">`*

---

### 6. **Éléments interactifs** (Principe : utilisable)
- **Boutons et liens** : Toujours utiliser `<button>` ou `<a>` avec des actions accessibles.  
  *Exemple : `<button>Envoyer</button>`*  
- **Roles ARIA** : Ajouter des rôles si nécessaire pour définir la fonction.  
  *Exemple : `<div role="button" tabindex="0">`*

---

### 7. **Structure et titres** (Principe : Compréhensible)
- **Hiérarchie** : Structurer les contenus avec des balises HTML sémantiques (`<h1>` à `<h6>`).  
  *Exemple : `<h1>Titre principal</h1><h2>Sous-titre</h2>`*  
- **Landmarks** : Utiliser `header`, `nav`, `main`, `footer` pour définir des zones clés.  
  *Exemple : `<main role="main">Contenu principal</main>`*

---

### 8. **Multimédia** (Principe : perceptible)
- **Sous-titres et transcription** : Ajouter des sous-titres aux vidéos et une transcription textuelle.  
  *Exemple : `<track kind="subtitles" src="sous-titres.vtt">`*  
- **Descriptions audio (audiodescription)** : Fournir une description audio des éléments visuels importants.  

---

### 9. **Temps et animations** (Principe : utilisable)
- **Contrôle du temps** : Permettre de prolonger ou désactiver les délais.  
  *Exemple : Bouton "Prolonger le délai".*  
- **Réduire les animations** : Respecter le paramètre utilisateur "Réduire les animations".  
  *Exemple : `@media (prefers-reduced-motion: reduce) { animation: none; }`*

---

### 10. **Tableaux** (Principe : Perceptible)
- **Tableaux de données** :  
  - Titre explicite avec `<caption>`.  
  - En-têtes de colonnes (`<th scope="col">`) et lignes (`<th scope="row">`).  
  - Résumé pour les données complexes.  
- **Tableaux de mise en forme** :  
  - Utiliser `<table role="presentation">` pour les styles non liés à des données.  
  - S’assurer que les tableaux restent Compréhensibles une fois linéarisés.

---

### 11. **Liens** (Principe : Perceptible)
- **Liens explicites** :  
  - Intitulés clairs (éviter "Cliquez ici").  
  - Ajouter un `aria-label` ou `title` si le contexte seul ne suffit pas.  
- **Éviter les liens vides ou mal construits** :  
  - Par exemple : `<a><img alt=""></a>`.  
  - Attention aux répétitions inutiles (liens composites).

---

### 12. **Scripts** (Principe : Compréhensible)
- **Composants interactifs accessibles** :  
  - Menus déroulants, modales, carrousels, accordéons, etc.  
  - Commandes compatibles clavier/souris et technologies d’assistance.  
- **Messages de statut** :  
  - Utiliser les rôles ARIA adaptés :  
    - `role="alert"` pour les erreurs.  
    - `role="status"` pour les informations.  
    - `role="log"` pour les chats ou journaux.

---

### 13. **Éléments obligatoires & structures** (Principe : Compréhensible & Perceptible)
- **Code source** :
  - Respect des standards W3C (balises correctement ouvertes/fermées, valeurs uniques pour les attributs `id`, etc.).  
  *Outil : [W3C Validator](https://validator.w3.org/)*  
- **Balises et titres** :  
  - Langue par défaut définie.  
  - Chaque page a un titre unique et pertinent.  
- **Utilisation sémantique des balises** :  
  - Éviter les usages incorrects comme `<h>` pour des styles ou `<br>` pour les espacements.
- **Hiérarchie logique des titres** :  
  - Au moins un `<h1>` par page, suivi de niveaux cohérents (`<h2>`, `<h3>`, etc.).  
- **Éléments de structure** :  
  - `<header>`, `<main>`, `<footer>`, `<nav>`.  
  - Ajouter des `aria-label` pour préciser leur rôle (ex. : `aria-label="Navigation principale"`).  

---

### 14. **Présentation de l’information** (Principe : Perceptible)
- Utiliser des **feuilles de styles CSS** pour contrôler l’apparence (éviter les styles en HTML brut).  
- **Zoom et adaptabilité** :  
  - Contenu lisible à 200%.  
  - Garantir une version **responsive** pour mobile et desktop.  
- **Liens visibles** :  
  - Souligner ou différencier les liens par contraste (3:1 minimum).  

---

### 15. **Formulaires** (Principe :  Perceptible & Compréhensible)
- Associer chaque champ à une étiquette `<label>`.  
- Regrouper les champs similaires dans un `<fieldset>` avec `<legend>`.  
- Fournir :  
  - Intitulés explicites pour les champs.  
  - Messages d’aide à la saisie et erreurs claires.  
  - Indication des champs obligatoires.  

---

### 16. **Navigation** (Principe : Perceptible)
- Fournir **au moins deux systèmes de navigation** :  
  - Menu principal, plan de site ou moteur de recherche.  
- Navigation cohérente :  
  - Ordre logique pour le **tabulation** et pas de piège clavier (ex. : menus bloquants).  
  - **Prioriser les tabulations** : Utiliser `tabindex` pour définir l'ordre de navigation.  
    *Exemple :*
    ``` html
    <div tabindex="1">Premier élément</div>
    <div tabindex="2">Deuxième élément</div>
    <div tabindex="3">Troisième élément</div>
    ```
  - **Ordre naturel** : Laisser les éléments suivre l'ordre du DOM pour une navigation intuitive.
    *Exemple :*
    ``` html
    <button>Premier bouton</button>
    <a href="#">Premier lien</a>
    <input type="text" placeholder="Premier champ de texte">
    ```
- **Liens d’accès rapide** :  
  - Ex. : Aller directement au contenu principal.  
    *Exemple :*
    ``` html
    <a href="#main-content" class="skip-link">Aller au contenu principal</a>
    <main id="main-content">
      <!-- Contenu principal -->
    </main>
    ```

---

En suivant ces recommandations, vous garantissez un site accessible à la majorité des utilisateurs en situation de handicap.  
Ce guide résume l’essentiel des bonnes pratiques en accessibilité numérique pour rendre le contenu web utilisable et Compréhensible par tous,  
en tenant compte des limitations techniques et des besoins spécifiques des utilisateurs.  