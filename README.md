# KAFKA

Part 1 - Even Driven Distributed Processing With Spring Cloud Stream Functions - KAFKA Broker

Tout dabord on commence par le démarrage de serveur zookeeper en ligne de commande (cmd) :

![image](https://user-images.githubusercontent.com/78086000/172024515-47950cee-c4a2-43ed-b5cb-32d528471384.png)

Une fois zookeeper est démarré on va démarrer le serveur KAFKA en ligne de commande (cmd) :

![image](https://user-images.githubusercontent.com/78086000/172024674-b8eb63ed-2126-47d3-bdf4-cc5219367c5d.png)

Puis on démarre l'outil kafka-console-consumer en ligne de commande (cmd) en spécifiant l'emplacement où il se trouve kafka avec l'option --bootstrap-server localhost:9092 et le nom de topic avec l'option --topic R1 :

![image](https://user-images.githubusercontent.com/78086000/172025081-5709602d-57bd-444e-a3b0-2a531376d855.png)

Pour envoyer des messages vers ce topic on va lancer kafka-console-producer :

![image](https://user-images.githubusercontent.com/78086000/172025268-37de7e47-e5a3-4c7c-9675-0305d22c4deb.png)

Maintenant on envoie des messages par le producer et on teste s'ils vont arrivés au consommateur via le broker kafka :

![image](https://user-images.githubusercontent.com/78086000/172025363-c4403311-649b-47c5-aa68-da3464edeaf0.png)

Après avoir tester le fonctionnement de broker kafka avec kafka-console-consumer et kafka-console-producer on passe à la création d'une application Spring Boot dans la quelle on va essayer de produire des messages dans un topic.

Dans le premièr cas on publie des messages vers le topic kafka à travers d'un RestController pour q'un consommateur kafka-console-consumer  puisse les consommer :

![image](https://user-images.githubusercontent.com/78086000/172027212-4aa0e4e9-fbdf-4388-afd2-df512ea47ef6.png)

Dans le deuxième cas au lieu d'utiliser kafka-console-consumer on va créer un consumer qui va écouter le topic et de lire les messages qui arrivent sur le topic :

![image](https://user-images.githubusercontent.com/78086000/172027990-22aac80b-8b8d-4d8b-9eca-c37cf5f8904a.png)

Pour le troisième cas au lieu d'utiliser kafka-console-producer on va créer un producer qui va produire des streams vers le topic chaque seconde :

![image](https://user-images.githubusercontent.com/78086000/172049761-9a873498-49a9-4f49-80df-6ba658d864b7.png)

Dans le quatrième cas on va créer à la fois un producer et un consumer :

![image](https://user-images.githubusercontent.com/78086000/172049826-3d196789-c334-4b1f-b718-cd6f89890240.png)

Après pour traiter les flux de message en temps réel nous avons utilisés kafka stream :

![image](https://user-images.githubusercontent.com/78086000/172077489-5af509c2-a6e1-4846-b8cb-7635a2f87339.png)

Pour accélérer l'affichage des résultats (statistiques) fournit par kafka stream on va le faire commiter les résultat au bout de chaque seconde :

![image](https://user-images.githubusercontent.com/78086000/172078092-e965bff2-34c5-448d-ab72-f8db40287418.png)

Pour éviter le cumul des résultats on va faire des statistiques sur une fenêtre de temps de 5 secondes en utilisant un opérateur de fenêtrage qui s'appelle windowedBy : 

![image](https://user-images.githubusercontent.com/78086000/172160146-cae199b0-e071-4075-b5d1-13348de139f3.png)

Pour utiliser les résultats provenant de ktable dans une application on peut les percister dans un store :

Interroger Kafka-streams Store avec Server Sent Event :
Une fois le client établit une connexion http (la connexion reste ouverte), le serveur va poucer les données vers le client 

![image](https://user-images.githubusercontent.com/78086000/172172998-3d1208a3-7355-4a70-85a6-12769889759b.png)

Client HTML Server Sent Event :

![image](https://user-images.githubusercontent.com/78086000/172179335-ef96241a-d811-4e81-89eb-cdd7e41525bd.png)













