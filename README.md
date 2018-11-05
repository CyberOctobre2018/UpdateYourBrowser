
# Bandeau sensibilisation opération Octobre Cybersécurité 

Comme l’année précédente, le service du haut fonctionnaire de défense et de sécurité va organiser une campagne de sensibilisation au risque cybernétique en octobre 2018. L’objectif est de diffuser des messages de prévention simples à mettre en œuvre auprès de deux publics : les agents du ministère et les entreprises des secteurs sous tutelle ministérielle.

Cette année, la communication s’articule autour de la mise à jour de ses logiciels, et en particulier du navigateur. Le SHFDS distribue la présente bibliothèque pour afficher sur votre site un bandeau indiquant aux utilisateurs si leur navigateur est à jour. Ainsi, ils constateront d'eux-même qu'ils utilisent avec un navigateur ancien, ne disposant donc pas des dernières fonctions de sécurité et présentant des failles de sécurité connues.


## configuration HTML: [Pour installer](INSTALL.md)
## Plus d'informations sur la configuration des options du bandeau                     
## 1. Options

Différentes options sont configurables :

- La période à laquelle le bandeau est actif (startDate -> endDate)

- Les versions supportées minimum par navigateur

- Les versions long time support uniques avec leur date de build (Firefox est concerné)

- L’activation/désactivation pour windows XP d'un message spécifique (xpMode)

- L’activation/désactivation pour les plateformes mobiles (androidMode)

- Le formatting : La couleur du texte et du lien, le corps du texte et du liens, le lien en lui même  

Elles se paramètrent dans la variable « _umb » et sont toutes optionnelles.

 
## 2. Version requise  

Elle est définie par navigateur dans une liste nommée « require » et une liste « current »:

La version par défaut :
```javascript
require: {
     chrome :  "68" ,
     firefox : "61",
     ie : "11",
     opera : "53",
     safari : "11",
     edge : "17"
},
current: {
     chrome :  "68" ,
     firefox : "61",
     ie : "11",
     opera : "53",
     safari : "11",
     edge : "17"
},
``` 
Suite aux versions LTS, certains canaux de navigateurs à jour en termes de sécurité reste à une version antérieure. Il est possible de préciser une version acceptable de firefox et de spécifier une builddate : 
```javascript
esr: {
    firefox : "52"},
build: {
    firefox : "20180621121600"}; // version ultérieur au 21 juin 2018
```	
	
## 3. Définition du message :

Il est possible de définir une charte de message spécifique à votre site web,
```javascript
message: {
     color : "#FDF2AB", // couleur du fond
     textColor : "black" // couleur du texte
     linkColor : "black" // couleur du texte
  }
```
## 4. Chargement du bandeau :

 Il est réalisé à travers le snippet de code suivant :
```javascript
(function(u,v) { var s = document.createElement('script'); s.async = true; s.src = u;s.integrity = v; var b = document.getElementsByTagName('script'); b.parentNode.insertBefore(s, b); }) ('umb2.js',"sha25-signcurrentbuild");
```

avec **signcurrentbuild** la signature actuel du fichier.
Un script python est fourni pour signer ou fournir automatiquement la signature CSP.

## 5. Pages de test :

- Une page par défaut est disponible pour voir comment fonctionne le script :
https://cyberoctobre2018.github.io/UpdateYourBrowser/test/wikipedia-mef/indexdefaut.html
- Une page avec la configuration ci dessous est disponible pour voir comment fonctionne le script :
https://cyberoctobre2018.github.io/UpdateYourBrowser/test/wikipedia-mef/index.html
- Une page mobile avec la configuration ci dessous est disponible pour voir comment fonctionne le script sur un appareil mobile:
https://cyberoctobre2018.github.io/UpdateYourBrowser/test/wikipedia-mef-mobile/index-mobile.html
configuration :
```javascript
	var _umb = {   require: {    chrome : "68",    firefox : "61",
		opera : "53",    ie : "11",    safari : "11",    edge : "17"},
				current: {    chrome : "68",    firefox : "61",
		opera : "53",    ie : "11",    safari : "11",    edge : "17"},
				esr: { firefox : "52"},
				build: { firefox : "20180621121600"},
				display : true,   
				nonCritical: true,   
				startDate: "2017-12",   
				endDate: "2019-12",   
				message:{     
				backgroundColor : "red",
				backgroundUpdateColor : "#00ff80",
				textUpdateColor : "white",
				textColor: "white",
				linkColor: "grey",
				linkURL: "economie.gouv.fr"
				}  
			};
```

