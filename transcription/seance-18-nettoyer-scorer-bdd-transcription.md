# Séance 18 - Transcription brute

- Durée détectée : 01:01:47
- Langue : fr

## Segments

### 00:00 - 00:06
Ok c'est parti maintenant on va passer à la partie nettoyer et scorer donc on va

### 00:06 - 00:12
créer la version finale de notre BDD pour la prospection automatisée on le

### 00:12 - 00:16
sait qu'une base enrichie n'est pas encore une base exploitable le but ça

### 00:16 - 00:21
va être de la nettoyer ensuite de la scorer et ensuite de la préparer pour

### 00:21 - 00:26
faire de l'outreach pour notre CRM pour de la segmentation et puis pour le

### 00:26 - 00:31
Donc la stratégie, on l'a vu, c'est qu'on a enrichi avec

### 00:31 - 00:38
HAPIFI, ensuite on a dédupliqué, on a validé le contact, on a fait un score

### 00:38 - 00:42
final, on va faire un segment message et on va faire un lead screen CRM.

### 00:42 - 00:47
Donc la règle de cette séance c'est qu'on lance pas une prospection tant que

### 00:47 - 00:51
la base ne s'est pas distinguée, prêt à contacter du coup nos

### 00:51 - 00:55
contacts, à vérifier, à exclure et enrichir plus tard.

### 00:55 - 01:01
notre objectif c'est encore récupérer des doublons qu'on a dans notre BDD que

### 01:01 - 01:06
Cloud Code n'a pas su trouver donc ça ça va être important aussi de le faire

### 01:06 - 01:11
c'est pour ça que derrière on va créer des règles pour que si une adresse est

### 01:11 - 01:14
similaire on fait sauter ce lit là en question

### 01:14 - 01:18
donc ça va être encore une histoire de prompte, une stratégie, une mise en

### 01:18 - 01:22
place et une réflexion de la part de codex pour qu'on ait une BDD

### 01:22 - 01:29
exploitable par la suite. Donc les champs qui doivent devenir utilisables pour ensuite faire

### 01:29 - 01:35
de la prospection c'est la syntaxe type donc e-mail propre, source, statut, vérification,

### 01:35 - 01:44
le format français lisible et le canal recommandé normalisé et la partie audit donc la preuve de

### 01:44 - 01:48
chaque contact ça va être important ensuite pour la rédaction du message. Je sais que dans

### 01:48 - 01:52
notre BDD on a déjà un message prédéfini mais l'objectif ça va être de le suivre

### 01:52 - 01:58
personnalisé pour que derrière chaque prospect du coup et un message qui

### 01:58 - 02:05
correspond exactement à son entreprise et du coup on a plus de chance ensuite de

### 02:05 - 02:08
bouquer un RDV avec cette personne là c'est ce qu'on va voir lors de la

### 02:08 - 02:14
prochaine séance quand on va créer tout ce système là sur une adresse

### 02:14 - 02:20
email l'objectif ça va être aussi de scorer donc on va combiner les trois

### 02:20 - 02:27
séances précédentes avec le legal confidence score, la contactability score, le fit score,

### 02:27 - 02:32
le pain score, le timing score, donc ça c'est tout ce qu'on a fait ensuite on va créer vraiment

### 02:32 - 02:44
un regroupement du total complet de ces notes là. Donc le CRM doit imposer une action claire

### 02:44 - 02:52
A plus contact complet fit for anglo clair A très bon prêt pour l'e-mail ou appel B

### 02:52 - 02:56
exploitable mais moins prioritaire, c'est à enrichir des ne pas contactés.

### 02:56 - 03:01
Donc la prescription automatisée a besoin d'un segment pas d'une seule liste.

### 03:01 - 03:05
Par exemple, un restaurant gastronomique, une brasserie et un

### 03:05 - 03:08
traiteur n'ont pas la même douleur ni le même message. C'est pour ça qu'on

### 03:08 - 03:12
va vraiment essayer de comprendre ce que veut notre cible.

### 03:12 - 03:18
Donc le prospect qu'on a scrapté, qu'on a trouvé, va falloir qu'on comprenne son

### 03:18 - 03:24
besoin, on ne peut pas se permettre d'aller chercher un restaurateur, j'espère que tu vas bien,

### 03:24 - 03:32
j'aimerais te vendre, je ne sais pas, un truc qui n'a rien à voir, un profil LinkedIn automatisé,

### 03:32 - 03:37
il s'en fout, lui il veut des clients directement sur son restaurant, donc c'est ce qu'on va essayer

### 03:37 - 03:43
de faire justement, donc encore une fois on part d'un prompt, donc ça va être ce prompt là

### 03:43 - 03:47
qui va justement classifier tout ça, on va l'analyser un petit peu plus en détail, là

