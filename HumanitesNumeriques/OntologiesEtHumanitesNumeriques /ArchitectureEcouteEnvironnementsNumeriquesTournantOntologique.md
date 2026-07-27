### L'Architecture de l'Écoute : Environnements Numériques et Tournant Ontologique dans les Humanités Numériques

#### 1. Introduction : La matérialité numérique comme nouveau régime d'existence du savoir

Le passage de l’archive sonore traditionnelle — en l'occurrence, les enregistrements des séminaires de Gilles Deleuze à l’Université Paris 8 — vers un écosystème applicatif intégré, composé du module ChaoticumSeminario et de la Progressive Web App (PWA) Flux Conceptuel, ne constitue pas une simple translation de support. Il s'agit d'une mutation profonde du régime d'existence du savoir au sein des Humanités Numériques. Comme le souligne Milad Doueihi (2011), l'humanisme numérique ne réside pas dans la technologie elle-même, mais dans la manière dont elle reconfigure nos catégories de pensée. Ici, l'archive n'est plus un dépôt statique de fichiers audio ; elle devient une « donnée vivante », un objet malléable dont l'ontologie est redéfinie par sa structure logicielle.Jeffrey Schnapp (2014) avance que les Humanités Numériques transforment la nature même du travail savant en déplaçant l'attention de l'objet vers le processus. Dans cet écosystème, le cours de Deleuze cesse d'être une unité monolithique pour devenir un agrégat de fragments, de tokens indexés et de flux sémantiques. La problématique centrale de cette évolution réside dans la dualité structurelle entre le serveur (la gestion relationnelle des données) et le client (l'expérience phénoménologique de l'utilisateur). Cette architecture participe au « tournant ontologique » en ce qu'elle ne se contente pas de représenter l'œuvre, mais lui confère une nouvelle matérialité dynamique. Ce chapitre explore comment l'interopérabilité entre les tables SQL de ChaoticumSeminario et l'interface mobile de Flux Conceptuel redéfinit l'acte d'écoute et de recherche, transformant la parole philosophique en un territoire de curation continue.

#### 2. Le Serveur comme Ontologie Structurante : Au-delà du Modèle RDF Standard

Dans la conception d'un système d'information patrimonial, l'infrastructure serveur n'est jamais un conduit neutre ; elle agit comme une ontologie structurante qui prédétermine les entités de recherche et leurs relations possibles. Lev Manovich (2013) rappelle que le logiciel « prend le commandement » des objets culturels en les soumettant à ses propres logiques de données. Pour le projet ChaoticumSeminario, le choix technique s'est porté sur une architecture hybride au sein d'Omeka-S, dépassant délibérément les limites du modèle RDF (Resource Description Framework).Si le modèle RDF, pivot du Web Sémantique prôné par Berners-Lee et al. (2001), est idéal pour établir des relations globales entre des ressources, il s'avère souvent trop rigide pour capturer la granularité et la fluidité « rhizomatique » d'un séminaire oral. L'utilisation de tables SQL dédiées pour les transcriptions et les concepts, en marge du cœur d'Omeka-S, marque une volonté de modéliser le « chaos » inhérent à la pensée deleuzienne. Johanna Drucker (2012) souligne que les interfaces de données doivent refléter l'ambiguïté des objets humanistes. Ici, la pièce maîtresse technique est la requête pivot timelineConceptAnnexe().Cette fonction ne se limite pas à une simple extraction ; elle opère une jointure complexe entre cinq tables SQL (Conférences, Enregistrements, Fragments, Transcriptions et Concepts). Elle « reconstitue » l'objet numérique à partir de fragments atomisés. Techniquement, elle transforme le texte brut en un flux de tokens ASR (Automatic Speech Recognition) horodatés. Chaque mot devient ainsi une entité adressable, possédant sa propre existence temporelle au sein du fragment d'environ 50 secondes. Cette approche transforme la base de données en une véritable « machine à lire » (Ramsay, 2011), où le texte n'est plus une suite de caractères, mais un réseau de métadonnées temporelles.Cette structure repose sur trois piliers fondamentaux :

-   **L'indexation granulaire :** Le découpage systématique de la parole en segments temporels précis, permettant une manipulation chirurgicale de la pensée.\
-   **La curation collaborative :** Un modèle où la donnée n'est jamais figée, mais exposée à des ajustements constants via des contrôleurs dédiés comme le CorrectionController.\
-   **L'intégration de services tiers :** L'ouverture du système à des modèles d'IA (Whisper, Google STT) via des tâches de fond (jobs), assurant une versionnalité de la transcription.Cette organisation logicielle crée une base de connaissances prête à être consommée. Cependant, cette structure serveur reste une potentialité abstraite tant qu'elle n'est pas réactualisée par une interface client capable de lui redonner son rythme et sa présence.

