# Configuration de l'environnement de travail

Il existe un archetype [maven](http://maven.apache.org) pour définir un artefact déploylable sur ELB. Le guide d'installation et de configuration se trouve [ici](http://docs.ingenieux.com.br/project/beanstalker/). 

En suivant ce guide:

1. Configurer vos credentials dans `~/.m2/settings.xml`
2. Utilisez l'archetype pour créer le projet maven
3. Une fois l'archetype créé
	- changer la région à utiliser en `eu-west-1`
	- change le type d'instance `SingleInstance` en `LoadBalanced`
4. Lisez le fichier `README.md`
5. Lisez le une deuxième fois
6. Déployez l'application squelette par git
7. Créez l'environnement. Si le nom DNS n'est pas disponible, il faut changer la valeur de `beanstalk.cnamePrefix`
8. Une fois déployé, une requête GET sur `/services/api/v1/debug` devrait aboutir

9. Rajouter une API rest pour le fun. Pour redéployer, il faut rajouter le goal `update-environment` au profil `fast-deploy`, goal `deploy`.

9. Continuez la configuration de l'instance pour permettre le healthcheck. Il faut pensez à déclarer les noms de clef et le profile IAM dans le pom.xml

10. Le profile `worker est déjà disponible pour créer un tier worker au besoin.
	- définissez le tier worker
	- comme le war est commun avec le tier web, le goal `update-environment` suffira à mettre à jour le tier

11. Tester depuis la console SQS l'envoie de message dans la queue. Un tour dans les logs du worker permettra de suivre l'acheminement.