### 03:47 - 03:53
le premier objectif c'est d'ouvrir le logiciel que vous souhaitez donc soit

### 03:53 - 03:58
code code soit codex peu importe moi personnellement je vais ouvrir codex

### 03:58 - 04:02
je vous invite à faire de même ça peut être intéressant aussi d'utiliser

### 04:02 - 04:09
directement l'application desktop une occasion de l'utiliser il me semble

### 04:09 - 04:17
lors des précédentes séances je vais cliquer sur codex maintenant je

### 04:17 - 04:25
Je copie le prompt, je lance Codex et là je vais tout simplement sélectionner le bon dossier.

### 04:25 - 04:29
Donc le dossier où on a scrapé l'élite.

### 04:29 - 04:43
Donc je fais nouveau clavardage, je choisis le projet, ajouter un nouveau projet en bas,

### 04:43 - 04:54
Business, gratuit massif, j'ouvre et là ensuite je colle tout simplement le prompt.

### 04:54 - 04:58
On va l'analyser, il n'y a pas de problème pour qu'on comprenne bien justement la demande.

### 04:58 - 05:05
pourquoi il va agir ainsi. Donc là je le mets sur le modèle 5.5 en élevé, je le met en très

### 05:05 - 05:11
approfondi, je vais aller chercher de la vitesse, je vais mettre vite et je lui donne accès complet

### 05:11 - 05:18
dans le sens où il va pouvoir travailler sur tout le dossier au complet et il va tout simplement

### 05:18 - 05:26
pas me faire de demandes supplémentaires, je lui donne une mission et il termine une fois

### 05:26 - 05:32
qu'il me signale qu'il a terminé la mission une fois qu'il a tout fait.

### 05:32 - 05:59
Là je peux envoyer, il va réfléchir, travailler, il va trouver une solution, parce que ce n'est

### 05:59 - 06:07
pas le bon dossier encore une fois, donc là il a trouvé la source dans le décès travail

### 06:07 - 06:08
réel.

### 06:08 - 06:24
Après on ira, lors d'une prochaine séance, réorganiser du coup tous nos dossiers et

### 06:24 - 06:30
ensuite les connecter sur Cowork. C'est pour ça que là c'est un petit peu le

### 06:30 - 06:37
bazar, c'est pas grave. Pendant qu'ils travaillent nous, ce qu'on va faire c'est

### 06:37 - 06:40
qu'on va analyser un petit peu le prompt, on va essayer de le comprendre.

### 06:40 - 06:48
Encore une fois je vous conseille de prendre un abonnement à 100 euros sur

### 06:48 - 06:54
Cloud Code et un abonnement de 100 euros sur Codex. Le dernier modèle 5.5

### 06:54 - 06:59
de OpenAI est extrêmement puissant, vous pouvez vraiment tout faire, on se

### 06:59 - 07:03
rapproche vraiment de la super intelligence c'est assez bluffant je vous

### 07:03 - 07:07
invite à le tester je sais qu'on parle beaucoup de Claude Code parce que voilà

### 07:07 - 07:15
il sort beaucoup de nouveaux outils mais OpenEye s'est bien rattrapé et

### 07:15 - 07:19
honnêtement il n'y a pas un meilleur modèle actuellement sur le marché

### 07:19 - 07:23
vous pouvez tout faire donc là ce que je lui dis c'est que c'est un

### 07:23 - 07:31
REV OBS donc ceux qui ne savent pas professionnel dont la mission principale est

### 07:31 - 07:35
d'optimiser et d'animer les processus liés à la génération des revenus au

### 07:35 - 07:37
centre de l'entreprise donc c'est important à chaque fois de lui donner du

### 07:37 - 07:42
détail de lui dire ce qu'il est pourquoi parce que là il sait que derrière il

### 07:42 - 07:46
va devoir se mettre dans cette position il va devoir être un expert

### 07:46 - 07:55
revops data donc lui on lui donne la mission de nettoyer la base B2B de

### 07:55 - 07:59
faire un scoring commercial un CRM de conformité préparation de campagne de

### 07:59 - 08:02
prospections. Sa mission c'est de reprendre le fichier enrichi avec

### 08:02 - 08:09
Apify, celui qu'on lui a donné. Là il est en train de travailler, il est en train de

### 08:09 - 08:15
voir qu'il y a 11 839 lignes, donc il a bien le bon fichier, celui qu'on a

### 08:15 - 08:20
enrichi avec Apify. Donc le but c'est qu'il va créer une base CRM propre,

### 08:20 - 08:24
dédupliquer, scorer et prête pour la prospection. Le but n'est pas d'envoyer

### 08:24 - 08:27
des emails, le but est de préparer une base solide pour la séance

