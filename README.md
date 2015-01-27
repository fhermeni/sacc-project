# Tweetalytics

Une application cloud native permettant d'exécuter à la demande, des analyses du flux publique de twitter.
Cela peut servir par exemple à:
- cartographier les hashtags sur une région
- analyser la distribution de hashtags sur le temps
- suivre l'évolution des tendances (votes)
- ...

L'application est développée pour un hébergement sur le cloud de Amazon au travers de `Amazon Elastic Beanstalk`

## Fonctionnalités

- définir (et réviser au besoin) la requête de base à utiliser sur le flux public
- capturer et stocker le flux dans une base de données DynamoDB
- accepter des demandes d'analyses sur les données stockées. Une demande consistera en une requête à exécuter. L'application doit pouvoir gérer plusieurs analyses.
- l'emetteur de l'analyse doit pouvoir à tout moment consulter ses analyses, les supprimer, les relancer, interrompre celles en cours.
- notifier l'emetteur d'une analyse une fois celle-ci effectuée
- une architecture REST pour communiquer entre les clients et le service. Des échanges au format JSON ou XML.

_Attention_, ne pas tomber dans l'excès sur le support de requêtes d'analyses. Il n'y a pas de support SQL et si vous souhaitez obtenir de bonnes performance, il vaut mieux restreindre le domaine.

## Environnement de travail

- java + maven. Voir [CONFIGURE.md](CONFIGURE.md)
- git pour la gestion des sources. Code de production à déposer dans la branche `master`

## Resources

- guide développeur pour utiliser l'API streaming de twitter: https://dev.twitter.com/streaming/overview
- guide développeur pour Amazon Elastic Beanstalk: http://aws.amazon.com/elasticbeanstalk/developer-resources/
- un client Java pour l'API streaming de Twitter: https://github.com/twitter/hbc
- exécution de requêtes sur une base DynamoDB: http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/QueryAndScan.html
- Beanstalker, le plugin pour déployer du projet maven sur Elastic BeanStalk: http://docs.ingenieux.com.br/project/beanstalker/

## À rendre dans votre [rapport](rapport.pdf)
- le nom des membres de l'équipe
- L'URL de votre repository Git. La branche 'master' sera récupérée une fois la deadline passée
- l'URL où l'application est déployée
- un accès au dashboard de l'application sur AWS de manière à observer la configuration, les règles d'élasticité, ...
- un rapport contenant:
  - une description de ce que vous avez fait/pas fait et pourquoi
  - une description justifiée de l'architecture de l'application
  - les types d'analyse supportées
  - un modèle de coût: Combien coûte l'application par mois en fonction de différents facteurs.
  - des points notables concernant l'implantation 
  - l'API REST mise à disposition des clients
  - tout ce qui est nécessaire pour tester l'application en ligne facilement
  - un retour sur votre vision du projet et du module
