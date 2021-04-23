# axel
Tests checklist Pedro
===============

## Tester le déploiement

-[ ] Je dois pouvoir mettre a jour le projet avec git puis lancer "update.bat" sans avoir d'erreur.\
- [ ] Les containers sont lancés (docker-compose ps).

## Test Hi5 / Creation de session

- [ ] Je valide que je peux créer une session Hi5\
- [ ] Je valide que je peux créer une autre Hi5 et que quand je clic sur valider j'en ai pas 2 qui s'ajoutent.\
- [ ] Je valide que je peux ajouter 10 joueurs a la session, mais que je ne peux pas mettre de 11e.\
- [ ] Je valide que je peux supprimer un joueur d'une session Hi5

## Test Hi5 / Session avec joueurs

### Sur la borne terrain je dois voir la session Hi5.
- [ ] je valide que je ne peux pas mettre 6 joueurs dans une equipe.\
- [ ] Je valide que je peux changer les équipes sur la page rules.

### Je démarre le match:
- [ ] Je valide que les sons sont présent (debut de match et buts)\
- [ ] Je valide le fait d'ajouter un but, un but avec passeur, un moment clé, un csc\
- [ ] Je valide l'annulation de but qui s'effectue dans le bon ordre jusqu'a 0\
- [ ] Je valide que je peux terminer le match en avant.
- [ ] Je valide en bdd que le score, la duration, le status en played sont correct\
- [ ] Je valide sur le serveur que les vidéos sont bien présente et que la durée correspond bien\

## Test Hi5 / Session sans joueurs

Sur la borne terrain je dois voir la session Hi5.
Pendant que je suis sur l'écran de sélection des équipes, ajouter un joueur via la borne inscription: la page doit se recharger avec le nouveau joueur.\
Ensuite lancer la session mettre 2, 3 actions et laisser tourner pendant une 1h\
- [ ] Je valide en bdd que le score, la duration, le status en played sont correct a la fin du match.\
- [ ] Je valide sur le serveur que les vidéos sont bien présente et que la durée correspond bien

## Test Planning

### Sur la borne planning
- [ ] Je dois pouvoir créer une session Ec1, elle s'affiche\
- [ ] Je dois pouvoir créer une session Ec1 rapide, elle s'affiche\
- [ ] Je dois pouvoir créer une session Hi5, elle s'affiche\
- [ ] Je dois pouvoir modifier une session Ec1, elle s'affiche\
- [ ] Je dois pouvoir modifier une session Hi5, elle s'affiche\
- [ ] Je dois pouvoir supprimer une session Ec1, elle disparait\
- [ ] Je dois pouvoir supprimer une session Hi5, elle disparait

## Test EasyConnect

### Sur la borne Terrain 2,
- [ ] Lancer une session de la durée de ton choix et ajouter/supprimer des evenements (buts + garder action)\
- [ ] Terminer la session en avance, valider que le graphique des buts est correct.\
- [ ] Je valide en bdd que le score, la duration, le status en played sont correct a la fin du match.\
- [ ] Lancer une session 1h et la laisser tourner.\
- [ ] A la fin du match, valider que le graphique des buts est correct.\
- [ ] Je valide en bdd que le score, la duration, le status en played sont correct a la fin du match.\
- [ ] Je valide sur le serveur que les vidéos sont bien présente et que la durée correspond bien

## Test Mode incognito

- [ ] Je valide que je peux lancer le mode incognito\
- [ ] Je valide en bdd que le status passe bien de playing a played a la fin de la partie.\
- [ ] Je valide que quand je rentre et sors AVANT que la page soit loadé je n'ai pas d'erreur.

## NgtvSession
Envoyer deux evenements:
- au demarage de la session poster un event : localhost:82/fields/118/events/star.json 
- verifier qu'un nouvel event est apparu pour la ngtvsession en cours
- x2
    - [ ] Je valide que 2 events sont apparuent sur la ngtvSession en cours.

## Test Customer

- [ ] Je valide que je peux lancer une session customer.\
- [ ] Je valide que je peux l'arreter.\
- [ ] Je valide qu'en BDD j'ai bien la session.\
- [ ] Je valide que j'ai bien la vidéo.

## Test Airfly (autre sport)
- [ ] Je valide que depuis la page customer je peux lancer une session.\
- [ ] Je valide que les infos s'affichent bien en bdd.\
- [ ] A la fin de la session je reviens sur la page customer.\
- [ ] Les donnees se mettent bien a jour en bdd a la fin de la session.\
- [ ] Je valide que j'ai bien la vidéo.

## Test Postmatch

- [ ] Je lance le script 'reset-demo-commercial.bat'\
- [ ] Je valide que le match apparait sur le postmatch\
- [ ] Je valide qu'il y ait bien la vidéo & les stats\
- [ ] Je valide le résumé automatique

## Test Video / Events

- [ ] format matchTimecode\
- [ ] position matchTimeCode\
- [ ] caractéres spéciaux\
- [ ] generation miniature\
- [ ] longueur nom equipe\
- [ ] positionnement des elements en fonction de la video (hd/sd)

## Test Video / Match

- [ ] format matchTimecode\
- [ ] position matchTimeCode\
- [ ] caractéres spéciaux\
- [ ] longueur nom equipe\
- [ ] positionnement des elements en fonction de la video (hd/sd)\
- [ ]] verifier durée de la video\
- [ ] verifier la presence du message publicitaire, s'il n'est pas censé y avoir de message publicitaire, la barre dans laquelle il s'affiche ne doit pas être présente.

## Test Video / Padel

- [ ] Sur les videos des puntacos verifier la presence du logo

## Test Video / Compilation

- [ ] Sur les videos des puntacos verifier la presence du logo - Verifier le preroll

## Test FFF / Creation session

- [ ] Au clic sur demarrer enregistrement:\
- [ ] une session doit se créer dans fff_session\
- [ ] le status doit être playing\
- [ ] la duration à 10800\
- [ ] un dossier doit se creer dans le .docker (nom= reference)

## Test FFF / Match

- [ ] Match non commencé & Calcul des stats en pause doivent s'afficher

### Demarrer match:
- [ ] les pids doivent apparaîtrent dans fff_session
- [ ] dans fff_session_events : stats_in et session_start => même videoTimecode
- [ ] message: Calcul des stats en cours

### Mi-temps
- [ ] dans fff_session_events : stats_out et half_time_in => même videoTimecode\
- [ ] message: Calcul des stats en pause

### Fin mi-temps:
- [ ] dans fff_session_events : stats_in et half_time_out => même videoTimecode\
- [ ] message: Calcul des stats en cours

### Suspendre les stats:
- [ ] stats_out & message: Calcul des stats en pause

### Arreter match :
dans fff_session :

- [ ]status= played\
- [ ] date de fin: moment arrêt match\
- [ ] duration: maj\
- [ ] retour sur la page de creation de session

Point d'attention\
⚠️ si le match est démarré ET que les stats sont en pause Et que j'appuie sur siffler mi-temps il ne doit PAS y avoir de nouvel evenement stats_out.\
⚠️ si le match est en pause ET que les stats sont en demarrées Et que j'appuie sur demarrer seconde mi-temps il ne doit PAS y avoir de nouvel evenement stats_in.\
⚠️ si le match n'est jamais  arrete en appuyant sur arreter le match, il doit s'arréter tout seul au bout des trois heures, envoyer toutes les données de fin de match et revenir sur la page de creation de session