### 08:27 - 08:33
suivante donc les fichiers de sortie créés donc mon business 09 bbd

### 08:33 - 08:38
prospections donc ça c'est tout ce qu'il va faire il va créer aussi des

### 08:38 - 08:46
dupe map quality en csv et la partie md parce qu'on sait que les modèles llm

### 08:46 - 08:51
aiment bien justement ces formats là donc entre toutes les colonnes donc là

### 08:51 - 08:55
il va lire justement les 11000 colonnes qu'il a détecté juste ici

### 08:55 - 09:04
ça va lui prendre pas mal de temps et il va comprendre colonne Serper, colonne

### 09:04 - 09:10
DG, colonne API5, Priority Score, Priority Class, Personalized Angle, Outreach

### 09:10 - 09:14
Message. Donc la contrainte ne supprime aucune

### 09:14 - 09:18
donnée utile si tu fusionnes des lignes, conserve toutes les sources, ne

### 09:18 - 09:23
modifie pas les féchiers précédents et crée une nouvelle version propre

### 09:23 - 09:28
phase 2 phase 0 audit initial donc lui va analyser le nombre de leads donc là

### 09:28 - 09:39
il l'a déjà fait et là la phase 0 modèle 5 en 6 donc le total de lead ID

### 09:39 - 09:43
le total serial, les doublons probables, les emails présents, les

### 09:43 - 09:47
téléphones présents, on nous donne toutes les informations et il doit les

### 09:47 - 09:49
récupérer donc là il va en faire un diagnostic il va le mettre dans le

### 09:49 - 09:54
rapport md donc à chaque étape il va enrichir ce fichier là on lui

### 09:54 - 10:00
donne un parcours. Tu fais la phase 0, t'enrichis. Tu fais la phase 1, t'enrichis.

### 10:00 - 10:07
Comme ça, après on a un fichier qui est extrêmement détaillé avec toutes les

### 10:07 - 10:10
informations nécessaires pour la prochaine étape.

### 10:10 - 10:14
Donc l'étape 1, ça va être de normaliser company name, domain, website,

### 10:14 - 10:21
email, phone, city, postal code, dgcrn, dgcred, app findings, sociaux, email.

### 10:21 - 10:29
Donc là le but c'est qu'on ait un mail directement exploitable, pas avec un double par exemple

### 10:29 - 10:37
AROBASE, pareil pour le numéro de téléphone, pareil pour la partie site, et après une fois

### 10:37 - 10:41
qu'il a fait ça, on passe à la phase 2. Donc là on va créer de la déduplication,

### 10:41 - 10:45
on va le refaire encore une fois, le but c'est de faire le ménage, même si on lui a déjà

### 10:45 - 10:51
demandé deux fois, c'est pas un problème si on peut trouver 3 ou 4 doublons, c'est

### 10:51 - 10:55
c'est toujours au top derrière si on ne les a pas dans notre base.

### 10:55 - 11:01
Donc on lui dit qu'il regarde le sirene, le sirene plus domaine, domaine plus city,

### 11:01 - 11:04
donc là on lui fait vraiment une sorte de boucle,

### 11:04 - 11:10
donc si derrière il y a des ressemblances, si c'est identique, tu les sautes directement.

### 11:10 - 11:14
Donc quand il fusionne, il va garder les meilleurs priority scores.

### 11:14 - 11:26
Une donnée email, une donnée téléphone, source URL, source page, contact, les notes utiles

### 11:27 - 11:30
et après il va écrire directement dans le dedup map en CSV

### 11:30 - 11:41
et après il va merger du coup ceux où ils sont tout simplement similaires

### 11:41 - 11:50
Donc c'est pour ça qu'on va lui faire un merge reasons avec secret, domain, domain city, email phone, name city, adresse

### 11:50 - 11:53
Et après on passe à la phase 3, donc la phase qualité

### 11:53 - 11:59
Donc on va créer un système de flags avec la partie ci derrière

### 11:59 - 12:03
Il n'y a pas d'email, de phone, donc il n'y a pas de wik

### 12:03 - 12:07
Il n'y a pas de wik ici au niveau d'apify et de data goof

### 12:07 - 12:13
s'il n'y a pas de conflit au niveau de l'email, du phone, s'il n'y a pas de source aussi au niveau du contact

### 12:13 - 12:23
regarde, il est encore en train de travailler

### 12:23 - 12:27
s'il n'y a pas un bad fit, s'il y a une duplicate machine

### 12:27 - 12:30
et une manuelle review recueillie

### 12:30 - 12:38
donc après il va faire un call ID statue avec la partie clean ready

### 12:38 - 12:42
ready with swarming needs manual review

### 12:42 - 12:50
notre contact, donc la règle encore une fois, on lui donne des informations pour que derrière

