# CM-Bot-Twitter-
Un Bot Twitter qui Aime, Tweet et Produit du contenu sur votre fil d'actualité dans votre domaine d'activité.

## Descritpion
Ce Bot Twitter est conçu pour animer un fil d'actualité Twitter à votre place. Il Like, Tweet du contenu structuré et sur-mesure (des articles de presse) correspondant à votre domaine d'activité.<br />De plus, il permet de poster du contenu créé par vos soins pour faire la promotion de votre activité, de vos services, etc ...<br />
Le but de cet outil est de générer régulièrement de la présence, de l'affichage et donc du traffic vers votre site ou vos services.

## Pré-Requis
Les scripts .php nécessitent d'être executés régulièrement par des tâches CRON. Pour effectuer cela, vous devez disposer : 
- D'un hébergement Linux associé au nom de domaine de votre site-web par exemple.
	- Si vous ne disposez pas d'un tel hébergement, voici ceux que j'utilise : https://www.amen.fr/hebergement-web/linux/comparatif/
- D'un compte Twitter
- D'une App Twitter 
- D'un éditeur de texte avec coloration syntaxique tel que [ATOM](https://atom.io/)

## Création de l'App Twitter
Pour créer une App Twitter en quelques minutes, rendez-vous sur https://apps.twitter.com/ et cliquez sur **Create New App**
- Saisissez le nom, l'URL du site-web qui hébergera les fichiers CRON et une petite description courte de votre projet 
	- Exemple : Un Bot Twitter efficace qui fait tout à ma place.
- Cochez la case des CGU.
Une fois arrivé sur le compte de votre nouvelle App Twitter : 
- Cliquez sur Keys & Access Tokens
- Notez la**Consumer Key (API Key)** et la clé **Consumer Secret (API Secret)** de côté.
- Cliquez ensuite sur **Create my access Token** tout en bas de cette meme page.
- Notez de côté de nouveau ces 2 identifiants qui vous serviront par la suite
- Votre App Twitter est prête et configurée !

## Installation des Fichiers
- Téléchargez le contenu du dépot et dézippez le sur votre bureau.
- Renommez ce dossier en "**Tweets_auto**" pour plus de facilité par la suite.
- Ouvrez le fichier config.php pour remplir les clés que vous avez noté lors de la création de votre App Twitter.
```
<?php
$settings = array(
    'oauth_access_token' => "XXXXX",
    'oauth_access_token_secret' => "XXXXX",
    'consumer_key' => "XXXXX",
    'consumer_secret' => "XXXXX"
);
?>
```
## Configuration
## Aller + loin
## Contacts
