# Introduction 
Tout d'abord je souheterais souligner l'importance d'avoir une bonne structure de fichier dans vos projets.

Une architercute de dossiers correct rend notre projet plus facile a prendre en main, par des future collaborateur et aussi par nous même dans le cas ou on doit retourner à un projet plusieur mois plus tard.

Elle nous donne aussi la possibiliter de pouvoir naviguer à travers notre projet plus facilement/rapidement.

# La structure de fichier avec  React

Pour le meilleur ou pour le pire, React n'impose pas une manière particuliére sur l'organisation des projets React, cependant il existe plusieurs approches populaires dans son écosystème, que vous êtes libre de decouvrire à votre temps.

# Une Approche
L'aproche que je vais vous présenter consite a grouper les différentes parties de votre code tells que les composants, les custom hooks, les rêquete aux api... Dans des dossier specifiques à leur fonction.

On pourrais par example dans le dossier `components` grouper tous les fichiers en lien aven un composant dans un dossier portant le nom de ce composant. Concretement cela resemble à ça: 
``
```
- src
	-- components
		--- Article
			---- index.js
			---- style.css
- App.js
- Readme.md
```

Supposons que votre application doit faire appel à une api pour récupérer des données cette même logique:

```
- src
	-- components
    -- requests
	   	 --- contacts.api.js
	   	 --- companies.api.js
		 --- invoices.api.js
- App.js
- Readme.md
```

En programation il arrive souvent qu'on créer des fonctions utilitaires en peu générique qui peuvent servir à convertir une date ou à traiter du text... Pour ce type de fonction on peut créer un dossier `utils` qui contiendra les fichier `js` associer à chaque bout de code portant sur une fonction 

```
- src
    -- components
    -- requests
    -- utils
	   	 --- text.utils.js
	   	 --- dates.utils.js
- App.js
- Readme.md

```

# Conclusion

La separation du code en fonction du domaine dans lequelle il agit est un concepte asser courant en progammation. 
Vous allez rencontrer ou avais déjà rencontré le terme ==Separation of Concerns== ou ==Séparation des responsabilités==. C'est un principe de conception visant à segmenter un programme informatique en plusieurs parties afin que chacune d'entre elles gère un aspect du programme. Il existe plusieur façon d'implémenter ce principe, celui que vous utiliserez dependra de vos préférences, des convations établis par la communauté ou concepteur du language/framework que vous utiliser ainsi que de l'entreprise à laquelle vous travaillerez.