### 12:50 - 12:56
quand il travaille sur ce fichier là qu'on souhaite ensuite pour la prospection, il soit

### 12:56 - 13:04
parfait et soit vraiment utile pour de la prospection, ne pas envoyer de mail à des

### 13:04 - 13:10
personnes qui ne vont pas l'ouvrir, ou tout simplement une adresse email qui bug, c'est

### 13:10 - 13:15
pas utile, c'est d'avoir la full qualité pour que d'autres messages passent le mieux

### 13:15 - 13:16
possible.

### 13:16 - 13:23
Après on passe à la phase 4, c'est le score final, on va lui dire de calculer sur 100

### 13:23 - 13:24
le lead.

### 13:24 - 13:30
On avait déjà fait le legal confidence score avec une note sur 20, c'est confirmé,

### 13:30 - 13:32
entreprise active, code APE cohérent.

### 13:32 - 13:38
Après on lui avait fait contactability score, feed score final on l'avait fait

### 13:38 - 13:44
aussi PEN score final et TEN score final et ensuite une fois qu'il a fait ce

### 13:44 - 13:51
calcul là, on passe à la phase 5 donc la segmentation Outreach donc

### 13:51 - 13:56
créer Outreach segment, privates station group, agents vocales appel, avis

### 13:56 - 14:01
réputation, réservation de show, récupération staffing, menu contenu, CRM

### 14:01 - 14:06
fidélisation générale à IOPS donc là encore une fois c'est mes services à

### 14:06 - 14:09
moi donc après vous allez changer vos services

### 14:09 - 14:16
ça c'est des variables, on est même que moi parce que sinon vous allez proposer des services

### 14:16 - 14:23
qui n'ont rien à voir avec vos leads probablement. Ensuite, une fois que c'est fait, on va créer

### 14:23 - 14:32
un angle final donc assistant email privatisation groupe, audit appel raté plus agent vocal IA,

### 14:32 - 14:37
automatisation responsable Google, relance clients et nos shows, assistant recrutement

### 14:37 - 14:43
en candidature automatisation et du jour et réseau mini CRM fidélisation donc

### 14:43 - 14:48
après on lui demande de créer justement un message personnalisé avec avec google

### 14:48 - 14:52
site web page contact page privatisation numéro de téléphone outils de

### 14:52 - 14:59
réservation d'attaque ou autre donc phase 6 action recommandé créer final

### 14:59 - 15:04
next action avec la partie email personnalisé appel

### 15:04 - 15:09
email puis email, email puis appel, LinkedIn, Instagram, formulaire contact, vérification, etc.

### 15:09 - 15:15
Encore une fois, l'objectif principal c'est d'avoir un fichier exploitable,

### 15:15 - 15:22
ensuite on va l'utiliser pour de la prospection, mais la prospection qu'on va tout simplement faire,

### 15:22 - 15:29
ça va pas être les mêmes messages qu'on écrit là. L'objectif c'est d'avoir un brouillon et

### 15:29 - 15:31
et ensuite de l'améliorer.

### 15:31 - 15:34
On sait ce qui marche et on sait ce qui ne marche pas comme message.

### 15:34 - 15:36
On ne veut pas quelque chose de...

### 15:36 - 15:39
C'est ici, je vais voir juste où il en est.

### 15:39 - 15:48
On va y aller, c'est top, je vais voir un peu.

### 15:48 - 15:49
On ne veut pas...

### 15:49 - 16:21
Bonjour, je suis Baptiste.

### 16:21 - 16:22
C'est de la merde ça.

### 16:22 - 16:23
Ce n'est pas utile.

### 16:23 - 16:27
L'objectif c'est vraiment d'avoir quelque chose d'extrêmement personnalisé qui tape.

### 16:27 - 16:29
Donc là je ne pourrais pas vous faire.

### 16:29 - 16:32
Je vais essayer d'en faire un qui je sais qui fonctionne.

### 16:32 - 16:50
Moi j'aime bien être extrêmement amical.

### 16:50 - 17:18
J'aimerais te proposer un agent IA, c'est vraiment d'être différent, on reçoit énormément

### 17:18 - 17:22
de mails de prospection, si derrière on ne personnalise pas un maximum, là déjà

### 17:22 - 17:29
on a le nom, on lui dit le resto tourne bien en ce moment, on pourrait rajouter encore

### 17:29 - 18:07
une fois une variable, filet de leads, on lui rajoute, comme ça il sait que derrière

### 18:07 - 18:08
on parle à lui.

### 18:08 - 18:17
Allo Jean-Christophe, la farm, brasserie du port tourne bien en ce moment, j'aimerais

### 18:17 - 18:30
te proposer. Personne ne lui écrit des messages comme ça. Peut-être ça va pas passer parce que