#### 3. Le Client Mobile "Flux Conceptuel" : L'Ontologie de la Présence et du Rythme

Si le serveur structure la donnée, l'interface client, représentée par la PWA Flux Conceptuel, réactualise la parole philosophique dans l'espace-temps du chercheur. David M. Berry (2012) argumente que le médium numérique n'est pas seulement un vecteur, mais un cadre de compréhension qui modifie notre rapport au temps. En se connectant au point d'entrée OMK_BASE du serveur, l'application mobile transforme le chercheur en un acteur immergé.Un aspect crucial de cette architecture est la contrainte de déploiement : le client doit résider sur le même domaine que le serveur Omeka-S car l'API ne transmet pas d'en-têtes CORS. Cette « liaison ontologique » technique entre le serveur et le client garantit l'intégrité de l'écosystème. L'expérience de l'écoute est alors médiée par la fonction alignConceptsWithText située dans js/player.js. Cette logique est fondamentale : elle réconcilie deux régimes d'existence. D'un côté, les « tokens » bruts (la vision de la machine, une liste de mots isolés et horodatés) ; de l'autre, le « texte » (la vision humaine, ponctuée et syntaxique). En alignant ces deux flux, l'application crée un « lecteur-écouteur » : le texte s'illumine au rythme de la voix, fusionnant le document sonore et sa représentation textuelle en un objet unique.Cette présence est renforcée par l'usage du Service Worker (sw.js). En préchargeant l'« App Shell » et en gérant un cache persistant, le système assure une autonomie technique. L'objet de recherche n'est plus confiné au laboratoire ; il est « territorialisé » dans le quotidien du chercheur. Le tableau suivant analyse comment ces modes d'accès redéfinissent l'interaction avec l'œuvre :\| Mode d'accès \| Mécanisme technique \| Agence de l'utilisateur \| Dépendance technique \| Impact ontologique \|\| ------ \| ------ \| ------ \| ------ \| ------ \|\| **Recherche Plein Texte** \| cherche?trouve= (SQL MATCH) \| Explorateur sémantique : l'usager déconstruit l'œuvre par concepts. \| Dépendance forte à l'indexation SQL et à l'API. \| L'œuvre devient une base de données conceptuelle. \|\| **Lecture fragmentée** \| transcriptions?idConf= \| Auditeur phénoménologue : l'usager suit le flux temporel. \| Dépendance au player.js et à la synchronisation ASR. \| L'œuvre retrouve son rythme originel de séminaire. \|\| **Contribution active** \| signalerAction \| Éditeur collaboratif : l'usager corrige et enrichit l'archive. \| Dépendance au système d'authentification et aux ACL. \| L'archive devient un écosystème ouvert et évolutif. \|\
Cette interface n'est donc pas un simple masque posé sur les données, mais le lieu même où s'accomplit l'expérience de la pensée, comme le suggère Bruno Latour (2005) à propos de la médiation technique : l'outil ne se contente pas de transmettre, il transforme et compose l'objet qu'il donne à voir.

#### 4. La Curation Collaborative et l'IA : Vers une Ontologie Dynamique et Ouverte

L'archive numérique, dans ce paradigme, n'est jamais achevée. Elle est un processus en devenir, soutenu par une collaboration entre l'humain et la machine. Le flux de curation mis en place via le CorrectionController et l'intégration de WikidataReference illustre cette ouverture vers le monde.Lorsqu'un chercheur utilise l'application pour signaler une référence, il engage un processus qui dépasse le cadre du silo technique d'Omeka-S. Le lien avec Wikidata, via l'identifiant QID, permet d'inscrire l'archive de Deleuze dans le graphe universel des connaissances. Comme le prédisait Tim Berners-Lee (2001), le Web Sémantique prend vie lorsque les données locales se connectent à des référentiels globaux. L'entité « Deleuze » cesse d'être une simple chaîne de caractères pour devenir un nœud au sein d'un réseau de relations biographiques et bibliographiques infinies.La « relance de transcription » (relancerAction) introduit une dimension supplémentaire : l'ontologie de la « versionnalité ». L'archive n'est plus un texte fixé une fois pour toutes, mais une série de couches successives. L'usage de modèles d'IA comme Whisper ou Google STT signifie que la « vérité » du texte est une asymptote vers laquelle on tend. Stephen Ramsay (2011) parle d'une critique algorithmique où la machine aide à révéler des structures ; ici, la machine aide à révéler la parole, mais sous la surveillance constante de l'humain. Le TranscriptionCorrection agit comme un filtre éthique, validant les suggestions de l'IA et garantissant que l'expertise humaine reste souveraine.Cette collaboration soulève trois enjeux majeurs :

