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
- D'une [App Twitter](https://apps.twitter.com/) 
- D'une API Key [Google News](https://newsapi.org/docs/get-started)
- D'un éditeur de texte avec coloration syntaxique tel que [ATOM](https://atom.io/)

## API Key Google News
Vous devez disposer de cette clé pour interroger la base de données en temps réel de Google. Pour cela, rendez-vous sur [Google News](https://newsapi.org/docs/get-started) et enregistrez-vous avec votre compte Google.<br />
Vous obtiendrez alors votre API Key. Notez-la dans un endroit et mettez-la de côté.

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
- Vos fichiers sont maintenant connectés avec votre App Twitter

## Configuration des Fichiers
**Configuration des Likes Auto**<br />
Le modèle de base utilisé est _like1.php_. Il vous suffit juste paramétrer une ligne dans ce fichier pour dire au Bot ce qu'il doit aimer :
```
$getfield = '?q=#SEO&lang=fr&result_type=recent&count=10';
```
Les 2 paramètres réglables sont :
- **q=**
	- Ajoutez ici le Hastag souhaité (Exemple : q=#Chatbot)
- **count=**
	- Saisissez ici le nombre de tweets que le script aimera automatiquement à chaque execution. (ne pas dépasser les 30). Exemple count=10
    
Vous pouvez donc dupliquer ce modèle de fichier à l'infini et changer uniquement ces 2 paramètres. Votre Compte Twitter aimera alors automatiquement de nombreux tweets dont les Hastags seront paramétrés dans ces fichiers avec comme regèle : 1 fichier .php = 1 Hastag associé !

**Configuration des Publications d'articles de Presse Auto**<br />
Le modèle de base utilisé est _presse1.php_.  Pour chacun de vos fichiers, vous devrez paramétrer ces variables de cette manière : <br />
```
$keyword = 'Chatbot';
$hashtag = '#Robot';
$keyword_sans_majuscule = 'chatbot';
```
- $keyword représente le mot qui sera recherché dans la base de données de Google News
- $hastag représente le Hastag Twitter le plus proche (un synonyme) de $keyword
- $keyword_sans_majuscule représente $keyword sans aucune majuscule

Ensuite, vous devez paramétrer les Hastags aléatoires (afin d'eviter que plusieurs de vos tweets se ressemblent, j'utilise cette technique aléatoire) : 
```
$mot_cle = array("#ChatBots", "#NLP", "#Ai", "#IA", "#machinelearning");
```

Vous pouvez donc ici ajouter jusqu'à 10 Hastags autour de la variable $keyword (des mots ou expressions en rapport avec ce mot).

Vous pouvez donc dupliquer ce modèle de fichier à l'infini et changer uniquement ces 4 paramètres. Votre Compte Twitter publiera alors automatiquement de nombreux articles de presse dont les Hastags et le contenu seront paramétrés dans ces fichiers avec comme regèle : 1 fichier .php = 1 thème (mot clé).

## Configuration des Tâches CRON
## Aller + loin
## Contacts