### 18:30 - 18:36
derrière, il va voir que c'est trop cash, ça lui fait pas, mais ça fonctionne. C'est plus

### 18:36 - 18:40
comme ça que je prospecte. Pourquoi ? Parce que c'est différent. Chaque fois je reçois des

### 18:40 - 18:45
messages LinkedIn, c'est tous les mêmes, même par mail. Bonjour, j'espère que vous allez bien

### 18:45 - 18:50
Baptiste. On peut se retrouver, on peut se faire un call, j'aimerais vous proposer mes

### 18:50 - 18:56
services. Ça y est, tu vois ça tous les jours, tu zappes. Si tu rentres dans l'art, tu comprends

### 18:56 - 19:04
exactement son business, tu vas lui proposer une solution cohérente, directe, qui le touche, qui

### 19:04 - 19:12
lui permet d'avoir un vrai avis sur ce que tu peux lui apporter. Ah ouais, ça parle beaucoup

### 19:12 - 19:15
d'Ian en ce moment, ça peut être pas mal. Je vais peut-être le prendre en call, il peut

### 19:15 - 19:18
me ramener de l'argent, il peut me ramener du business, il peut me faire gagner du temps,

### 19:18 - 19:26
ça peut être top, je suis sous l'eau en ce moment. On pourrait rajouter aussi, j'espère que t'es pas

### 19:26 - 19:31
sous l'eau, il ne va pas être facile de gérer un resto. Je voulais voir si on pouvait discuter

### 19:31 - 19:36
il y a un moment, parce que je propose des services justement pour les restaurateurs, j'ai

### 19:36 - 19:47
accompagné trois restos dans la région, ça peut t'intéresser, je pense. Je passe aux

### 19:47 - 19:52
transformations, lecture de toutes les données, normalisation, e-mail, téléphone, union des

### 19:52 - 19:59
Donc là il est en train de travailler sur la partie des duplications, on va le laisser faire

### 19:59 - 20:04
Encore une fois ça prend du temps, c'est pour ça que c'est une étape très importante de structurer vos données

### 20:04 - 20:24
La phase 7, on va lui dire les résultats qu'on souhaite

### 20:24 - 20:28
Donc on veut un CRM dashboard KPI avec une source

### 20:28 - 20:30
On veut aussi un graphique, on veut un master CRM

### 20:30 - 20:34
Donc les lignes finales sont dédupliquées, colonnes minimum

### 20:34 - 20:38
Ready for email, seulement les lignes avec primaries emails

### 20:38 - 20:43
Donc ça, c'est ça qu'on va utiliser au IG4Call si vous souhaitez faire du callcalling,

### 20:43 - 20:48
au IG4Social, ManuelReview, NoteContact.

### 20:48 - 21:00
C'est possible qu'on ait sur 11 000 lignes, beaucoup moins de peut-être 3 ou 4 000 maximum

### 21:00 - 21:04
de listes contactables, mais c'est déjà intéressant sur 4 000 leads.

### 21:04 - 21:10
Si vous êtes bon, avec un bon message, vous pouvez en bouclier facile,

### 21:10 - 21:22
4-5, plus peut-être, peut-être 7-8, ça dépend après ce que vous proposez comme service.

### 21:22 - 21:26
C'est pour ça qu'il faut être vraiment pas général.

### 21:26 - 21:34
Il faut aller taper directement sur ce que veut le prospect, très important.

### 21:34 - 21:40
Après, juste pour vous faire un petit récap' rapide de tout ce qu'on a vu,

### 21:40 - 21:45
bien maintenant je pense qu'on a fait 19 séances, à peu près 18 je crois.

### 21:45 - 21:54
En fait, il faut se mettre en tête que les modèles comme Codex, Cloud Code peuvent tout faire.

### 21:54 - 22:00
Je sais que je l'ai déjà dit, mais c'est à vous justement de travailler sur ces modèles-là.

### 22:00 - 22:05
Dans le sens où je vous montre une stratégie, vous allez la reproduire à l'identique avec un prompt.

### 22:05 - 22:08
C'est top parce que vous allez savoir le faire.

### 22:08 - 22:18
Mais il va falloir faire aussi une preuve de réflexion dans le sens où il va falloir rentrer un petit peu plus dans le détail.

### 22:18 - 22:21
Donc faire des exos personnels.

### 22:21 - 22:29
Je ne sais pas, par exemple, vous aimez la création d'assets 3D sur Blender.

### 22:29 - 22:34
Vous pouvez connecter le modèle Codex en MCP à Blender.

### 22:34 - 22:39
Donc là ça va vous permettre d'élargir vos compétences, de comprendre encore plus les modèles d'IA

### 22:40 - 22:42
et ensuite d'être un petit peu plus