1.  **La souveraineté de l'expertise humaine :** Bien que l'IA génère les tokens, c'est l'éditeur qui valide les corrections, transformant le processus de publication en une forme de « peer review » continue et collaborative (Fitzpatrick, 2011).\
2.  **La traçabilité et l'éthique des sources :** Chaque modification est tracée via le standard oa:motivatedBy, assurant que l'histoire de l'archive et ses altérations restent transparentes pour les futurs chercheurs.\
3.  **L'infinitude du réseau face à la finitude de l'outil :** L'architecture permet de substituer les modèles d'IA sans compromettre la structure globale, reconnaissant que les outils de traitement sont transitoires tandis que le réseau de connaissances est permanent.

#### 5. Conclusion : La convergence applicative, nouveau paradigme des Humanités Numériques

Le tournant ontologique analysé à travers ChaoticumSeminario et Flux Conceptuel réside dans le passage de l'archive-objet (la cassette, le fichier audio) à l'archive-écosystème. La convergence entre le serveur et le client démontre que l'environnement numérique ne se contente pas de « contenir » la connaissance, mais qu'il la produit activement par ses interactions techniques et ses choix d'architecture.Comme l'analyse N. Katherine Hayles (2012) dans son concept de « technogénèse », notre pensée évolue en symbiose avec les outils que nous créons. L'intégration future d'assistants IA locaux comme AnythingLLM, mentionné dans les sources du projet, laisse entrevoir un nouveau mode de dialogue avec l'archive : celui où le chercheur ne se contente plus de chercher des mots-clés, mais interroge directement la pensée modélisée. La matérialité numérique, loin de dématérialiser le savoir, lui offre une nouvelle profondeur, à la fois technique, éthique et philosophique. L'archive deleuzienne devient ainsi un laboratoire vivant, une architecture de l'écoute où la voix du philosophe continue de résonner, augmentée par les flux du réseau.

#### 6. Bibliographie (Format BibTeX)

@book{doueihi2011,\
author = {Milad Doueihi},\
title = {Pour un humanisme numérique},\
publisher = {Seuil},\
year = {2011},\
address = {Paris}\
}

@book{manovich2013,\
author = {Lev Manovich},\
title = {Software Takes Command},\
publisher = {Bloomsbury Academic},\
year = {2013},\
address = {New York}\
}

@book{latour2005,\
author = {Bruno Latour},\
title = {Reassembling the Social: An Introduction to Actor-Network-Theory},\
publisher = {Oxford University Press},\
year = {2005},\
address = {Oxford}\
}

@article{bernerslee2001,\
author = {Tim Berners-Lee and James Hendler and Ora Lassila},\
title = {The Semantic Web},\
journal = {Scientific American},\
year = {2001},\
volume = {284},\
number = {5},\
pages = {34--43}\
}

@book{drucker2012,\
author = {Johanna Drucker},\
title = {SpecLab: Digital Aesthetics and Projects in Speculative Computing},\
publisher = {University of Chicago Press},\
year = {2012},\
address = {Chicago}\
}

@book{berry2012,\
author = {David M. Berry},\
title = {Understanding Digital Humanities},\
publisher = {Palgrave Macmillan},\
year = {2012},\
address = {London}\
}

@book{schnapp2014,\
author = {Jeffrey Schnapp},\
title = {Digital Humanities},\
publisher = {MIT Press},\
year = {2014},\
address = {Cambridge}\
}

@article{ramsay2011,\
author = {Stephen Ramsay},\
title = {Reading Machines: Toward an Algorithmic Criticism},\
journal = {University of Illinois Press},\
year = {2011}\
}

@book{fitzpatrick2011,\
author = {Kathleen Fitzpatrick},\
title = {Planned Obsolescence: Publishing, Technology, and the Future of the Academy},\
publisher = {NYU Press},\
year = {2011},\
address = {New York}\
}

@book{hayles2012,\
author = {N. Katherine Hayles},\
title = {How We Think: Digital Media and Contemporary Technogenesis},\
publisher = {University of Chicago Press},\
year = {2012},\
address = {Chicago}\
}