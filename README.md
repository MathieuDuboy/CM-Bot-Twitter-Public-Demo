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
Vos fichiers doivent maintenant être paramétrés manuellement un à un comme suit :

### Configuration des Likes Auto
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

### Configuration des Publications d'articles de Presse Auto
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

### Configuration des Publications de promotion de votre activité
Le fichier utilisé est _promotion.php_. Vous allez devoir configurer à l'intérieur de celui-ci un tableau de 2 à 100 publicités (je ne vous conseille pas d'aller plus loin que 100 mais vous pouvez) de cette manière : <br />
```
$boite = "MonTitre | Ceci est mon Titre accrocheur utilisé sur toutes mes publications\r\n";
```
Une fois cette variable (qui restera inchangée) paramétrée, vous devez créer le tableau PHP de vos offres, vos publicités, etc. <br />
```
$tweets_variables = array(
  $boite."▶ Une promotion, un service ici pas trop long\r\nDes hastags, des mots clés
  \r\n\r\n".$date."contact@maboite.com 2 ou 3 Hastags https://www.unlienici.com",
  $boite."▶ Une promotion, une promotion ici pas trop longue\r\nDes hastags, des mots clés
  \r\n\r\n".$date."contact@maboite.com 2 ou 3 Hastags https://www.unlienici.com",
  ... // ici vous pouvez en créer 100
  $boite."▶ Une promotion, un service ici pas trop long\r\nDes hastags, des mots clés
  \r\n\r\n".$date."contact@maboite.com 2 ou 3 Hastags https://www.unlienici.com"
);
```
A chaque exécution de ce script sera tiré au sort un tweets parmi ce tableau et il sera ensuite formaté et envoyé sur votre fil d'actualité comme si c'etait un humain qui l'avait publié.

## Configuration des Tâches CRON
Pour exécuter les fichers promotions.php, like1.php et presse1.php, vous devez configurer des tâches récurrentes. Pour éviter de faire trop "Robot", voici ce que je vous conseille :<br />
- Publiez une promotion toutes les 2 heures max
- Publiez des news toutes les 6 heures
- Likez 10 ou 20 tweets toutes les heures

De cette manière, votre ascension et votre taux de publication sera progressif et non violent aux yeux de vos Followers. Le contenu sera riche et varié et ceux-ci seront ravis de vous suivre et d'être informé de toutes ces nouveautés dans votre domaine d'activité.

- Commencez par héberger dans un sous-dossier du nom de domaine de votre choix (peu importe le nom de domaine) l'ensemble des fichiers configurés du dépot.
- Notez l'adresse relative à ce dossier
- Ouvrez ensuite votre Panneau de configuration des tâches CRON (ici dans mon cas, [cPanel](https://cpanel.com/))
- Ajoutez une tâche CRON et sélectionnez une heure d'éxecution de votre tâche
- Dans le Champs "Command" ajoutez une commande comme ceci en utilisant wget
```
wget https://mon-chatbot.com/tweets_auto/cron_relation_client.php >/dev/null 2>&1
```

l'argument ```>/dev/null 2>&1``` vous permet de ne pas être notifié par email lors de l'execution de cette commande.

## Aller + loin
## Contacts