### 22:43 - 22:45
expert justement sur

### 22:45 - 22:52
le but c'est de tout maîtriser

### 22:52 - 22:55
encore une fois il n'y a rien de bien complexe ça vraiment je vous le dis

### 22:56 - 23:03
je sais que ça peut paraître compliqué parfois les termes etc mais pour vous dire avant je connais encore un petit peu

### 23:04 - 23:06
maintenant je le fais plus du tout

### 23:06 - 23:11
les modèles d'IA sont dans la capacité de tout faire donc si vous avez une

### 23:11 - 23:15
problématique vous demandez à l'intelligence artificielle et il va la

### 23:15 - 23:18
résoudre. La structure pour un client n'est pas

### 23:18 - 23:26
compliquée. Le client souhaite une automatisation de son CRM connecté à

### 23:26 - 23:31
de l'IA. Ok, top. Est-ce qu'il veut de la sécurité ? Il veut de la

### 23:31 - 23:35
sécurité ? Bon bah parfait on va acheter un VPS sur Hostinger. Comme ça il

### 23:35 - 23:38
il aura tout en local, il n'y aura pas de problématique.

### 23:38 - 23:39
Donc il souhaite faire quoi ?

### 23:39 - 23:41
Il souhaite classifier ses leads.

### 23:41 - 23:44
Ok, donc on récupère l'API de son CRM

### 23:44 - 23:48
et on demande à Codex qu'il nous fasse justement ce qu'il nous a demandé.

### 23:48 - 23:52
Il va le faire automatiquement, il n'y a pas de problème et de manière sécurisée.

### 23:52 - 23:55
Voilà, par exemple, il y a ça.

### 23:55 - 23:58
Le client souhaite un chatbot hier.

### 23:58 - 24:00
Il veut un chatbot pour son site internet.

### 24:00 - 24:02
Et bien, ce qu'on va faire, c'est simple.

### 24:02 - 24:08
on va encore une fois lui demander s'il a besoin de sécurité

### 24:08 - 24:12
normalement c'est oui, ok on passe sur Hostinger, on achète un VPS propre au client

### 24:12 - 24:15
donc une fois qu'on a le VPS, qu'est-ce qu'il faut faire ?

### 24:15 - 24:17
il faut créer une base de données

### 24:17 - 24:20
donc la base de données, on va utiliser SuperBase

### 24:20 - 24:22
parce que c'est le plus simple à utiliser

### 24:22 - 24:25
est-ce que c'est nous qui allons créer nous-même les colonnes

### 24:25 - 24:28
allons créer justement la base ? Non, on va demander à Codex

### 24:28 - 24:31
parce qu'il va faire du piton, il va pouvoir se connecter en API

### 24:31 - 24:34
Donc on lui donne les accès API en ENV pour la sécurité.

### 24:34 - 24:36
Donc une fois qu'il a fait la base de données,

### 24:36 - 24:38
on va lui demander de nous créer le HTML.

### 24:38 - 24:43
Le HTML va nous permettre de connecter le Chatbot

### 24:43 - 24:48
avec une API directement de Cloud ou de ChatGPT.

### 24:48 - 24:51
Ensuite vous avez votre Chatbot, en 2 heures c'est fini.

### 24:51 - 24:54
En fait c'est vraiment ça qu'il faut se mettre en tête,

### 24:54 - 24:56
c'est que vous avez une problématique,

### 24:56 - 24:58
l'IA va être dans la capacité de le faire.

### 24:58 - 25:02
Pourquoi ? Parce que, tout simplement, elle a tellement de connaissances

### 25:02 - 25:06
qu'en aucun cas, elle ne peut pas résoudre quelque chose de simple

### 25:06 - 25:13
comme la création d'un agent IA, la création d'un chatbot,

### 25:13 - 25:20
la création d'une connexion entre outils, enfin bref, tout.

### 25:20 - 25:25
Donc c'est ça qu'il faut vraiment comprendre et se mettre en tête.

### 25:25 - 25:29
Si quelqu'un vous demande de faire quelque chose, vous allez pouvoir le faire.

### 25:29 - 25:32
Pourquoi ? Parce que il n'y a rien de bien compliqué.

### 25:32 - 25:35
Je sais que c'est facile à dire, je sais.

### 25:35 - 25:43
Mais dites-vous que je suis sur le marché il y a depuis maintenant un an et demi.

### 25:43 - 25:45
Et les modèles avant n'étaient pas aussi puissants.

### 25:45 - 25:50
C'est pour ça que j'ai pu avoir une expérience un peu plus développée.

### 25:50 - 25:52
Mais vous allez pouvoir avoir la même.

### 25:52 - 25:54
Ce n'est pas un souci.

