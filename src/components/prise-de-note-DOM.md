# DOM, kesseussé

> JavaScript et le DOM

En JS, tout ce qui concerne le DOM passe par l'objet `document`

## Récupérer des éléments (des "balises") depuis le HTML

`document` sélectionne la balise `html` de notre page, c'est à dire, toute notre page
`document.head` sélectionne la balise `head` de notre page
`document.body` sélectionne la balise `body` de notre page

`document.getElementById('')` retourne L'élément ayant l'ID passé en paramètre
`document.getElementsByClassName('')` retourne un tableau de tous les éléments ayant cette classe CSS
`document.getElementsByTagName('')` retourne un tableau de tous les éléments dont la balise est celle passée en paramètre

`document.querySelector('')` retourne le premier élément qui matche avec le sélecteur CSS passé en paramètre
`document.querySelectorAll('')` retourne tous les éléments qui matchent avec le sélecteur CSS passé en paramètre

### Quelques exemples

```javascript
// Pour récupérer toutes les checkbox d'une page :
document.querySelectorAll('input[type=checkbox]')
// Pour récupérer tous les inputs cochés de type radio :
document.querySelectorAll('input[type=radio]').forEach(item => item.checked? console.log(item): null)
```

!!! note

    Toutes les méthodes vues jusque là retournent un élément ou une liste d'éléments.
    On peut donc stocker ces valeurs dans des variables pour les utiliser plus tard

## Accéder au contenu des éléments (les "balises")

### Fonctionnent sur toutes les balises HTML :

`.innerText` pour récupérer le contenu textuel d'une balise (pas les balises qui se trouveraient éventuellement à l'intérieur, juste le texte)
`.innerHTML` pour récupérer TOUT ce qui se trouve dans la balise (texte et autres balises HTML)

`.value` permet de récupérer la valeur d'un input (marche sur tous les inputs et textarea et select)

`.classList` pour récupérer la liste de toutes les classes CSS d'un élément
`.getValue('')` permet de récupérer la valeur de l'attribut demandé en paramètre

## Modifier le contenu de balises

```javascript
// Modifier le contenun textuel de la 2ème balise h2 de la page en cours :
document.querySelectorAll('h2')[1].innerText = 'A propos'
// Si mon élément #name est un champ de formulaire, son contenu/sa valeur est maintenant 'coucou' :
document.querySelector('#name').value = 'coucou'
// Si je veux "switcher" un champ pour afficher/masquer le mot de passe, je peux utiliser la ligne suivante :
field.type = field.type === 'text'? 'password': 'text'
// Faire cliquer automatiquement sur le troisième bouton de notre page :
document.querySelectorAll('button')[2].click()
// Ajouter (ou modifier) l'attribut title de notre 2ème bouton pour lui donner la valeur "coincoin"
document.querySelectorAll('button')[1].setAttribute('title', 'coincoin')
```

## Manipuler les noeuds du DOM

`.remove()` supprime l'élément du DOM
`.parentElement()`
`.children()`
`.nextSibbling()`
`.previousSibbling()`

```javascript
// créer une section, avec un title, une classe CSS et l'ajoute après le 3ème bouton
const nouvelleSection = document.createElement('section')
nouvelleSection.innerText = 'bienvenue'
nouvellesection.setAttribute('title', 'contactez-nous')
nouvellesection.classList.add('important')
document.querySelectorAll('button')[2].after(nouvelleSection)
```