### 25:54 - 25:57
La stratégie est la même pour tout le monde.

### 25:57 - 26:04
une problématique, on utilise un modèle IA, on lui demande comment builder ça, ok il a compris

### 26:04 - 26:12
donc maintenant on lui donne un prompt, le prompt permet de donner une mission et la mission elle

### 26:12 - 26:19
est finie, on regarde ce qui peut être amélioré. C'est que ça, après ça peut prendre plus de

### 26:19 - 26:26
temps sur certains projets, mais généralement, à part si vous faites un SAS de la HAZ,

### 26:26 - 26:31
d'une infrastructure IA avec application personnelle, donc un nouveau CRM, vous allez

### 26:31 - 26:35
prendre peut-être une semaine mais derrière les factures ça va être à hauteur de 40-50k

### 26:35 - 26:41
mais si derrière vous faites un petit chatbot à 4-5 mille euros ça vous prendra pas plus de

### 26:41 - 26:49
trois jours. Allez peut-être peut-être quatre jours si vous demandez un 8N parce que après

### 26:49 - 26:56
voilà vous pouvez aussi très bien connecter un 8N comme on l'a vu à GPT ou Cloud Code

### 26:56 - 27:06
vous gagnez énormément de temps. Donc c'est ça aussi qu'il faut qu'on comprenne. Vous avez la

### 27:06 - 27:10
possibilité de tout faire. Vous pouvez être un expert de Blender, vous pouvez être un expert

### 27:10 - 27:18
de génération de leads automatiques, vous pouvez être un expert des chatbots, vous pouvez être

### 27:18 - 27:21
un expert des créations de bases de données, vous pouvez être un expert de création de SaaS

### 27:21 - 27:32
vous avez la possibilité de tout faire et surtout c'est une nouvelle niche, un nouveau métier,

### 27:32 - 27:45
un nouveau domaine donc il y a tellement d'opportunités qui sont incalculables que

### 27:45 - 27:49
vous allez pouvoir en profiter et ça se trouve vous allez avoir une idée parce que vous savez

### 27:49 - 27:56
maintenant gérer des modèles qui va vous permettre de créer un bon business quoi.

### 27:56 - 28:04
Donc allez-y foncez, n'ayez pas peur, vous avez l'expertise adéquate, il ne faut

### 28:04 - 28:09
juste pas se poser trop de questions, avoir ce syndrome de l'imposteur en disant

### 28:09 - 28:14
ah ouais mais avant je faisais ci, avant je faisais ça, je suis pas légitime de

### 28:14 - 28:15
me lancer dedans, de me faire passer par l'expert.

### 28:15 - 28:20
encore une fois c'est un nouveau milieu, personne n'est expert mis à part ceux qui ont créé les

### 28:20 - 28:28
modèles qui sont bons dans le coding, franchement la plupart des gens qui

### 28:28 - 28:33
bossent à l'heure actuelle dedans c'est des mecs comme vous et moi qui

### 28:33 - 28:38
essayent de comprendre constamment, de s'améliorer sur ces modèles là,

### 28:38 - 28:41
comprendre comment on peut les améliorer, comprendre comment on peut

### 28:41 - 28:51
gagner du temps et puis avance comme ça donc allez-y foncez et puis testez des

### 28:51 - 28:54
trucs faites vous plaisir de toute manière la séance 24 ça va être assez

### 28:54 - 28:59
arde l'objectif c'est que vous allez regrouper toutes les informations qu'on

### 28:59 - 29:06
a accumulé lors de toutes les séances et créer un énorme projet pas mal du tout ça

### 29:06 - 29:14
et je l'analyserai justement pour un petit peu vous en aide si vous avez

### 29:14 - 29:21
bien compris toutes les séances etc là je pense qu'il va bientôt

### 29:21 - 30:18
terminer juste la génération, donc il a bien structuré nos leads. Je sais que ça

### 30:18 - 30:23
peut paraître cher, après un abonnement j'ai pété, mais il suffit d'un client et ça part tout

### 30:23 - 30:28
seul. Dites-vous que vous pouvez aussi travailler sur 7 clients en même temps, donc ça accumule

### 30:28 - 30:34
vos joueurs de TGM, c'est vraiment une folie, c'est une folie. Allez-y foncez, vraiment,

### 30:34 - 30:37
c'est un conseil que je vous donne, parce qu'après le marché il peut changer d'ici 2 ans,

### 30:37 - 30:45
en trois ans. Donc allez-y, foncez. Honnêtement, il y a de quoi faire. De plus en plus d'entreprises

### 30:45 - 30:51
souhaitent justement des automatisations. Enfin, ils souhaitent gagner du temps tout

### 30:51 - 30:56
simplement. Ils souhaitent entrer dans le train de l'IA et de toute manière, ils

### 30:56 - 31:00
vont s'en rendre compte très vite une fois que vous avez en place la première automatisation

### 31:00 - 31:04
ou de l'intelligence artificielle qui gagne du temps, qui vont vous recontacter

### 31:04 - 31:47
ensuite vous pourrez pratiquer plus haut au fur et à mesure. Avoir les logs, c'est vraiment pas mal cette petite application codex

### 31:48 - 31:50
parce que vous pouvez créer des automatisations

### 31:51 - 31:53
directement dessus. Après c'est pas mieux qu'un 8n

### 31:54 - 31:55
si votre

### 31:55 - 31:57
client souhaite avoir un visuel

### 31:58 - 32:03
et vous pouvez aussi avoir les extensions ici qui sont similaires à celles de

### 32:03 - 32:14
cloud desktop. Vous en avez énormément, vous pouvez tout faire. C'est juste qu'ils communiquent mal en fait

### 32:14 - 32:21
du coup on a l'impression que Cloud Code est un meilleur modèle alors que franchement je

### 32:21 - 32:26
pense qu'ils sont en dessus à l'heure actuelle. Vous avez Gmail, Drive, SharePoint, Teams, Outlook,

### 32:26 - 32:35
Versel, NetiFly, Expo, non franchement vous avez de quoi faire. Je suis pas base aussi du coup

### 32:35 - 32:39
pour la base de données ça je sais qu'on n'en a pas parlé pour le moment on va le voir

### 32:39 - 34:55
justement sur un projet client réel. Il a terminé, il l'a mis. Si je vais en XLSX

### 34:55 - 35:33
Je vais ouvrir le CRM.CSV, le Clean en XLSX, l'Outreach MD, le Quality issue, je vais

### 35:33 - 35:34
peut-être le renoncer.

### 35:34 - 37:33
La valeur, le classement avec avis, vérifications, etc.

### 37:33 - 37:37
On a le Master CRM avec toutes les infos juste ici.

### 37:37 - 37:44
Donc là on a quand même énormément bien énormément de colonnes.

### 37:44 - 37:48
Après ce qui peut être intéressant c'est justement d'aller challenger Codex pour

### 37:48 - 37:50
recevoir des informations supplémentaires.

### 37:50 - 47:37
Le READY FOR EMAIL c'est ça qui va nous intéresser, on va demander lui s'il sait faire du code, s'il sait même très très bien faire du code très rapidement

### 47:37 - 47:45
La séance 24 qu'on va faire où vous allez avoir un exercice, et bien derrière ça va vous créer ce petit déblocage, c'est pour ça qu'il va falloir bien le réaliser

### 47:45 - 47:52
à la place de suivre une formation ou derrière, vous montrer, prendre vraiment un cas concret

### 47:52 - 47:58
donc là moi c'est Restia, agence, restauration, et ensuite d'arriver jusqu'à l'objectif

### 47:58 - 48:02
donc avoir une vraie agence. Donc là ça vous met déjà un petit peu dans le concret

### 48:02 - 48:07
c'est pas de la théorie, ça vaut vraiment de la pratique, mais la séance 24 va vous permettre

### 48:07 - 48:34
de créer un projet et compétences que vous avez, j'ai d'avoir 10 salariés pour faire tourner une agence

### 48:34 - 48:44
c'est prendre mes 100k sur une année, je fous l'automatique, je peux organiser toute

### 48:44 - 48:51
ma structure, fin de personne, juste un modèle il y a qui tourne et qui réfléchit, en plus

### 48:51 - 49:12
de mon cerveau et c'est parti, en avance ça ne faut jamais l'oublier, ça s'y met

### 49:12 - 53:09
à l'intérieur des fichiers, maintenant ce qu'il va falloir faire, tout simplement

### 53:09 - 53:26
récupérer la prospection BDD et lui demander d'organiser tout le projet à l'intérieur

### 53:26 - 53:30
cette fois-ci on a fait l'intérieur des fichiers là on va organiser l'intérieur

### 53:30 - 53:33
du dossier pour ça on peut faire très simple

### 53:33 - 53:37
je vais le faire en one shot encore une fois c'est votre imagination de comment vous voulez

### 53:37 - 53:41
voir la chose et comment vous allez résoudre enfin comment le LLM ou

### 53:41 - 53:45
Codex va résoudre la chose donc pour ça ça va pas être compliqué moi je vais faire très

### 53:45 - 01:01:29
simple les dossiers et l'organisation me va donc on va passer du coup à la

### 01:01:29 - 01:01:38
Science 19, on va aller faire de la prospection automatisée, donc grâce je vais juste supprimer

### 01:01:38 - 01:01:43
ce petit dossier là, je sais pas ce qu'il faut. A tout de suite !
